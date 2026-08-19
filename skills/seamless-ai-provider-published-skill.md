---
name: Seamless
description: Use when building integrations to search and enrich company and contact data via REST API or MCP tools, automating B2B research workflows, syncing enriched records to CRMs, or building AI agent workflows for sales automation and prospecting.
metadata:
    mintlify-proj: seamless
    version: "1.0"
---

# Seamless.AI Skill

## Product summary

Seamless.AI is a B2B data API that lets you search for companies and contacts, submit them for enrichment, and retrieve completed results via webhooks or polling. You authenticate with an API key (`Token` header) or OAuth (`Authorization: Bearer`), then follow a fixed three-step flow: search → research → retrieve. The platform also offers an MCP server with 54 tools for AI agents in Cursor, Claude, VS Code, and other IDEs. Primary docs: https://docs.seamless.ai

**Key endpoints:**
- `POST /search/companies` and `POST /search/contacts` — find targets
- `POST /companies/research` and `POST /contacts/research` — start enrichment
- `GET /companies/research/poll` and `GET /contacts/research/poll` — check status
- `GET /companies` and `GET /contacts` — retrieve org records without new research

**CLI/config:** API keys created at `Settings → Public API → API Key` in the Seamless app. MCP server URL: `https://mcp.seamless.ai/mcp`

## When to use

Reach for this skill when:
- Building a REST API integration to search and enrich company or contact records
- Automating research workflows with polling or webhooks
- Syncing enriched data to a CRM or data warehouse
- Building an AI agent workflow that needs to find and enrich B2B targets
- Connecting Seamless to Cursor, Claude, ChatGPT, or other MCP clients for agent-driven research
- Retrieving records already researched and stored in your org without starting new research
- Troubleshooting authentication, identifier sequencing, or result delivery issues

## Quick reference

### Authentication

| Method | Header | Setup |
| --- | --- | --- |
| API key | `Token: YOUR_API_KEY` | Create at Settings → Public API → API Key |
| OAuth | `Authorization: Bearer ACCESS_TOKEN` | Complete OAuth flow; see `/authentication/oauth` |

### Request flow

```
Search → Research → Polling/Webhooks
  ↓         ↓
searchResultId → requestId
```

| Step | Endpoint | Input | Output | Save |
| --- | --- | --- | --- | --- |
| Search | `POST /search/companies` or `/search/contacts` | Filters (name, domain, title, etc.) | List of matches | `searchResultId` |
| Research | `POST /companies/research` or `/contacts/research` | `searchResultIds` array | Queued for enrichment | `requestId` |
| Poll | `GET /companies/research/poll` or `/contacts/research/poll` | `requestIds` query param | Status + full record when done | — |
| Webhooks | Configure at Settings → Webhooks | Event type: `company-researched` or `contact-researched` | `POST` to your endpoint | — |

### Poll status values

| Status | Meaning | Action |
| --- | --- | --- |
| `researching` | Still processing | Poll again in 2–5 seconds |
| `done` | Complete | Extract enriched record |
| `missing` | No result found | Record not in database |
| `error` | Processing failed | Check credits and license |
| `duplicate` | Already researched | Existing result returned (contacts only) |

### Rate limits & credits

- **Rate limit:** 60 requests per minute per endpoint (org-wide)
- **Research credits:** Consumed by research endpoints only; search and org-data reads are free
- **Response headers:** `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `X-RateLimit-Reset`, `X-PublicAPI-Credits`
- **429 handling:** Read `X-RateLimit-Reset` and wait until that epoch timestamp before retrying

### MCP tools (54 total)

| Domain | Tools | Use for |
| --- | --- | --- |
| Search | `search_companies`, `search_contacts` | Find targets by filters |
| Research | `research_companies`, `research_contacts` | Start enrichment |
| User | `get_user_profile`, `get_credits` | Account info |
| Lists | `create_list`, `add_to_list`, `get_lists` | Organize contacts |
| Campaigns | `create_campaign`, `get_campaigns` | Manage outreach |
| Email | `send_email`, `get_email_templates` | Send messages |
| Calls | `log_call`, `get_calls` | Track calls |
| Tasks | `create_task`, `get_tasks` | Manage tasks |
| Activity | `get_activity` | View account activity |

## Decision guidance

### When to use search vs. research-without-search

| Scenario | Use search | Use research-without-search |
| --- | --- | --- |
| Need to find targets by filters (job title, industry, location) | ✓ | — |
| Already have company domain or name from CRM | — | ✓ |
| Already have contact name + company from spreadsheet | — | ✓ |
| Want to discover multiple matching records | ✓ | — |
| Want to enrich a single known record quickly | — | ✓ |

### When to use webhooks vs. polling

| Factor | Webhooks | Polling |
| --- | --- | --- |
| Infrastructure required | Public HTTPS endpoint | None (outbound HTTP only) |
| Latency | Near-instant on completion | Depends on poll interval |
| Best for | Event-driven, real-time pipelines | Scripts, notebooks, simple integrations |
| Setup complexity | Moderate (endpoint + secret validation) | Minimal |
| **Recommendation** | Use for production systems | Start here for prototypes |

### When to use org-data endpoints vs. research

| Scenario | Use org-data GET | Use research |
| --- | --- | --- |
| Retrieve records already researched and stored | ✓ | — |
| Bulk export of enriched data | ✓ | — |
| Need new enrichment | — | ✓ |
| Want to avoid credit consumption | ✓ | — |

## Workflow

### Standard search → research → poll workflow

1. **Authenticate** — Store API key in `SEAMLESS_API_KEY` env var or complete OAuth flow.
2. **Search** — Call `POST /search/companies` or `/search/contacts` with filters. Save `searchResultId` from the matching record.
3. **Research** — Call `POST /companies/research` or `/contacts/research` with the `searchResultId`. Save `requestId` from the response.
4. **Poll** — Call `GET /companies/research/poll` or `/contacts/research/poll` with `requestId` every 2–5 seconds until `status` is `done`.
5. **Extract** — Parse the enriched record from the poll response and use it downstream.

### Research-without-search workflow (when you have identifiers)

1. **Authenticate** — Store API key or OAuth token.
2. **Research directly** — Call `POST /companies/research` with `companies` array (domain + name) or `POST /contacts/research` with `contacts` array (name + company + optional title).
3. **Poll or webhook** — Same as standard workflow: poll until `done` or wait for webhook delivery.

### Webhook-based workflow

1. **Configure webhook** — Go to Settings → Webhooks, create endpoint, select event type (`company-researched` or `contact-researched`), set shared secret.
2. **Search and research** — Call search and research endpoints as normal; save `requestId`.
3. **Receive event** — When research completes, Seamless sends `POST` to your endpoint with enriched record.
4. **Validate secret** — Read `x-seamless-webhook-secret` header and compare to configured secret.
5. **Process and respond** — Parse JSON body, run application logic, return `2xx` status.

### Agent workflow (MCP)

1. **Install MCP** — Add server URL `https://mcp.seamless.ai/mcp` to your IDE config (Cursor, Claude Desktop, VS Code, etc.).
2. **Authorize** — On first connect, complete OAuth login in browser.
3. **Use tools** — Ask agent to search, research, or manage campaigns; tools are discovered automatically.
4. **Persist state** — Agent maintains `searchResultId` and `requestId` across tool calls.

## Common gotchas

- **Mixing up identifiers** — `searchResultId` comes from search; `requestId` comes from research. Do not pass `searchResultId` to polling or vice versa. Store both separately until workflow completes.
- **Polling too fast** — Tight loops (< 1 second) waste rate limit quota. Use 2–5 second intervals.
- **Forgetting to save identifiers** — If you lose `searchResultId` or `requestId`, you must restart from search. Store them immediately after each response.
- **Not handling 429** — When rate-limited, read `X-RateLimit-Reset` and wait until that epoch timestamp. Retrying immediately will fail.
- **Insufficient credits** — Research endpoints consume credits. Check `X-PublicAPI-Credits` header or Settings → Billing. HTTP 422 with `code: insufficientCredits` means you need more credits.
- **Missing license** — HTTP 422 with `code: missingLicense` means your account lacks Public API access. Contact your admin.
- **Webhook endpoint not public** — Localhost and private IPs cannot receive webhook deliveries. Deploy to a public HTTPS URL.
- **Webhook secret mismatch** — Validate `x-seamless-webhook-secret` header exactly (case-sensitive). Mismatches cause 401 responses.
- **Not returning 2xx from webhook** — Seamless treats non-2xx responses as delivery failures and may retry. Always return `200` or `202` after processing.
- **Calling research without search first** — You can skip search and call research directly with identifiers (domain, name, title), but you must have valid identifiers. Do not guess.
- **Duplicate research** — If poll status is `duplicate`, the record was already researched. Do not resubmit; use the existing result.
- **Hardcoding credentials** — Never commit API keys or access tokens to source control. Use environment variables or secrets managers.

## Verification checklist

Before submitting work:

- [ ] Authentication header is correct (`Token` or `Authorization: Bearer`)
- [ ] API key or OAuth token is stored in environment variables, not hardcoded
- [ ] `searchResultId` is saved immediately after search response
- [ ] `requestId` is saved immediately after research response
- [ ] Polling interval is 2–5 seconds (not tight loop)
- [ ] Poll loop continues until `status` is terminal (`done`, `error`, `missing`, or `duplicate`)
- [ ] If using webhooks, endpoint is publicly reachable over HTTPS
- [ ] If using webhooks, `x-seamless-webhook-secret` header is validated
- [ ] If using webhooks, endpoint returns `2xx` status after processing
- [ ] Rate limit headers (`X-RateLimit-Remaining`, `X-RateLimit-Reset`) are checked
- [ ] Credit balance (`X-PublicAPI-Credits`) is monitored before bulk research
- [ ] HTTP 422 errors are checked for `code` field (`insufficientCredits` vs. `missingLicense`)
- [ ] Error poll status (`error`, `missing`) is surfaced to caller, not retried automatically
- [ ] Org-data endpoints (`GET /companies`, `GET /contacts`) are used for bulk retrieval of existing records, not new research

## Resources

- **Comprehensive page listing:** https://docs.seamless.ai/llms.txt
- **First request walkthrough:** https://docs.seamless.ai/authenticate-and-make-your-first-request
- **Choose a workflow:** https://docs.seamless.ai/choose-the-right-workflow
- **Build a deterministic agent workflow:** https://docs.seamless.ai/build-a-deterministic-agent-workflow

---

> For additional documentation and navigation, see: https://docs.seamless.ai/llms.txt