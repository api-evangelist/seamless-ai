# Seamless.AI (seamless-ai)

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

Seamless.AI is a B2B sales intelligence platform that provides real-time contact and company data to help sales teams find and connect with their ideal customers. The platform uses artificial intelligence to continuously verify and update contact information including emails, direct dials, and mobile numbers. Seamless.AI offers a RESTful API secured with OAuth 2.0 and API key authentication, enabling developers to integrate contact search, company search, enrichment, and job-change intelligence directly into CRM systems, marketing platforms, and internal sales tools.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/seamless-ai/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/seamless-ai/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Consuming
- **Access:** 3rd-Party

## Tags

- B2B
- Contact Data
- Sales Intelligence
- Prospecting
- Lead Generation
- CRM Enrichment

## Timestamps

- **Created:** 2026-05-02
- **Modified:** 2026-05-19

## APIs

### Seamless.AI Contacts API

The Seamless.AI Contacts API provides programmatic access to contact search, enrichment, and research capabilities. Search for B2B contacts by name, company, title, and location. Enrich existing contact records with emails, phone numbers, and job history. Access job-change intelligence to identify contacts that have recently changed roles.

- **Human URL:** [https://docs.seamless.ai/](https://docs.seamless.ai/)
- **Base URL:** `https://api.seamless.ai`

#### Tags

- Contacts
- Sales Intelligence
- B2B
- Prospecting

#### Properties

- [OpenAPI](openapi/seamless-ai-contacts-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/seamless-ai-contacts.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/seamless-ai-contacts.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Documentation](https://docs.seamless.ai/)

### Seamless.AI Companies API

The Seamless.AI Companies API enables programmatic search and research of company data including firmographics, revenue, employee count, technology stack, and company intelligence. Use company search result IDs or direct identifiers such as domain or company name to retrieve comprehensive company profiles.

- **Human URL:** [https://docs.seamless.ai/](https://docs.seamless.ai/)
- **Base URL:** `https://api.seamless.ai`

#### Tags

- Companies
- Firmographics
- Sales Intelligence
- B2B

#### Properties

- [OpenAPI](openapi/seamless-ai-companies-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/seamless-ai-companies.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/seamless-ai-companies.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Documentation](https://docs.seamless.ai/)

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/seamlessai)
- [Website](https://seamless.ai)
- [Documentation](https://docs.seamless.ai/)
- [Overview](https://seamless.ai/products/api)
- [Getting Started](https://seamless.ai/customers/education/articles/seamless-ai-api-overview)
- [Glossary](https://seamless.ai/customers/education/articles/api-terms-glossary)
- [Blog](https://seamless.ai/news/releases/api)
- [JSON Schema](json-schema/seamless-ai-contact-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/seamless-ai-company-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Structure](json-structure/seamless-ai-contact-structure.json)
- [J S O N L D Context](json-ld/seamless-ai-context.jsonld)
- [Example](examples/seamless-ai-search-contacts-example.json)
- [Spectral Ruleset](rules/seamless-ai-rules.yml)
- [Vocabulary](vocabulary/seamless-ai-vocabulary.yml)
- [L L Ms Txt](https://docs.seamless.ai/llms.txt)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
