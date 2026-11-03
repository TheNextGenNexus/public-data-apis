# Startup Funding Data API: funding rounds, SEC Form D, VC portfolios and investment advisers

Get startup funding rounds, venture portfolio companies and SEC-registered investment advisers as JSON: company, amount, round, investors, sector, stage and firm assets under management.

Sources: SEC EDGAR Form D filings, TechCrunch and Y Combinator (funding rounds), SEC Form ADV (investment advisers), and the public portfolio pages of Sequoia Capital and 500 Global.

Used to build lead lists of newly funded companies, track investors, and research the advisers and funds behind them.

## Which tool to use

| You want | Tool (Apify Store) | Returns |
|---|---|---|
| Startup Funding Rounds Tracker | [nexgendata/startup-funding-tracker](https://apify.com/nexgendata/startup-funding-tracker?fpr=2ayu9b) | `source`, `recordType`, `companyName`, `fundingAmount`, `fundingCurrency`, `fundingAmountOriginal`, `valuation`, `roundType` |
| SEC Form ADV Tracker | [nexgendata/sec-form-adv-investment-adviser-tracker](https://apify.com/nexgendata/sec-form-adv-investment-adviser-tracker?fpr=2ayu9b) | `firm_name`, `legal_name`, `CRD_number`, `SEC_number`, `AUM`, `state`, `address`, `phone` |
| Sequoia Portfolio Scraper | [nexgendata/sequoia-portfolio-scraper](https://apify.com/nexgendata/sequoia-portfolio-scraper?fpr=2ayu9b) | `name`, `slug`, `url`, `description`, `sector`, `sectors`, `stage`, `founded_year` |
| 500 Global Companies Directory | [nexgendata/500-global-companies-directory](https://apify.com/nexgendata/500-global-companies-directory?fpr=2ayu9b) | `id`, `name`, `legal_name`, `slug`, `description`, `batch`, `batches`, `program` |

Each tool runs on Apify and charges per record returned. Current prices are on each Store page.

## Startup Funding Rounds Tracker — SEC Form D, TechCrunch & YC

Generate leads and build B2B prospect lists from newly funded startups — funding rounds from SEC EDGAR Form D filings, TechCrunch and Y Combinator in one call: company, amount, round, investors, date. Research funding & financials. Filter by amount, industry and date. No API key. Pay per record.

Store page: https://apify.com/nexgendata/startup-funding-tracker?fpr=2ayu9b

**Output fields:** `source`, `recordType`, `companyName`, `fundingAmount`, `fundingCurrency`, `fundingAmountOriginal`, `valuation`, `roundType`, `filingDate`, `investors`, `industry`, `location`, `companyUrl`, `sourceUrl`, `articleTitle`, `articleUrl`, `summary`

**Example record** (real output, run of 2026-11-02, some fields left out):

```json
{
  "source": "prnewswire",
  "recordType": "funding_round",
  "companyName": "Bizcap",
  "fundingAmount": 175000000,
  "fundingCurrency": "USD",
  "fundingAmountOriginal": 175000000,
  "valuation": null,
  "roundType": "Unknown"
}
```

**Run it from code** (replace YOUR_APIFY_TOKEN):

```bash
curl -X POST 'https://api.apify.com/v2/acts/nexgendata~startup-funding-tracker/run-sync-get-dataset-items' \
  -H 'Authorization: Bearer YOUR_APIFY_TOKEN' -H 'Content-Type: application/json' \
  -d '{"mode": "all_sources", "searchQuery": "", "minAmount": 0, "daysBack": 30, "maxResults": 25, "outputMode": "raw"}'
```

## SEC Form ADV Tracker — Investment Adviser (RIA) Data

Track Form ADV investment-adviser (RIA) records from SEC EDGAR — parsed, source-linked JSON for analysts, funds and AI agents. Official source. No API key. Pay per record.

Store page: https://apify.com/nexgendata/sec-form-adv-investment-adviser-tracker?fpr=2ayu9b

**Output fields:** `firm_name`, `legal_name`, `CRD_number`, `SEC_number`, `AUM`, `state`, `address`, `phone`, `fax`, `mailing_address`, `employee_count`, `fiduciary_advisor_count`, `organization_form`, `registration_type`, `registration_status`, `registration_date`, `last_filing_date`, `form_version`, `notice_filed_states`, `business_types`, `advisory_services`, `compensation_types`, `compensation_other`, `has_custody`, `has_custody_cash`, `has_custody_securities`, `custody_aum`, `custody_client_count`, `custodian`, `custodian_note`, `web_addresses`, `ADV_part_2_brochure_url`, `filing_url`, `sources`

**Example record** (real output, run of 2026-11-02, some fields left out):

```json
{
  "firm_name": "BONDBLOXX",
  "legal_name": "BONDBLOXX INVESTMENT MANAGEMENT CORPORATION",
  "CRD_number": "317318",
  "SEC_number": "801-122836",
  "AUM": 7239268024,
  "state": "CA",
  "employee_count": 32,
  "fiduciary_advisor_count": 5
}
```

**Run it from code** (replace YOUR_APIFY_TOKEN):

```bash
curl -X POST 'https://api.apify.com/v2/acts/nexgendata~sec-form-adv-investment-adviser-tracker/run-sync-get-dataset-items' \
  -H 'Authorization: Bearer YOUR_APIFY_TOKEN' -H 'Content-Type: application/json' \
  -d '{"state_filter": "CA", "min_aum": 100000000, "max_aum": 1000000000, "max_firms": 25}'
```

## Sequoia Portfolio Scraper — VC Companies, Sectors & Stage

Scrape every company in Sequoia Capital's public portfolio. Clean JSON — name, website, description, sector, stage, founding year, the Sequoia partner, founders, and status (active, acquired, IPO). No API key. Pay per record.

Store page: https://apify.com/nexgendata/sequoia-portfolio-scraper?fpr=2ayu9b

**Output fields:** `name`, `slug`, `url`, `description`, `sector`, `sectors`, `stage`, `founded_year`, `partnered_year`, `year_invested`, `acquired_year`, `ipo_year`, `status`, `partner`, `partners`, `founders`, `website`, `twitter_url`, `linkedin_url`, `geography`, `source_firm`, `source_sitemap_lastmod`, `scraped_at`

**Example record** (real output, run of 2026-10-29, some fields left out):

```json
{
  "name": "Cymphony",
  "slug": "cymphony",
  "url": "https://sequoiacap.com/companies/cymphony",
  "sector": "Security",
  "stage": null,
  "founded_year": 2024,
  "year_invested": 2024,
  "acquired_year": null
}
```

**Run it from code** (replace YOUR_APIFY_TOKEN):

```bash
curl -X POST 'https://api.apify.com/v2/acts/nexgendata~sequoia-portfolio-scraper/run-sync-get-dataset-items' \
  -H 'Authorization: Bearer YOUR_APIFY_TOKEN' -H 'Content-Type: application/json' \
  -d '{"geographyFilter": "Global", "yearFromTo": {"from": null, "to": null}, "maxResults": 25}'
```

## 500 Global Companies Directory — Startup API

Scrape the 500 Global (500 Startups) company directory — 2,200+ accelerator alumni. Each company gives name, description, batch, cohort year, industry, business model, stage, funding status, country, team size, founders, website and LinkedIn. For deal sourcing. No API key. Pay per record.

Store page: https://apify.com/nexgendata/500-global-companies-directory?fpr=2ayu9b

**Output fields:** `id`, `name`, `legal_name`, `slug`, `description`, `batch`, `batches`, `program`, `programs`, `cohort_year`, `first_investment_date`, `industry`, `industries`, `sector`, `business_model`, `stage`, `funding_status`, `country`, `region`, `location`, `team_size`, `founders`, `logo_url`, `website`, `linkedin_url`, `500global_url`, `data_source`

**Example record** (real output, run of 2026-10-31, some fields left out):

```json
{
  "id": 5732,
  "name": "Askria",
  "legal_name": "Askria Ltd.",
  "slug": "askria",
  "batch": null,
  "program": "sea",
  "cohort_year": 2023,
  "first_investment_date": "2023-06-06T00:00:00.000Z"
}
```

**Run it from code** (replace YOUR_APIFY_TOKEN):

```bash
curl -X POST 'https://api.apify.com/v2/acts/nexgendata~500-global-companies-directory/run-sync-get-dataset-items' \
  -H 'Authorization: Bearer YOUR_APIFY_TOKEN' -H 'Content-Type: application/json' \
  -d '{"limit": 10}'
```

---
Built by [NexGenData](https://apify.com/nexgendata?fpr=2ayu9b). Store links carry a NexGenData referral tag. Data comes from public and official sources; check each source's terms for your use.
