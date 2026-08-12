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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Adobe Workfront is Adobe's enterprise work-management platform for marketing and creative operations.
It was surfaced via the API Evangelist harvest backlog (source: marketing-integration-graph) and has
since been profiled by the full enrichment pipeline.

- Product: https://business.adobe.com/products/workfront/main.html
- API documentation: https://experienceleague.adobe.com/en/docs/workfront/using/adobe-workfront-api/workfront-api
- API Explorer: https://developersupport.workfront.com/page-api-explorer.html
- Planning API reference (OpenAPI): https://developer.adobe.com/wf-planning
- GitHub: https://github.com/Workfront

> **Correction to the original harvest.** This repository was created with `https://workfront.ai/` as
> the company website. That domain is *not* Adobe Workfront — it is an unrelated AI-training business
> in Nocatee, Florida, running on a GoDaddy website builder. The website property has been corrected
> to Adobe's own Workfront product page.

## What was found

| Surface | Result |
|---|---|
| OpenAPI | Two first-party Adobe specs — Workfront Planning API **v2** (OpenAPI 3.1.0, 21 paths / 49 operations / 74 schemas) and **v1** (OpenAPI 3.0.1, 7 paths / 10 operations), published at `developer.adobe.com/wf-planning/v{1,2}.json` |
| Core API contract | No OpenAPI. Adobe serves an anonymous **object-metadata** contract at `api-cl01.my.workfront.com/attask/api/v22.0/metadata` — 174 objects with fields, references, collections, searchable fields, named queries, actions and supported operations |
| MCP | Hosted server at `mcp.workfront.adobe.com/mcp/v1/workfront`, GA June 2026, **87 documented tools**, OAuth 2.1 (`tools/list` returns 401 with an RFC 9728 challenge) |
| Agent Skills | **Five first-party Adobe skills** harvested verbatim from `github.com/adobe/skills` (Apache-2.0), plus two generated here |
| Events | Event Subscription API (30 object types, CREATE/UPDATE/DELETE) and the Document Webhooks API. No AsyncAPI published |
| A2A | **No agent card** on any host — the 200s on `developer.adobe.com` and `api-cl01.my.workfront.com` are SPA catch-alls returning HTML, and were rejected |
| Well-known | RFC 8414 + RFC 9728 OAuth discovery on the MCP host; PGP-signed RFC 9116 `security.txt` on `www.adobe.com` |
