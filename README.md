# AppsMax (appsmax.ru:api-catalog)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

AppsMax.ru is a Russian-language SaaS platform for small business, communities and integrators, used to run customer requests, online booking, orders, mini apps, groups, channels, permitted messaging, GigaChat and integrations inside MAX and Telegram. Its developer surface is a single server-to-server REST API (v1) with a published OpenAPI 3.0.3 contract, an APIs.json index, an API Onboarding Descriptor and an llms.txt. AppsMax is not a product of, nor an official representative of, MAX, Telegram or GigaChat.

**APIs.json:** [https://appsmax-rest-api-v1.apievangelist.com/apis.yml](https://appsmax-rest-api-v1.apievangelist.com/apis.yml)

## Scope

- **Type:** Index

## Tags

- Company
- SaaS
- Messaging
- Business Automation
- Chatbots
- Mini Apps
- Customer Requests
- Workflow Automation
- MAX
- Telegram
- Russian Language

## Timestamps

- **Created:** 2026-07-31
- **Modified:** 2026-08-09

## APIs

### AppsMax Access API

Проверка токена и контекста организации.

- **Human URL:** [https://appsmax.ru/developers/](https://appsmax.ru/developers/)
- **Base URL:** `https://telegram.appsmax.ru/api/v1`

#### Tags

- Access

#### Properties

- [OpenAPI](openapi/appsmax-rest-api-v1-access-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/appsmax-rest-api-v1-access-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/appsmax-rest-api-v1-access-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Documentation](https://appsmax.ru/developers/)
- [Getting Started](https://appsmax.ru/developers/#quick-start)
- [Authentication](https://appsmax.ru/developers/#authentication)
- [A P I Onboarding](https://appsmax.ru/.well-known/api-onboarding)
- [Rate Limits](https://appsmax.ru/developers/#errors)
- [Pricing](https://appsmax.ru/pricing/)
- [Terms of Service](https://appsmax.ru/documents/publichnaya-oferta/)
- [Privacy Policy](https://appsmax.ru/documents/politika-obrabotki-personalnyh-dannyh/)
- [Support](https://appsmax.ru/contacts/)
- [L L M S Txt](https://appsmax.ru/llms.txt)

### AppsMax Applications API

Заявки и их теги.

- **Human URL:** [https://appsmax.ru/developers/](https://appsmax.ru/developers/)
- **Base URL:** `https://telegram.appsmax.ru/api/v1`

#### Tags

- Applications

#### Properties

- [OpenAPI](openapi/appsmax-rest-api-v1-applications-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/appsmax-rest-api-v1-applications-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/appsmax-rest-api-v1-applications-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Documentation](https://appsmax.ru/developers/)
- [Getting Started](https://appsmax.ru/developers/#quick-start)
- [Authentication](https://appsmax.ru/developers/#authentication)
- [A P I Onboarding](https://appsmax.ru/.well-known/api-onboarding)
- [Rate Limits](https://appsmax.ru/developers/#errors)
- [Pricing](https://appsmax.ru/pricing/)
- [Terms of Service](https://appsmax.ru/documents/publichnaya-oferta/)
- [Privacy Policy](https://appsmax.ru/documents/politika-obrabotki-personalnyh-dannyh/)
- [Support](https://appsmax.ru/contacts/)
- [L L M S Txt](https://appsmax.ru/llms.txt)

### AppsMax Bots API

Боты и их безопасные сведения о подключении без секретов.

- **Human URL:** [https://appsmax.ru/developers/](https://appsmax.ru/developers/)
- **Base URL:** `https://telegram.appsmax.ru/api/v1`

#### Tags

- Bots

#### Properties

- [OpenAPI](openapi/appsmax-rest-api-v1-bots-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/appsmax-rest-api-v1-bots-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/appsmax-rest-api-v1-bots-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Documentation](https://appsmax.ru/developers/)
- [Getting Started](https://appsmax.ru/developers/#quick-start)
- [Authentication](https://appsmax.ru/developers/#authentication)
- [A P I Onboarding](https://appsmax.ru/.well-known/api-onboarding)
- [Rate Limits](https://appsmax.ru/developers/#errors)
- [Pricing](https://appsmax.ru/pricing/)
- [Terms of Service](https://appsmax.ru/documents/publichnaya-oferta/)
- [Privacy Policy](https://appsmax.ru/documents/politika-obrabotki-personalnyh-dannyh/)
- [Support](https://appsmax.ru/contacts/)
- [L L M S Txt](https://appsmax.ru/llms.txt)

### AppsMax Campaigns API

Рассылки и их запуск.

- **Human URL:** [https://appsmax.ru/developers/](https://appsmax.ru/developers/)
- **Base URL:** `https://telegram.appsmax.ru/api/v1`

#### Tags

- Campaigns

#### Properties

- [OpenAPI](openapi/appsmax-rest-api-v1-campaigns-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/appsmax-rest-api-v1-campaigns-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/appsmax-rest-api-v1-campaigns-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Documentation](https://appsmax.ru/developers/)
- [Getting Started](https://appsmax.ru/developers/#quick-start)
- [Authentication](https://appsmax.ru/developers/#authentication)
- [A P I Onboarding](https://appsmax.ru/.well-known/api-onboarding)
- [Rate Limits](https://appsmax.ru/developers/#errors)
- [Pricing](https://appsmax.ru/pricing/)
- [Terms of Service](https://appsmax.ru/documents/publichnaya-oferta/)
- [Privacy Policy](https://appsmax.ru/documents/politika-obrabotki-personalnyh-dannyh/)
- [Support](https://appsmax.ru/contacts/)
- [L L M S Txt](https://appsmax.ru/llms.txt)

### AppsMax Funnels API

Сценарии и воронки ботов.

- **Human URL:** [https://appsmax.ru/developers/](https://appsmax.ru/developers/)
- **Base URL:** `https://telegram.appsmax.ru/api/v1`

#### Tags

- Funnels

#### Properties

- [OpenAPI](openapi/appsmax-rest-api-v1-funnels-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/appsmax-rest-api-v1-funnels-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/appsmax-rest-api-v1-funnels-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Documentation](https://appsmax.ru/developers/)
- [Getting Started](https://appsmax.ru/developers/#quick-start)
- [Authentication](https://appsmax.ru/developers/#authentication)
- [A P I Onboarding](https://appsmax.ru/.well-known/api-onboarding)
- [Rate Limits](https://appsmax.ru/developers/#errors)
- [Pricing](https://appsmax.ru/pricing/)
- [Terms of Service](https://appsmax.ru/documents/publichnaya-oferta/)
- [Privacy Policy](https://appsmax.ru/documents/politika-obrabotki-personalnyh-dannyh/)
- [Support](https://appsmax.ru/contacts/)
- [L L M S Txt](https://appsmax.ru/llms.txt)

### AppsMax Interactive menu API

Элементы интерактивного меню ботов.

- **Human URL:** [https://appsmax.ru/developers/](https://appsmax.ru/developers/)
- **Base URL:** `https://telegram.appsmax.ru/api/v1`

#### Tags

- Interactive menu

#### Properties

- [OpenAPI](openapi/appsmax-rest-api-v1-interactive-menu-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/appsmax-rest-api-v1-interactive-menu-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/appsmax-rest-api-v1-interactive-menu-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Documentation](https://appsmax.ru/developers/)
- [Getting Started](https://appsmax.ru/developers/#quick-start)
- [Authentication](https://appsmax.ru/developers/#authentication)
- [A P I Onboarding](https://appsmax.ru/.well-known/api-onboarding)
- [Rate Limits](https://appsmax.ru/developers/#errors)
- [Pricing](https://appsmax.ru/pricing/)
- [Terms of Service](https://appsmax.ru/documents/publichnaya-oferta/)
- [Privacy Policy](https://appsmax.ru/documents/politika-obrabotki-personalnyh-dannyh/)
- [Support](https://appsmax.ru/contacts/)
- [L L M S Txt](https://appsmax.ru/llms.txt)

### AppsMax Miniapps API

Мини-приложения организации.

- **Human URL:** [https://appsmax.ru/developers/](https://appsmax.ru/developers/)
- **Base URL:** `https://telegram.appsmax.ru/api/v1`

#### Tags

- Miniapps

#### Properties

- [OpenAPI](openapi/appsmax-rest-api-v1-miniapps-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/appsmax-rest-api-v1-miniapps-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/appsmax-rest-api-v1-miniapps-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Documentation](https://appsmax.ru/developers/)
- [Getting Started](https://appsmax.ru/developers/#quick-start)
- [Authentication](https://appsmax.ru/developers/#authentication)
- [A P I Onboarding](https://appsmax.ru/.well-known/api-onboarding)
- [Rate Limits](https://appsmax.ru/developers/#errors)
- [Pricing](https://appsmax.ru/pricing/)
- [Terms of Service](https://appsmax.ru/documents/publichnaya-oferta/)
- [Privacy Policy](https://appsmax.ru/documents/politika-obrabotki-personalnyh-dannyh/)
- [Support](https://appsmax.ru/contacts/)
- [L L M S Txt](https://appsmax.ru/llms.txt)

### AppsMax Organizations API

Организация, к которой привязан токен.

- **Human URL:** [https://appsmax.ru/developers/](https://appsmax.ru/developers/)
- **Base URL:** `https://telegram.appsmax.ru/api/v1`

#### Tags

- Organizations

#### Properties

- [OpenAPI](openapi/appsmax-rest-api-v1-organizations-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/appsmax-rest-api-v1-organizations-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/appsmax-rest-api-v1-organizations-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Documentation](https://appsmax.ru/developers/)
- [Getting Started](https://appsmax.ru/developers/#quick-start)
- [Authentication](https://appsmax.ru/developers/#authentication)
- [A P I Onboarding](https://appsmax.ru/.well-known/api-onboarding)
- [Rate Limits](https://appsmax.ru/developers/#errors)
- [Pricing](https://appsmax.ru/pricing/)
- [Terms of Service](https://appsmax.ru/documents/publichnaya-oferta/)
- [Privacy Policy](https://appsmax.ru/documents/politika-obrabotki-personalnyh-dannyh/)
- [Support](https://appsmax.ru/contacts/)
- [L L M S Txt](https://appsmax.ru/llms.txt)

### AppsMax Subscribers API

Подписчики и их сегментационные теги.

- **Human URL:** [https://appsmax.ru/developers/](https://appsmax.ru/developers/)
- **Base URL:** `https://telegram.appsmax.ru/api/v1`

#### Tags

- Subscribers

#### Properties

- [OpenAPI](openapi/appsmax-rest-api-v1-subscribers-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/appsmax-rest-api-v1-subscribers-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/appsmax-rest-api-v1-subscribers-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Documentation](https://appsmax.ru/developers/)
- [Getting Started](https://appsmax.ru/developers/#quick-start)
- [Authentication](https://appsmax.ru/developers/#authentication)
- [A P I Onboarding](https://appsmax.ru/.well-known/api-onboarding)
- [Rate Limits](https://appsmax.ru/developers/#errors)
- [Pricing](https://appsmax.ru/pricing/)
- [Terms of Service](https://appsmax.ru/documents/publichnaya-oferta/)
- [Privacy Policy](https://appsmax.ru/documents/politika-obrabotki-personalnyh-dannyh/)
- [Support](https://appsmax.ru/contacts/)
- [L L M S Txt](https://appsmax.ru/llms.txt)

## Common Properties

- [M C P Server](mcp/appsmax-rest-api-v1-mcp.yml)
- [Agentic Access](agentic-access/appsmax-rest-api-v1-agentic-access.yml)
- [Domain Security](security/appsmax-rest-api-v1-domain-security.yml)
- [Authentication](authentication/appsmax-rest-api-v1-authentication.yml)
- [Website](https://appsmax.ru/)
- [A P Is J S O N](https://appsmax.ru/apis.json)
- [Developer Portal](https://appsmax.ru/developers/)
- [API Reference](https://appsmax.ru/developers/#methods)
- [Blog](https://appsmax.ru/news/)
- [Blog R S S](https://appsmax.ru/news/feed/)
- [Sign Up](https://telegram.appsmax.ru/register)
- [Login](https://telegram.appsmax.ru/login)
- [Help Center](https://appsmax.ru/kb/)
- [F A Q](https://appsmax.ru/faq/)
- [Source Code](https://gitverse.ru/appsmax/appsmax-api-reference)
- [Postman](https://gitverse.ru/appsmax/appsmax-api-reference) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Conventions](conventions/appsmax-rest-api-v1-conventions.yml)
- [Idempotency](conventions/appsmax-rest-api-v1-conventions.yml)
- [Error Catalog](errors/appsmax-rest-api-v1-problem-types.yml)
- [Lifecycle](lifecycle/appsmax-rest-api-v1-lifecycle.yml)
- [Scopes](scopes/appsmax-rest-api-v1-scopes.yml)
- [Conformance](conformance/appsmax-rest-api-v1-conformance.yml)
- [Data Model](data-model/appsmax-rest-api-v1-data-model.yml)
- [Packages](packages/appsmax-rest-api-v1-packages.yml)
- [Well Known](well-known/appsmax-rest-api-v1-well-known.yml)
- [L L Ms Txt](llms/appsmax-rest-api-v1-llms.txt)
- [Overlay](overlays/appsmax-rest-api-v1-rest-api-v1-overlay.yaml)
- [Examples](examples/_index.yml)
- [Agent Skill](skills/_index.yml)
- [Rate Limits](rate-limits/appsmax-rest-api-v1-rate-limits.yml)
- [Plans](plans/appsmax-rest-api-v1-plans.yml)
- [Vulnerability Disclosure](security/appsmax-rest-api-v1-vulnerability-disclosure.yml)
- [Security](https://gitverse.ru/appsmax/appsmax-api-reference)

## Maintainers

**FN:** AppsMax.ru team
**Email:** info@appsmax.ru
**URL:** https://appsmax.ru/developers/
