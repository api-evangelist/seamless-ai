---
name: Enrich contacts with Seamless.AI
description: >-
  Find B2B contacts by filter, submit them for enrichment, and collect verified emails and phone
  numbers by polling. Use when you have search criteria (title, company, industry, location) rather
  than a known person.
api: openapi/_original/seamless-ai-public-api-openapi-original.json
base_url: https://api.seamless.ai/api/client/v1
operations:
  - searchContacts
  - researchContacts
  - pollContactsResearchResults
generated: '2026-08-14'
method: generated
source: >-
  Grounded in the provider-published OpenAPI at https://docs.seamless.ai/openapi.json plus
  conventions/seamless-ai-conventions.yml, errors/seamless-ai-problem-types.yml and
  rate-limits/seamless-ai-rate-limits.yml. Every operationId below is verified present in that spec.
---

# Enrich contacts with Seamless.AI

Seamless.AI is not a request/response lookup API. It is a **three-hop pipeline**: search, then
research, then collect. Each hop hands a different identifier to the next, and mixing them up is
the most common way this integration fails.

## Authenticate

Send the API key raw in the `Token` header — no `Bearer`, no scheme prefix:

```
Token: <SEAMLESS_API_KEY>
```

If you are acting on a user's behalf via OAuth instead, send `Authorization: Bearer <access_token>`
and make sure the connection carries the `publicAPI.v1.all` scope. **Never send both headers on one
request.** Keys are created at Settings → Public API in the Seamless app.

## Step 1 — `searchContacts`

`POST /search/contacts`. Send filters (`jobTitle`, `seniority`, `companyName`, `companyDomain`,
`industry`, `contactState`, `technologies`, `companySize`, `companyRevenue`, …) plus `limit`.

Search is **free** — it spends no research credits. Save the `searchResultId` off each match you
want enriched; that value is the only thing step 2 accepts. Paginate by passing the returned
`nextToken` back as `nextToken` on the next call. Search results are *unenriched*: they carry name,
title and company but not a verified email or phone.

## Step 2 — `researchContacts`

`POST /contacts/research`. Send `searchResultIds: [...]` — an array, so batch rather than looping
one at a time.

You can also skip search entirely and pass a `contacts` array of identifiers (name + company, plus
optional title) when you already have them from a CRM or spreadsheet. Do not guess identifiers; a
wrong one costs a credit and returns `missing`.

This is the **only operation that spends credits**. It returns `202 Accepted` with `requestIds` —
a *different* identifier from `searchResultId`. Save it immediately; if you lose it you must start
over from search.

Set `skipDeduplicationCheck` only if you deliberately want to re-research a record you already
hold. Leaving it off is what protects your credit balance.

## Step 3 — `pollContactsResearchResults`

`GET /contacts/research/poll?requestIds=<id>`. Poll every **2–5 seconds**. Tight loops burn the
endpoint's rate-limit window and get you nothing faster.

**The HTTP status is not the outcome.** A completed, a failed and an in-flight job all return
`200`. Branch on the body's `status` field:

| `status` | Meaning | Do |
| --- | --- | --- |
| `researching` | Still running | Poll again in 2–5s |
| `done` | Complete | Read the enriched record from `contact` |
| `missing` | Not in the database | Surface it. Do not retry — it will not appear |
| `error` | Failed | Check credits and license. Do not auto-retry |
| `duplicate` | Already researched | Use the returned result. Do not resubmit |

Stop only on a terminal status (`done`, `missing`, `error`, `duplicate`).

## Reading the enriched contact

The record has ~101 fields. Note two shapes before you write mapping code:

- **Confidence scores are percentage STRINGS**, not numbers — `contactPhone1TotalAI: "98%"`. Parse
  before comparing.
- **Company data is denormalized onto the contact** and there is no company foreign key. Join back
  to a Company by `domain` or `companyName`.

## Runtime rules

- **Rate limit**: 60 requests per minute, per endpoint, per *organization* — every key and user in
  the org shares the window. Read `X-RateLimit-Limit`; a custom limit may apply.
- **On 429**: there is **no `Retry-After` header**. Read `X-RateLimit-Reset` (epoch seconds) and
  sleep until that timestamp. Generic Retry-After backoff will not work here.
- **Credits**: watch `X-PublicAPI-Credits` on every response. There is no endpoint that returns a
  balance.
- **On 422**: read the `code` field. `insufficientCredits` means top up or shrink the batch;
  `missingLicense` means the org has no Public API license and no amount of retrying will fix it.
- **No idempotency key exists.** A retried research POST is a new job against a new credit unless
  the platform's own dedupe catches it. Track `requestId`s yourself.
- **Never hardcode the key.** Use an environment variable or a secret manager.

## When to use something else

- Already have a domain or a name from your CRM → skip search, call `researchContacts` directly.
- Need results pushed rather than polled → configure a `contact-researched` webhook and match
  deliveries by `apiResearchId`, which equals your `requestId`. See
  `asyncapi/seamless-ai-webhooks.yml`.
- Only need records you already researched → call `getContacts`, which is free and spends no
  credits.
