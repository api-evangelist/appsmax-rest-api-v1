---
name: Draft and launch an AppsMax campaign
description: >-
  Create a broadcast in AppsMax as a draft, verify its audience and content, and launch it as a
  separate, deliberate, human-approved action.
api: openapi/appsmax-rest-api-v1-openapi-original.json
base_url: https://telegram.appsmax.ru/api/v1
operations:
  - getCurrentApiContext
  - listBots
  - listSubscribers
  - createCampaign
  - getCampaign
  - runCampaign
  - listCampaigns
scopes:
  - campaigns:write
  - campaigns:read
  - subscribers:read
  - bots:read
consequence: high
human_in_the_loop: required
generated: '2026-08-09'
method: generated
source: openapi/appsmax-rest-api-v1-openapi-original.json + https://appsmax.ru/developers/
---

# Draft and launch an AppsMax campaign

> **This skill sends messages to real people.** AppsMax states plainly that the existence of a
> campaign endpoint does not override the law, the recipient's consent, or the rules of the
> messenger. Bulk marketing messages into MAX private chats are available only with separate
> platform permission. **An agent must not call `runCampaign` without an explicit human
> decision on this specific campaign.**

## Why creation and launch are two operations

AppsMax deliberately splits them. `createCampaign` produces a draft or scheduled record and
sends nothing. `runCampaign` is what moves it into launch/scheduling. Treat the gap between
them as the approval window — that is what it exists for.

## Steps

1. **Confirm scopes** — `getCurrentApiContext` (`GET /me`). You need `campaigns:write` to
   create and to run.

2. **Resolve the bot** — `listBots` (`GET /bots`); `bot_id` must belong to the token's
   organization.

3. **Size and inspect the audience** — `listSubscribers` (`GET /subscribers`) filtered by
   `bot_id`, `channel[]`, `status[]`, `tag`, `group_id`. Report the real count to the human
   before anything is created.

4. **Create the draft** — `createCampaign` (`POST /campaigns`) with `bot_id`, `title`,
   `content`, `channel`. **Send an `Idempotency-Key`** (1–128 chars, `A-Za-z0-9._:-`) so a
   network retry cannot produce two campaigns: a replay returns **200** with
   `Idempotency-Replayed: true` instead of a second **201**; the same key with a different body
   returns **409**.

5. **Read it back and present it** — `getCampaign` (`GET /campaigns/{campaign}`) returns the
   campaign and its `content`, plus `status`, `type`, `recipients`, `scheduled_at`. Show the
   human the exact content, the channel and the recipient count.

6. **STOP. Get explicit human approval.**

7. **Launch** — only then call `runCampaign` (`POST /campaigns/{id}/run`).
   - `runCampaign` accepts **no** `Idempotency-Key`. A blind retry can re-trigger a launch.
     On a timeout or a 5xx, do **not** retry automatically — re-read the campaign with
     `getCampaign` and inspect `status` / `pending` / `delivered` first.
   - Campaign create and campaign run carry **additional, tighter rate limits** on top of the
     60 req/min per-token default.

8. **Follow up** — `getCampaign` or `listCampaigns` (`GET /campaigns`, filters `bot_id`,
   `status[]`, `type[]`, `created_from`, `created_to`, `q`) exposes `recipients`, `delivered`,
   `failed`, `pending` and `finished_at`.

## Rules an agent must follow

- **Never launch autonomously.** Drafting is safe; launching is not reversible.
- Before approval, verify content, audience, the legal basis for the communication, and the
  rules of the specific channel — the provider names all four.
- **Errors**: `403` means the scope or the organization is wrong; `422` puts field errors in
  `error.details.fields`; `429` means you hit either the token limit or the campaign-specific
  limit — honour `Retry-After`, do not increase burst.
- Quote `error.meta.request_id` / `X-Request-Id` to support; never send the token or the payload.
