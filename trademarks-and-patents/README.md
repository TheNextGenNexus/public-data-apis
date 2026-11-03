# Trademark Search API: USPTO, EUIPO and US patent search data

Search trademarks and patents as JSON: mark, owner or applicant, status, filing and registration dates, Nice classes, and for patents the title, abstract, assignee, CPC classes and citations.

Sources: the USPTO TSDR record and IP Australia (trademarks), the EUIPO register (EU trade marks), and the Google Patents index for US patents (not an official USPTO API).

Used for brand clearance, trademark watching, prior-art searches and competitor IP research.

## Which tool to use

| You want | Tool (Apify Store) | Returns |
|---|---|---|
| Trademark Search | [nexgendata/uspto-trademark-search](https://apify.com/nexgendata/uspto-trademark-search?fpr=2ayu9b) | `serial_number`, `registration_number`, `mark`, `owner`, `status`, `filing_date`, `registration_date`, `class` |
| EUIPO Trademark Search | [nexgendata/euipo-esearch-trademarks](https://apify.com/nexgendata/euipo-esearch-trademarks?fpr=2ayu9b) | `application_number`, `office`, `mark_name`, `mark_type`, `applicant_name`, `applicant_country`, `application_date`, `registration_date` |
| USPTO Patent Search | [nexgendata/uspto-patent-search](https://apify.com/nexgendata/uspto-patent-search?fpr=2ayu9b) | `publication_number`, `title`, `abstract`, `abstract_snippet`, `claims_text`, `claims_count`, `cpc_classifications`, `cited_patents` |

Each tool runs on Apify and charges per record returned. Current prices are on each Store page.

## Trademark Search — USPTO Serial + IP Australia Name Search

Trademark due diligence and brand clearance: look up US trademarks by serial/registration number from the official USPTO TSDR source, and search brand names across the IP Australia register. JSON: mark, owner, status, serial/registration, dates, class, goods/services. No API key. Pay per record.

Store page: https://apify.com/nexgendata/uspto-trademark-search?fpr=2ayu9b

**Output fields:** `serial_number`, `registration_number`, `mark`, `owner`, `status`, `filing_date`, `registration_date`, `class`, `goods_services`, `office`, `trademark_type`, `st13`, `detail_url`, `image_url`, `search_query`, `source`, `match_mode`, `requested_query`, `matched_query`, `status_raw`, `similarity_score`, `clearance_risk`

**Example record** (real output, run of 2026-11-02, some fields left out):

```json
{
  "serial_number": "76533541",
  "registration_number": "",
  "mark": "ACME",
  "status": "Expired",
  "filing_date": "2003-07-30",
  "registration_date": "",
  "goods_services": "034: Tobacco requisites namely, cigarettes, cigars, pipe tobacco, chewing tobacco, snuf...",
  "office": "US"
}
```

**Run it from code** (replace YOUR_APIFY_TOKEN):

```bash
curl -X POST 'https://api.apify.com/v2/acts/nexgendata~uspto-trademark-search/run-sync-get-dataset-items' \
  -H 'Authorization: Bearer YOUR_APIFY_TOKEN' -H 'Content-Type: application/json' \
  -d '{"query": "nike", "searchType": "name", "territories": ["US"], "maxResults": 20}'
```

## EUIPO Trademark Search — EU Trade Mark Lookup & Clearance

EU trademark due diligence and clearance: search the EUIPO register by brand name, applicant or Nice class. JSON — mark, type, application/registration number, status, applicant, filing/registration dates, Nice classes, plus a similarity score and clearance risk. Official source. Pay per record.

Store page: https://apify.com/nexgendata/euipo-esearch-trademarks?fpr=2ayu9b

**Output fields:** `application_number`, `office`, `mark_name`, `mark_type`, `applicant_name`, `applicant_country`, `application_date`, `registration_date`, `status`, `nice_classes`, `image_url`, `source_url`, `scraped_at`, `st13`, `similarity_score`, `clearance_risk`

**Example record** (real output, run of 2026-11-02, some fields left out):

```json
{
  "application_number": "001859693",
  "office": "EM",
  "mark_name": "ACME",
  "mark_type": "Figurative",
  "applicant_country": null,
  "application_date": "2000-09-05",
  "registration_date": "2001-11-13",
  "status": "Registered"
}
```

**Run it from code** (replace YOUR_APIFY_TOKEN):

```bash
curl -X POST 'https://api.apify.com/v2/acts/nexgendata~euipo-esearch-trademarks/run-sync-get-dataset-items' \
  -H 'Authorization: Bearer YOUR_APIFY_TOKEN' -H 'Content-Type: application/json' \
  -d '{"query": "Apple", "offices": ["EM"], "maxResults": 25}'
```

## USPTO Patent Search — US Prior Art via Google Patents Index

Patent research for due diligence and competitor research: search US patents (USPTO grants and published applications) for prior art by keyword, assignee or inventor, via the Google Patents index. Not an official USPTO API. Clean JSON with claims, CPC classes and citations.

Store page: https://apify.com/nexgendata/uspto-patent-search?fpr=2ayu9b

**Output fields:** `publication_number`, `title`, `abstract`, `abstract_snippet`, `claims_text`, `claims_count`, `cpc_classifications`, `cited_patents`, `cited_patents_count`, `cited_by_count`, `family_size`, `assignee`, `inventor`, `priority_date`, `filing_date`, `grant_date`, `publication_date`, `language`, `pdf_url`, `google_patents_url`, `source`, `detected_at`

**Example record** (real output, run of 2026-11-02, some fields left out):

```json
{
  "publication_number": "US9941496B2",
  "title": "On-board power source device",
  "cpc_classifications": null,
  "cited_patents": null,
  "cited_patents_count": null,
  "cited_by_count": null,
  "family_size": null,
  "priority_date": "2014-10-01"
}
```

**Run it from code** (replace YOUR_APIFY_TOKEN):

```bash
curl -X POST 'https://api.apify.com/v2/acts/nexgendata~uspto-patent-search/run-sync-get-dataset-items' \
  -H 'Authorization: Bearer YOUR_APIFY_TOKEN' -H 'Content-Type: application/json' \
  -d '{"query": "artificial intelligence", "maxResults": 20}'
```

---
Built by [NexGenData](https://apify.com/nexgendata?fpr=2ayu9b). Store links carry a NexGenData referral tag. Data comes from public and official sources; check each source's terms for your use.
