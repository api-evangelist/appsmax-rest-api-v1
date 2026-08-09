---
name: Inventory an AppsMax bot estate
description: >-
  Walk an AppsMax organization read-only — its bots, channel connections, mini apps, funnels
  and interactive menus — to produce an accurate picture of what is deployed before changing
  anything.
api: openapi/appsmax-rest-api-v1-openapi-original.json
base_url: https://telegram.appsmax.ru/api/v1
operations:
  - ping
  - getCurrentApiContext
  - listOrganizations
  - listBots
  - getBot
  - listBotConnections
  - listMiniapps
  - listFunnels
  - listInteractiveMenuItems
scopes:
  - organizations:read
  - bots:read
  - connections:read
  - miniapps:read
  - funnels:read
  - interactive_menu:read
generated: '2026-08-09'
method: generated
source: openapi/appsmax-rest-api-v1-openapi-original.json + https://appsmax.ru/developers/
---

# Inventory an AppsMax bot estate

A **read-only** skill. Use a token granted only the six `:read` scopes above — AppsMax's own
guidance is to split read and write tokens where the integration allows it.

## Steps

1. **Verify the token** — `ping` (`GET /ping`) confirms the token and organization context;
   `getCurrentApiContext` (`GET /me`) returns the token's name, `scopes`, `rate_limit` and
   `last_used_at`, plus the organization. Both require a valid token.

2. **The tenant** — `listOrganizations` (`GET /organizations`) returns the current
   organization: `id`, `name`, `slug`, `plan`, contact fields.

3. **The bots** — `listBots` (`GET /bots`, filters `driver`, `status`, `per_page` ≤ 100).
   Each bot exposes its feature flags: `scenarios_active`, `commands_active`,
   `interactive_menu_active`, `miniapps_active`, `subscribers_active`, `groups_active`,
   `channels_active`. `getBot` (`GET /bots/{bot}`) reads a single card.

4. **Channel bindings** — for each bot, `listBotConnections`
   (`GET /bots/{bot}/connections`) returns `driver`, `status`, `identifier`, `last_synced_at`
   and a driver-specific `profile`: a Telegram profile (username, `can_join_groups`,
   `can_read_all_group_messages`, `supports_inline_queries`, …) or a MAX profile
   (`user_id`, `name`, `username`). A stale `last_synced_at` is the first thing to flag.

5. **What is deployed on each bot**
   - `listMiniapps` (`GET /miniapps`, filters `bot_id`, `status`) — `slug`, `status`, `published_at`.
   - `listFunnels` (`GET /funnels`, filters `bot_id`, `active`) — `is_active`, `restart_mode`, `version`.
   - `listInteractiveMenuItems` (`GET /interactive-menu`, filters `bot_id`, `active`,
     `per_page` ≤ **200**) — a tree: `parent_id` points at another menu item. Rebuild the tree
     by `parent_id` and order by `sort_order`.

## Rules an agent must follow

- **Pagination**: follow the `links` next-page URL in the collection envelope
  (`{ data, links, meta }`) rather than incrementing `page`. `per_page` is clamped by the
  server — 100 everywhere except interactive menu, which allows 200.
- **Rate limit**: 60 requests/minute per token by default. A per-bot fan-out across five
  collections hits this quickly on a large estate — pace it and read `X-RateLimit-Remaining`.
- **Tenancy**: an object outside the token's organization is `403` or `404` by design. Do not
  probe id ranges.
- **Do not cache** responses: the API sets `Cache-Control: no-store, private`.
- Some references have no v1 endpoint behind them — `Funnel.start_block_id`,
  `InteractiveMenuItem.survey_template_id` and `linked_command_id` cannot be resolved through
  this API. Report them as opaque rather than guessing.
