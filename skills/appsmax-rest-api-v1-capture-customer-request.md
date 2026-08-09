---
name: Capture a customer request into AppsMax
description: >-
  Push a lead captured outside AppsMax (a website form, a CRM, an inbound call) into the
  AppsMax REST API as a customer request (заявка), tag it, and read it back — without
  creating duplicates on retry.
api: openapi/appsmax-rest-api-v1-openapi-original.json
base_url: https://telegram.appsmax.ru/api/v1
operations:
  - getCurrentApiContext
  - listBots
  - createApplication
  - syncApplicationTags
  - getApplication
scopes:
  - applications:write
  - applications:read
  - bots:read
generated: '2026-08-09'
method: generated
source: openapi/appsmax-rest-api-v1-openapi-original.json + https://appsmax.ru/developers/
---

# Capture a customer request into AppsMax

## Before you start

- You need an AppsMax API token created by a human in the cabinet (**Данные → Интеграции → API**).
  There is no programmatic token issuance. REST access is gated to the paid **Профи** plan or an
  individual access right.
- Send it as `Authorization: Bearer $APPSMAX_API_TOKEN`. The `X-Api-Token` header is the fallback
  for clients that cannot send Bearer. **Never** put the token in a query string, browser code or a repo.
- Request and response bodies are `application/json`. All responses carry `X-Request-Id` and
  `X-Api-Version: v1`.

## Steps

1. **Confirm the token before doing anything** — call `getCurrentApiContext` (`GET /me`).
   The response tells you the organization, the token's granted `scopes`, its effective
   `rate_limit`, and `last_used_at`. If `applications:write` is not in `scopes`, stop: every
   write will return `403`. (`ping` / `GET /ping` is the lighter alternative but also requires
   a valid token — nothing on this API is anonymous.)

2. **Resolve the bot** — call `listBots` (`GET /bots`, optional `driver` and `status` filters)
   and pick the bot the request belongs to. `bot_id` is **required** on create and must belong
   to the token's organization; a foreign id comes back as `403` or `404`, never as someone
   else's data.

3. **Create the request** — call `createApplication` (`POST /applications`) with at least
   `bot_id`. Also send `source`, `title`, `channel`, `contact` and `payload` as the flow
   provides them.
   - **Always set an `Idempotency-Key` header.** 1–128 characters from `A-Za-z0-9._:-`. Derive
     it deterministically from the upstream record (for example the CRM lead id) so a retry
     reuses the same key.
   - A first success returns **201**. A retry with the same key and the *same* body returns
     **200** with `Idempotency-Replayed: true` and the original record — that is success, not
     a duplicate. The same key with a *different* body returns **409**; generate a new key.
   - Do **not** send a top-level `status` — it is not accepted on create. AppsMax assigns the
     initial status itself.

4. **Tag it** — call `syncApplicationTags` (`POST /applications/{application}/tags`) with
   `{"tags": [...]}`. This is a **sync**, not an append: the list you send becomes the list on
   the record. Maximum 20 non-empty tags. This operation does not accept an `Idempotency-Key`,
   but it is naturally safe to repeat because it is a full replace.

5. **Read it back** — call `getApplication` (`GET /applications/{id}`) to confirm the stored
   `number`, `status`, `status_label`, `contact`, `answers`, `form_meta` and `tags`.

## Rules an agent must follow

- **Rate limit**: 60 requests/minute per token by default; a token may carry a different limit,
  visible in `GET /me` and in `X-RateLimit-Limit` / `X-RateLimit-Remaining`. On `429`, honour
  `Retry-After` and back off exponentially. Never increase burst.
- **Errors**: branch on `error.code`, never on `error.message`. `422` puts per-field messages in
  `error.details.fields` — surface those, do not retry unchanged. Every error carries
  `error.meta.request_id`; quote it to support and never send the token or the payload.
- **Personal data**: send only the fields the flow needs. `contact` holds real personal data
  under Russian 152-FZ; the provider's guidance is to define controller/processor roles,
  retention and deletion before writing at volume.
- **Pagination** on `GET /applications`: follow the `links` next-page URL from the response
  envelope rather than incrementing `page`; `per_page` is clamped to 100.
