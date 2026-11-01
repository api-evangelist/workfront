# Adobe Workfront

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

Adobe Workfront is Adobe's enterprise work-management platform for marketing and creative operations — project and portfolio planning, request intake, task and resource management, proofing and approvals, timesheets, financial tracking and reporting — sold in Select, Prime and Ultimate packages. Its developer surface is unusually wide for a work-management vendor: a versioned REST core API at /attask/api (v22.0, 174 objects exposed through an anonymous object-metadata endpoint), the separately versioned Workfront Planning API published as first-party OpenAPI 3.0.1 and 3.1.0 documents on developer.adobe.com, an Event Subscription API that pushes object change events to customer webhook endpoints, a Document Webhooks API third-party document providers implement, and — since June 2026 — a hosted Model Context Protocol server at mcp.workfront.adobe.com exposing 87 documented tools behind OAuth 2.1, plus first-party agent Skills published in the adobe/skills repository.

**Areas:** Company · Work Management · Project Management · Marketing Operations · Creative Operations · Collaboration · Approvals · Resource Management · Workflow Automation · Enterprise Software · Adobe · MCP

## Adobe Workfront on APIs.io

Everything profiled for Adobe Workfront is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/workfront/](https://apis.io/providers/workfront/)** — or go straight to one of the APIs or properties below.

### APIs (9)

- [Adobe Workfront API](https://apis.io/apis/workfront/workfront-api/) — The core Workfront REST API. Every object in the system has a URI of the form /attask/api/v22.0/{objCode}/{id}; GET retrieves or searches, POST inserts, PUT…
- [Adobe Workfront Event Subscription API](https://apis.io/apis/workfront/workfront-event-subscription-api/) — The Workfront webhook/event surface. A system administrator registers a subscription for an object type (objCode) and event type (CREATE, UPDATE, DELETE)…
- [Adobe Workfront MCP Server](https://apis.io/apis/workfront/workfront-mcp-server/) — Adobe's hosted Model Context Protocol server for Workfront, generally available since June 2026. It exposes 87 documented tools across three families —…
- [Adobe Workfront Fields API](https://apis.io/apis/workfront/workfront-fields-api/) — Field management. Per-record-type quotas: max 500 fields total; max 20 PARAGRAPH (long-text) fields; max 20 FORMULA fields; max 30 REFERENCE fields. Field…
- [Adobe Workfront Permissions API](https://apis.io/apis/workfront/workfront-permissions-api/) — Resource permissions, member management, and access requests.
- [Adobe Workfront Record Types API](https://apis.io/apis/workfront/workfront-record-types-api/) — Record Type Controller
- [Adobe Workfront Records API](https://apis.io/apis/workfront/workfront-records-api/) — Record Controller
- [Adobe Workfront Views API](https://apis.io/apis/workfront/workfront-views-api/) — View management. Limits: max 100 personal views per record type; max 255 characters for view name.
- [Adobe Workfront Workspaces API](https://apis.io/apis/workfront/workfront-workspaces-api/) — Workspace Controller

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Workfront Event Subscriptions Webhooks](https://apis.io/asyncapis/workfront/workfront-event-subscriptions-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [Adobe Workfront MCP server](https://apis.io/servers/workfront/adobe-workfront-mcp-server/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Workfront Agentic Access](https://apis.io/agentic-access/workfront/workfront-agentic-access/)

#### Collections (2)

Postman and Open Collection request collections.

- [Workfront Planning API Version 1](https://apis.io/collections/workfront/open-workfront-planning-v1/)
- [Workfront Planning API Version 2](https://apis.io/collections/workfront/open-workfront-planning-v2/)

#### Overlays (8)

OpenAPI overlays, including conversational phrasing for each operation.

- [Workfront Fields Api Phrasing Overlay](https://apis.io/overlays/workfront/workfront-fields-api-phrasing-overlay/)
- [Workfront Permissions Api Phrasing Overlay](https://apis.io/overlays/workfront/workfront-permissions-api-phrasing-overlay/)
- [Workfront Planning V1 Overlay](https://apis.io/overlays/workfront/workfront-planning-v1-overlay/)
- [Workfront Planning V2 Overlay](https://apis.io/overlays/workfront/workfront-planning-v2-overlay/)
- [Workfront Record Types Api Phrasing Overlay](https://apis.io/overlays/workfront/workfront-record-types-api-phrasing-overlay/)
- [Workfront Records Api Phrasing Overlay](https://apis.io/overlays/workfront/workfront-records-api-phrasing-overlay/)
- [Workfront Views Api Phrasing Overlay](https://apis.io/overlays/workfront/workfront-views-api-phrasing-overlay/)
- [Workfront Workspaces Api Phrasing Overlay](https://apis.io/overlays/workfront/workfront-workspaces-api-phrasing-overlay/)

#### Security (4)

Authentication, trust centre, and vulnerability disclosure.

- [Workfront Authentication](https://apis.io/security/workfront/workfront-authentication/)
- [Workfront Domain Security](https://apis.io/security/workfront/workfront-domain-security/)
- [Workfront Trust Center](https://apis.io/security/workfront/workfront-trust-center/)
- [Workfront Vulnerability Disclosure](https://apis.io/security/workfront/workfront-vulnerability-disclosure/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Workfront Scopes](https://apis.io/scopes/workfront/workfront-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Workfront Plans Pricing](https://apis.io/plans/workfront/workfront-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Workfront Rate Limits](https://apis.io/rate-limits/workfront/workfront-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://business.adobe.com/products/workfront/main.html)
- [Documentation](https://experienceleague.adobe.com/en/docs/workfront/using/adobe-workfront-api/workfront-api)
- [Getting started](https://experienceleague.adobe.com/en/docs/workfront/using/adobe-workfront-api/api-general-information/api-basics)
- [API reference](https://developersupport.workfront.com/page-api-explorer.html)
- [Pricing](https://business.adobe.com/products/workfront/pricing.html)
- [Support](https://experienceleaguecommunities.adobe.com/t5/workfront/ct-p/workfront-community)
- [Changelog](https://experienceleague.adobe.com/en/docs/workfront/using/product-announcements/product-releases/product-releases)
- [Security](https://helpx.adobe.com/security.html)
- [Compliance](https://www.adobe.com/trust/compliance/compliance-list.html)
- [Trust centre](https://www.adobe.com/trust.html)
- [Terms of service](https://www.adobe.com/legal/terms.html)
- [Privacy policy](https://www.adobe.com/privacy/policy.html)
- [GitHub](https://github.com/Workfront)
- [Status](https://status.adobe.com/)

## API Evangelist rating

**Kin Score 70.4** — exemplar · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 75.0 |
| Contract quality | 56.4 |
| Contract governance | 4.5 |
| Operational transparency | 78.9 |
| Developer ergonomics | 83.3 |
| Access clarity | 73.7 |

**Agent readiness 59.2** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | verified |
| Auth Clarity | served (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | partial |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | yes |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | verified |
| Dynamic Client Registration | yes |
| Agentic Commerce | — |
| Pagination Ratio | partial |
| Operation Distinctiveness | — |

**Regulatory alignment 45.1** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/workfront/](https://apis.io/providers/workfront/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Adobe Workfront: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/workfront/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
