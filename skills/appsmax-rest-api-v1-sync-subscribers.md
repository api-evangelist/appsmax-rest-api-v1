---
name: Sync subscribers into AppsMax
description: >-
  Keep an external contact list (CRM, spreadsheet, loyalty database) in step with AppsMax
  subscribers — upsert on the natural key, update status and tags, and page through the
  existing audience safely.
api: openapi/appsmax-rest-api-v1-openapi-original.json
base_url: https://telegram.appsmax.ru/api/v1
operations:
  - getCurrentApiContext
  - listBots
  - listSubscribers
  - upsertSubscriber
  - getSubscriber
  - updateSubscriber
scopes:
  - subscribers:read
  - subscribers:write
  - bots:read
generated: '2026-08-09'
method: generated
source: openapi/appsmax-rest-api-v1-openapi-original.json + https://appsmax.ru/developers/
---

# Sync subscribers into AppsMax

## Before you start

- Token from the AppsMax cabinet, sent as `Authorization: Bearer $APPSMAX_API_TOKEN`.
- Confirm `subscribers:read` and `subscribers:write` with `getCurrentApiContext` (`GET /me`)
  before the first write.

## The natural key

A subscriber is identified by the pair **`bot_id` + `external_id`** — the channel-side id of
the person on that bot. This is why `upsertSubscriber` is safe to repeat: it creates on first
sight and updates thereafter. It returns **201** when it created and **200** when it updated.
There is no `Idempotency-Key` on this operation and none is needed.

## Steps

1. **Confirm scopes** — `getCurrentApiContext` (`GET /me`).

2. **Resolve the bot** — `listBots` (`GET /bots`). `bot_id` must belong to the token's
   organization.

3. **Read the current audience** — `listSubscribers` (`GET /subscribers`). Filters:
   `channel[]`, `status[]`, `bot_id`, `tag`, `group_id`, `q`, `created_from`, `created_to`,
   plus `sort=created_at` and `direction=asc|desc`. Page with `page` / `per_page` (clamped to
   100) and follow the `links` next-page URL from the envelope.

4. **Upsert each record** — `upsertSubscriber` (`POST /subscribers`) with `bot_id`,
   `external_id`, `channel`, and whatever of `status`, `name`, `username`, `phone`, `email`,
   `tags` you hold. Process in batches sized to stay under the rate limit.

5. **Targeted edits** — when you already know the AppsMax `id`, use
   `updateSubscriber` (`PATCH /subscribers/{id}`) to change channel, status, name, username or
   tags without resending the whole record, and `getSubscriber` (`GET /subscribers/{id}`) to
   read one back.

## Rules an agent must follow

- **Rate limit**: 60 requests/minute per token by default. A full-list sync is the operation
  most likely to trip it — pace the loop, read `X-RateLimit-Remaining`, and on `429` honour
  `Retry-After` with exponential backoff.
- **Tenancy**: a subscriber belonging to another organization is reported as `404`, not as a
  permission error. Do not treat `404` on a known-good id as a transient failure.
- **Errors**: `422` returns per-field messages in `error.details.fields`; fix the record rather
  than retrying it unchanged. Branch on `error.code`.
- **Personal data**: subscribers carry `phone`, `email`, `name` and `username`. Send only what
  is needed and agree retention and deletion with the operator before bulk-loading a list.
- Subscriber `groups` appear on the record but there is no groups collection endpoint in v1 —
  do not attempt to manage groups through this API.
