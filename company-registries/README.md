# Company Registry Search API: Delaware, France and Australia company data

Look up official company registry records as JSON: entity name, registry number, legal form, status and incorporation date.

Sources are the government registries themselves: the Delaware Division of Corporations, the French SIRENE/RNE open data (DINUM/INSEE) and the Australian ASIC register.

Used for KYC and AML checks, supplier and customer due diligence, VC sourcing and M&A research.

<!-- ngd-site-links -->
## On thenextgennexus.com

- [I need to check whether a Delaware company exists and when it was incorporated. How can I look that up in bulk?](https://thenextgennexus.com/delaware-company-lookup-in-bulk/)
- [Delaware’s own entity search or a third-party API: which is better for checking many Delaware companies at once?](https://thenextgennexus.com/delaware-entity-search-vs-api/)
- [What are the best company registry APIs in 2026?](https://thenextgennexus.com/best-company-registry-apis/)
- [How can I look up Singapore companies by name or UEN from ACRA?](https://thenextgennexus.com/singapore-acra-company-search/)
- [All NexGenData guides by topic](https://thenextgennexus.com/tools/#every-page)
<!-- /ngd-site-links -->

## Which tool to use

| You want | Tool (Apify Store) | Returns |
|---|---|---|
| Delaware Corporations Search | [nexgendata/delaware-corporations-search-scraper](https://apify.com/nexgendata/delaware-corporations-search-scraper?fpr=2ayu9b) | `file_number`, `entity_name`, `state_of_formation`, `source`, `incorporation_date`, `incorporation_date_iso`, `entity_kind`, `entity_type` |
| France Companies Search | [nexgendata/france-pappers-companies](https://apify.com/nexgendata/france-pappers-companies?fpr=2ayu9b) | `name`, `siren`, `siret_siege`, `legal_form_code`, `legal_form`, `naf_code`, `activity_section`, `creation_date` |
| Australia ASIC Company Search | [nexgendata/australia-asic-company-search](https://apify.com/nexgendata/australia-asic-company-search?fpr=2ayu9b) | `name`, `acn`, `abn`, `status`, `registration_date`, `company_type`, `registered_address`, `jurisdiction` |

Each tool runs on Apify and charges per record returned. Current prices are on each Store page.

## Delaware Corporations Search — DE Entity Data API

Search the Delaware Division of Corporations entity registry. Partial-match name search returns matching DE entities — file_number + entity_name. KYC, AML, VC sourcing, M&A.

Store page: https://apify.com/nexgendata/delaware-corporations-search-scraper?fpr=2ayu9b

**Output fields:** `search_query`, `search_type`, `match_mode`, `requested_name`, `requested_name_normalized`, `file_number`, `entity_name`, `state_of_formation`, `source`, `incorporation_date`, `incorporation_date_iso`, `entity_kind`, `entity_type`, `residency`, `registered_agent_name`, `registered_agent_address`, `registered_agent_city`, `registered_agent_county`, `registered_agent_state`, `registered_agent_postal_code`, `registered_agent_phone`, `detail_status`

**Example record** (real output, run of 2026-11-02, some fields left out):

```json
{
  "search_type": "entity_name",
  "file_number": "4675506",
  "entity_name": "STRIPE, LLC",
  "state_of_formation": "DE",
  "source": "icis.corp.delaware.gov",
  "incorporation_date": "4/13/2009",
  "incorporation_date_iso": "2009-04-13",
  "entity_kind": "Limited Liability Company"
}
```

**Run it from code** (replace YOUR_APIFY_TOKEN):

```bash
curl -X POST 'https://api.apify.com/v2/acts/nexgendata~delaware-corporations-search-scraper/run-sync-get-dataset-items' \
  -H 'Authorization: Bearer YOUR_APIFY_TOKEN' -H 'Content-Type: application/json' \
  -d '{"entityNames": ["Stripe"], "maxEntities": 5}'
```

## France Companies Search — SIRENE & RNE (open data, no API key)

Search French companies in the French government's API Recherche d'entreprises (SIRENE and RNE open data, published by DINUM / INSEE). SIREN, SIRET, NAF code, SARL/SAS/SA/EURL/SCI, incorporation date, registered office, directors. Source data is free and needs no API key. KYC, M&A, lead-gen.

Store page: https://apify.com/nexgendata/france-pappers-companies?fpr=2ayu9b

**Output fields:** `name`, `siren`, `siret_siege`, `legal_form_code`, `legal_form`, `naf_code`, `activity_section`, `creation_date`, `company_category`, `employee_band_code`, `employee_band`, `status`, `is_employer`, `headquarters_address`, `street`, `postal_code`, `city`, `department_code`, `establishments_total`, `establishments_open`, `directors`, `last_financials_year`, `date_updated`, `data_source`, `source_url`

**Example record** (real output, run of 2026-11-03, some fields left out):

```json
{
  "name": "CARREFOUR",
  "siren": "652014051",
  "siret_siege": "65201405100732",
  "legal_form_code": "5599",
  "legal_form": "SA",
  "naf_code": "64.20Z",
  "activity_section": "K",
  "creation_date": "1963-01-01"
}
```

**Run it from code** (replace YOUR_APIFY_TOKEN):

```bash
curl -X POST 'https://api.apify.com/v2/acts/nexgendata~france-pappers-companies/run-sync-get-dataset-items' \
  -H 'Authorization: Bearer YOUR_APIFY_TOKEN' -H 'Content-Type: application/json' \
  -d '{"searchQuery": "Carrefour", "includeDormant": false, "maxResults": 10}'
```

## Australia ASIC Company Search — Registry API

Search the Australian ASIC company registry by name, ACN or ABN. Each record gives name, ACN, ABN, status, registration date, company type, registered address, officers, GST status and business names. For KYC and due diligence. No API key. Pay per record.

Store page: https://apify.com/nexgendata/australia-asic-company-search?fpr=2ayu9b

**Output fields:** `name`, `acn`, `abn`, `status`, `registration_date`, `company_type`, `registered_address`, `jurisdiction`, `officers`, `officers_source`, `gst_registered`, `gst_effective_from`, `entity_type`, `last_review_date`, `business_names`, `trading_names`, `asic_status`, `deregistration_date`, `asic_company_type`, `asic_class`, `asic_sub_class`, `former_names`, `abn_status`, `abn_status_date`, `data_source`, `_source_url`

**Example record** (real output, run of 2026-10-31, some fields left out):

```json
{
  "name": "MONAKA PTY LTD",
  "acn": "000000019",
  "abn": "89000000019",
  "status": "registered",
  "registration_date": "1990-01-08",
  "company_type": "Pty Ltd",
  "jurisdiction": "NSW",
  "gst_registered": true
}
```

**Run it from code** (replace YOUR_APIFY_TOKEN):

```bash
curl -X POST 'https://api.apify.com/v2/acts/nexgendata~australia-asic-company-search/run-sync-get-dataset-items' \
  -H 'Authorization: Bearer YOUR_APIFY_TOKEN' -H 'Content-Type: application/json' \
  -d '{"companyName": "Atlassian", "status": "any", "includeOfficers": true, "maxResults": 10}'
```

---
Built by [NexGenData](https://apify.com/nexgendata?fpr=2ayu9b). Store links carry a NexGenData referral tag. Data comes from public and official sources; check each source's terms for your use.
