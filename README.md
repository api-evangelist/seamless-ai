# Seamless.AI (seamless-ai)

Seamless.AI is a B2B sales intelligence platform that provides real-time contact and company data to help sales teams find and connect with their ideal customers. The platform uses artificial intelligence to continuously verify and update contact information including emails, direct dials, and mobile numbers. Seamless.AI offers a RESTful API secured with OAuth 2.0 and API key authentication, enabling developers to integrate contact search, company search, enrichment, and job-change intelligence directly into CRM systems, marketing platforms, and internal sales tools.

**URL:** [Visit APIs.json URL](https://raw.githubusercontent.com/api-evangelist/seamless-ai/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Consumer
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
- **Modified:** 2026-05-02

## APIs

### Seamless.AI Contacts API

The Seamless.AI Contacts API provides programmatic access to contact search, enrichment, and research capabilities. Search for B2B contacts by name, company, title, and location. Enrich existing contact records with emails, phone numbers, and job history. Access job-change intelligence to identify contacts that have recently changed roles.

#### Properties

- [OpenAPI](openapi/seamless-ai-contacts-openapi.yml)
- [Documentation](https://docs.seamless.ai/)

### Seamless.AI Companies API

The Seamless.AI Companies API enables programmatic search and research of company data including firmographics, revenue, employee count, technology stack, and company intelligence. Use company search result IDs or direct identifiers such as domain or company name to retrieve comprehensive company profiles.

#### Properties

- [OpenAPI](openapi/seamless-ai-companies-openapi.yml)
- [Documentation](https://docs.seamless.ai/)

## Common Properties

- [Website](https://seamless.ai)
- [API Documentation](https://docs.seamless.ai/)
- [API Overview](https://seamless.ai/products/api)
- [Getting Started](https://seamless.ai/customers/education/articles/seamless-ai-api-overview)

## Artifacts

### JSON Schema

- [Contact Schema](json-schema/seamless-ai-contact-schema.json)
- [Company Schema](json-schema/seamless-ai-company-schema.json)

### JSON Structure

- [Contact Structure](json-structure/seamless-ai-contact-structure.json)

### JSON-LD

- [Context](json-ld/seamless-ai-context.jsonld)

### Examples

- [Search Contacts](examples/seamless-ai-search-contacts-example.json)

### Rules

- [Spectral Ruleset](rules/seamless-ai-rules.yml)

### Capabilities

- [Sales Prospecting](capabilities/sales-prospecting.yaml)
  - Shared: [Contacts](capabilities/shared/contacts.yaml)
  - Shared: [Companies](capabilities/shared/companies.yaml)

### Vocabulary

- [Seamless.AI Vocabulary](vocabulary/seamless-ai-vocabulary.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
