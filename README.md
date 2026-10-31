# Seamless.AI

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

Seamless.AI is a B2B sales intelligence platform that provides real-time contact and company data to help sales teams find and connect with their ideal customers. The platform uses artificial intelligence to continuously verify and update contact information including emails, direct dials and mobile numbers. Its Public API v1 is a three-hop enrichment pipeline — search, research, then collect by polling or webhook — secured with an API key in a Token header or OAuth 2.0, and metered in research credits rather than API calls. Alongside the nine-operation REST API, Seamless.AI operates a hosted Model Context Protocol server exposing 54 tools across search, research, lists, saved searches, campaigns, templates, email, calls, tasks and activity, secured with OAuth 2.1, dynamic client registration and published per-tool risk tiers.

**Areas:** B2B · Contact Data · Sales Intelligence · Prospecting · Lead Generation · CRM Enrichment · Data Enrichment · MCP · Agents · Sales Automation · A2A

## Seamless.AI on APIs.io

Everything profiled for Seamless.AI is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/seamless-ai/](https://apis.io/providers/seamless-ai/)** — or go straight to one of the APIs or properties below.

### APIs (3)

- [Seamless.AI Public API](https://apis.io/apis/seamless-ai/seamless-ai-public-api/) — The Seamless.AI Public API v1 — nine operations covering contact and company search, asynchronous enrichment (research), result polling, org-data retrieval…
- [Seamless.AI MCP API](https://apis.io/apis/seamless-ai/seamless-ai-mcp-api/) — The Mcp API from Seamless.AI — 1 operation(s) for mcp.
- [Seamless.AI O Auth API](https://apis.io/apis/seamless-ai/seamless-ai-oauth-api/) — The OAuth API from Seamless.AI — 1 operation(s) for oauth.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Seamless Ai Webhooks](https://apis.io/asyncapis/seamless-ai/seamless-ai-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [seamless](https://apis.io/servers/seamless-ai/seamless/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Seamless Ai Agentic Access](https://apis.io/agentic-access/seamless-ai/seamless-ai-agentic-access/)

#### JSON Schema (2)

The data models the API reads and writes.

- [Seamless.AI Company](https://apis.io/schemas/seamless-ai/seamless-ai-company/)
- [Seamless.AI Contact](https://apis.io/schemas/seamless-ai/seamless-ai-contact/)

#### JSON Structure (2)

Data models expressed in JSON Structure.

- [Seamless Ai Company Structure](https://apis.io/json-structure/seamless-ai/seamless-ai-company-structure/)
- [Seamless Ai Contact Structure](https://apis.io/json-structure/seamless-ai/seamless-ai-contact-structure/)

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Seamless Ai Context](https://apis.io/jsonld/seamless-ai/seamless-ai-context/)

#### Vocabulary (1)

The provider's domain terms, defined.

- [Seamless.AI Vocabulary](https://apis.io/vocabularies/seamless-ai/seamless-ai-vocabulary/)

#### Examples (9)

Example requests and responses.

- [Seamless Ai Get Access Token Example](https://apis.io/examples/seamless-ai/seamless-ai-get-access-token-example/)
- [Seamless Ai Get Companies Example](https://apis.io/examples/seamless-ai/seamless-ai-get-companies-example/)
- [Seamless Ai Get Contacts Example](https://apis.io/examples/seamless-ai/seamless-ai-get-contacts-example/)
- [Seamless Ai Poll Company Research Results Example](https://apis.io/examples/seamless-ai/seamless-ai-poll-company-research-results-example/)
- [Seamless Ai Poll Contacts Research Results Example](https://apis.io/examples/seamless-ai/seamless-ai-poll-contacts-research-results-example/)
- [Seamless Ai Research Companies Example](https://apis.io/examples/seamless-ai/seamless-ai-research-companies-example/)
- [Seamless Ai Research Contacts Example](https://apis.io/examples/seamless-ai/seamless-ai-research-contacts-example/)
- [Seamless Ai Search Companies Example](https://apis.io/examples/seamless-ai/seamless-ai-search-companies-example/)
- [Seamless Ai Search Contacts Example](https://apis.io/examples/seamless-ai/seamless-ai-search-contacts-example/)

#### Overlays (15)

OpenAPI overlays, including conversational phrasing for each operation.

- [Seamless Ai Company Research Api Phrasing Overlay](https://apis.io/overlays/seamless-ai/seamless-ai-company-research-api-phrasing-overlay/)
- [Seamless Ai Company Research Overlay](https://apis.io/overlays/seamless-ai/seamless-ai-company-research-overlay/)
- [Seamless Ai Company Search Api Phrasing Overlay](https://apis.io/overlays/seamless-ai/seamless-ai-company-search-api-phrasing-overlay/)
- [Seamless Ai Company Search Overlay](https://apis.io/overlays/seamless-ai/seamless-ai-company-search-overlay/)
- [Seamless Ai Contact Research Api Phrasing Overlay](https://apis.io/overlays/seamless-ai/seamless-ai-contact-research-api-phrasing-overlay/)
- [Seamless Ai Contact Research Overlay](https://apis.io/overlays/seamless-ai/seamless-ai-contact-research-overlay/)
- [Seamless Ai Contact Search Api Phrasing Overlay](https://apis.io/overlays/seamless-ai/seamless-ai-contact-search-api-phrasing-overlay/)
- [Seamless Ai Contact Search Overlay](https://apis.io/overlays/seamless-ai/seamless-ai-contact-search-overlay/)
- [Seamless Ai Mcp Api Phrasing Overlay](https://apis.io/overlays/seamless-ai/seamless-ai-mcp-api-phrasing-overlay/)
- [Seamless Ai Oauth Api Phrasing Overlay](https://apis.io/overlays/seamless-ai/seamless-ai-oauth-api-phrasing-overlay/)
- [Seamless Ai Oauth Overlay](https://apis.io/overlays/seamless-ai/seamless-ai-oauth-overlay/)
- [Seamless Ai Org Companies Api Phrasing Overlay](https://apis.io/overlays/seamless-ai/seamless-ai-org-companies-api-phrasing-overlay/)
- [Seamless Ai Org Companies Overlay](https://apis.io/overlays/seamless-ai/seamless-ai-org-companies-overlay/)
- [Seamless Ai Org Contacts Api Phrasing Overlay](https://apis.io/overlays/seamless-ai/seamless-ai-org-contacts-api-phrasing-overlay/)
- [Seamless Ai Org Contacts Overlay](https://apis.io/overlays/seamless-ai/seamless-ai-org-contacts-overlay/)

#### Governance rules (2)

Spectral rulesets for the provider's contracts.

- [Seamless.AI — jsonschema rules](https://apis.io/rules/seamless-ai/seamless-ai-jsonschema-spectral-rules/)
- [Seamless.AI API Rules](https://apis.io/rules/seamless-ai/seamless-ai-rules/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Seamless Ai Authentication](https://apis.io/security/seamless-ai/seamless-ai-authentication/)
- [Seamless Ai Domain Security](https://apis.io/security/seamless-ai/seamless-ai-domain-security/)
- [Seamless Ai Trust Center](https://apis.io/security/seamless-ai/seamless-ai-trust-center/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Seamless Ai Scopes](https://apis.io/scopes/seamless-ai/seamless-ai-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Seamless Ai Plans Pricing](https://apis.io/plans/seamless-ai/seamless-ai-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Seamless Ai Rate Limits](https://apis.io/rate-limits/seamless-ai/seamless-ai-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Seamless Ai Finops](https://apis.io/finops/seamless-ai/seamless-ai-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://seamless.ai)
- [Documentation](https://docs.seamless.ai/)
- [Getting started](https://docs.seamless.ai/authenticate-and-make-your-first-request)
- [API reference](https://docs.seamless.ai/searchcontacts)
- [Pricing](https://seamless.ai/pricing)
- [Sign up](https://login.seamless.ai/register)
- [Support](https://seamless.ai/customers/education)
- [Blog](https://seamless.ai/customers/blog)
- [Compliance](https://trust.seamless.ai/)
- [Terms of service](https://seamless.ai/policies/terms-of-use)
- [Privacy policy](https://seamless.ai/policies/privacy-policy)
- [GitHub](https://github.com/SeamlessAI)

## API Evangelist rating

**Kin Score 65.5** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 75.0 |
| Contract quality | 61.4 |
| Contract governance | 31.8 |
| Operational transparency | 34.2 |
| Developer ergonomics | 65.5 |
| Access clarity | 92.1 |

**Agent readiness 55.3** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | documented (partial credit) |
| Auth Clarity | served (partial credit) |
| Idempotency | — |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | verified |
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
| Pagination Ratio | na |
| Operation Distinctiveness | na |

**Regulatory alignment 39.2** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/seamless-ai/](https://apis.io/providers/seamless-ai/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Seamless.AI: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/seamless-ai/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
