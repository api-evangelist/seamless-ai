---
name: Enrich companies with Seamless.AI
description: >-
  Search companies by firmographics, submit them for enrichment, and collect revenue, headcount,
  technology stack and funding data by polling. Use for account research, TAM building and CRM
  account hygiene.
api: openapi/_original/seamless-ai-public-api-openapi-original.json
base_url: https://api.seamless.ai/api/client/v1
operations:
  - searchCompanies
  - researchCompanies
  - pollCompanyResearchResults
  - getCompanies
generated: '2026-08-14'
method: generated
source: >-
  Grounded in the provider-published OpenAPI at https://docs.seamless.ai/openapi.json. Every
  operationId below is verified present in that spec.
---

# Enrich companies with Seamless.AI

Same three-hop pipeline as contacts — search → research → poll — against the company graph.

## Authenticate

`Token: <SEAMLESS_API_KEY>` (raw key, no prefix), or `Authorization: Bearer <access_token>` with
scope `publicAPI.v1.all`. Never both on one request.

## Step 1 — `searchCompanies`

`POST /search/companies`. Filters include `companyName`, `companyNameSearchType`, `companyDomain`,
`companyState`, `companyCountry`, `companyZipCode`, `industry`, `companyKeyword`, `companySize`,
`companyRevenue`, `technologies` (with `technologiesIsOr` to switch AND/OR), `companyType`,
`foundedOn`, `newsTypes`, `latestFundingDates`, `latestFundingClassifications` and
`latestFundingTotals`.

Free — no credits. Save each `searchResultId`. Paginate with `nextToken`.

The funding and news filters are the ones worth knowing: they let you build a list of *companies
that just raised* or *companies with a specific news event*, which is the intent-signal use case
rather than plain firmographic filtering.

## Step 2 — `researchCompanies`

`POST /companies/research` with `searchResultIds: [...]`, or skip search and pass a `companies`
array of `{domain, companyName}` when you already hold identifiers — the normal path when you are
cleaning an existing CRM account list.

Spends credits. Returns `202` with `requestIds`. Save them.

## Step 3 — `pollCompanyResearchResults`

`GET /companies/research/poll?requestIds=<id>`, every 2–5 seconds, until the body `status` is
terminal (`done`, `missing`, `error`). Remember the outcome lives in the **body**, not the HTTP
status — every one of those returns `200`.

The enriched Company record carries ~51 fields: firmographics, `revenueRange`, `staffCountRange`,
technologies, `location`, `newsAndEvents`, funding classifications and `linkedInProfileUrl`. There
is no first-party company id — the closest stable key is `linkedInId`, a third-party identifier, so
key your warehouse on `domain` where LinkedIn coverage is thin.

## Retrieving without spending credits — `getCompanies`

`GET /companies?startDate=…&endDate=…&page=…&limit=…`

Returns companies **already researched and stored in your org**. `startDate` and `endDate` are
**required**. This costs no credits and is the right call for a nightly warehouse sync or a bulk
export — do not re-run research to fetch data you already own.

Note the pagination style differs from search: this endpoint is offset-based (`page`/`limit`),
while search is cursor-based (`nextToken`).

## Runtime rules

- 60 requests/minute per endpoint per organization; read `X-RateLimit-Limit` rather than assuming.
- On 429 read `X-RateLimit-Reset` and wait — there is no `Retry-After`.
- Monitor `X-PublicAPI-Credits`; no endpoint returns a balance.
- On 422 branch on `code`: `insufficientCredits` vs `missingLicense`.
- No idempotency key. Retries create new jobs.

## Push instead of poll

Configure a `company-researched` webhook in Settings → Webhooks, validate the
`x-seamless-webhook-secret` header (a plain shared secret — no HMAC, so compare in constant time),
and match each delivery to its job via `apiResearchId`, which equals your `requestId`. Always
return `2xx` or the delivery is treated as failed.
