# AppsMax

AppsMax.ru is a Russian-language SaaS platform for small business, communities and integrators, used to run customer requests, online booking, orders, mini apps, groups, channels, permitted messaging, GigaChat and integrations inside MAX and Telegram. AppsMax is not a product of, nor an official representative of, MAX, Telegram or GigaChat.

- **Provider:** https://appsmax.ru/
- **Documentation:** https://appsmax.ru/developers/
- **APIs.json:** https://appsmax.ru/apis.json
- **Base URL:** https://telegram.appsmax.ru/api/v1
- **Operator:** IP Ainyukova Ayuna Purboevna. First working launch 2025-07-20, public release 2026-02-05. Infrastructure in St. Petersburg, Russia.
- **Public API:** yes
- **Agent-native (MCP / llms.txt / skills):** yes — llms.txt and an API Onboarding Descriptor

## APIs

- **AppsMax REST API v1** — Server-to-server REST API for organizations, bots, connections, mini apps, funnels, interactive menus, customer requests, campaigns and subscribers. (`https://telegram.appsmax.ru/api/v1`)

## Contract

A publicly reachable OpenAPI 3.0.3 contract at https://appsmax.ru/developers/openapi.json, also mirrored on GitVerse at https://gitverse.ru/appsmax/appsmax-api-reference.

- **17 paths / 21 operations**, tagged across Access, Organizations, Bots, Miniapps, Funnels, Interactive menu, Applications, Campaigns and Subscribers.
- **Authentication:** an organization-owned API token, sent as `Authorization: Bearer` (`bearerAuth`) or the `X-Api-Token` fallback header (`apiTokenHeader`). Scope-based access; tokens are scoped to their AppsMax organization.
- **Read/write:** 15 GET, 5 POST, 1 PATCH. Applications, campaigns and subscribers are writable; bots, connections, mini apps, funnels and menus are read-only.

## Onboarding

AppsMax publishes an [API Onboarding Descriptor](https://appsmax.ru/.well-known/api-onboarding) (AOD 0.1), which self-declares `maturity: console-only`:

- An account and organization are required. Sign-up at https://telegram.appsmax.ru/register.
- Token issuance is **console-only** — a signed-in user opens Data → Integrations → API in the AppsMax cabinet, selects the minimum required scopes and creates the token. There is no programmatic token-issuance endpoint.
- Tokens are shown once and rotated by revoke-and-replace.
- REST API access is gated to the paid **Профи (Profi)** plan. The **Старт (Start)** tier is free (0 ₽); a 7-day Profi trial is available in the cabinet, with the countdown starting at real launch rather than at registration. Paid plans start at 490 ₽/month.

## Notes

Every property advertised in the provider's APIs.json was fetched and confirmed reachable on 2026-08-01: documentation, OpenAPI, getting started, authentication, API onboarding, rate limits, pricing, terms of service, privacy policy, support and llms.txt.

No MCP server (hosted or local), no agent skills, no llms-full.txt, no GraphQL, AsyncAPI or Postman collection, and no official SDK. Outbound webhooks exist in the cabinet but their contract is not part of the public reference.

_Built from the provider's own APIs.json at https://appsmax.ru/apis.json (apis.io submission 449f5bad-f495-4073-938a-4da9a1e356c7)._
