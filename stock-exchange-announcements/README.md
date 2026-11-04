# Stock Exchange Announcements API: ASX, NSE India, SEBI filings and UK RNS

Collect listed-company announcements and regulatory filings as JSON: ticker, company, date and time, headline, announcement type and a link to the filing or PDF.

Sources: the Australian Securities Exchange (ASX), India's National Stock Exchange (NSE), SEBI filings (DRHP, RHP, takeovers, buybacks) and UK Regulatory News Service announcements via Investegate (LSE and AIM).

Used by analysts, funds and compliance teams following disclosures outside the US.

<!-- ngd-site-links -->
## On thenextgennexus.com

- [I’m a small fund without a data vendor. How can I get ASX company announcements into a spreadsheet?](https://thenextgennexus.com/asx-company-announcements-to-spreadsheet/)
- [How do I get NSE India corporate announcements with the PDF links automatically?](https://thenextgennexus.com/nse-india-announcements-pdf-links/)
- [How can I track India SEBI filings like DRHPs and takeover disclosures automatically?](https://thenextgennexus.com/india-sebi-filings/)
- [All NexGenData guides by topic](https://thenextgennexus.com/tools/#every-page)
<!-- /ngd-site-links -->

## Which tool to use

| You want | Tool (Apify Store) | Returns |
|---|---|---|
| ASX Announcements Scraper | [nexgendata/asx-company-announcements](https://apify.com/nexgendata/asx-company-announcements?fpr=2ayu9b) | `announcement_id`, `ticker`, `company_name`, `announcement_date`, `announcement_time`, `announcement_types`, `headline`, `is_market_sensitive` |
| NSE India Company Announcements Scraper | [nexgendata/nse-bse-announcements](https://apify.com/nexgendata/nse-bse-announcements?fpr=2ayu9b) | `announcement_id`, `symbol`, `company_name`, `isin`, `industry`, `announcement_date`, `announcement_time`, `subject` |
| India SEBI Filings Tracker | [nexgendata/india-sebi-filings-tracker](https://apify.com/nexgendata/india-sebi-filings-tracker?fpr=2ayu9b) | `filing_id`, `company_name`, `filing_type`, `filing_date`, `sebi_url`, `pdf_url`, `summary`, `party_role` |
| Investegate RNS Scraper | [nexgendata/investegate-rns-aggregator](https://apify.com/nexgendata/investegate-rns-aggregator?fpr=2ayu9b) | `rns_id`, `company_name`, `ticker`, `isin`, `exchange`, `announcement_date`, `announcement_time`, `title` |

Each tool runs on Apify and charges per record returned. Current prices are on each Store page.

## ASX Announcements Scraper — Australian Company Disclosures

Collect ASX company announcements and filings as clean JSON — track Australian Securities Exchange disclosures by ticker, company or date: headline, announcement type, market/price-sensitive flags, date/time, ticker, company and a link to the source PDF. Official source. No API key. Pay per record.

Store page: https://apify.com/nexgendata/asx-company-announcements?fpr=2ayu9b

**Output fields:** `announcement_id`, `ticker`, `company_name`, `announcement_date`, `announcement_time`, `announcement_types`, `headline`, `is_market_sensitive`, `is_price_sensitive`, `num_pages`, `file_size_kb`, `file_url`, `source_url`, `scraped_at`

**Example record** (real output, run of 2026-11-02, some fields left out):

```json
{
  "announcement_id": "03157237",
  "ticker": "HRN",
  "company_name": "HORIZON GOLD LIMITED",
  "announcement_date": "2026-11-02",
  "announcement_time": "17:58 AEST",
  "headline": "NOTICE UNDER SECTION 708A",
  "is_market_sensitive": false,
  "is_price_sensitive": false
}
```

**Run it from code** (replace YOUR_APIFY_TOKEN):

```bash
curl -X POST 'https://api.apify.com/v2/acts/nexgendata~asx-company-announcements/run-sync-get-dataset-items' \
  -H 'Authorization: Bearer YOUR_APIFY_TOKEN' -H 'Content-Type: application/json' \
  -d '{"marketSensitiveOnly": false, "maxResults": 50}'
```

## NSE India Company Announcements Scraper

Live corporate announcements & regulatory filings from India's NSE (National Stock Exchange) — dividends, results, board meetings, allotments — with PDF attachment URLs. Watch mode for new-filing alerts.

Store page: https://apify.com/nexgendata/nse-bse-announcements?fpr=2ayu9b

**Output fields:** `announcement_id`, `symbol`, `company_name`, `isin`, `industry`, `announcement_date`, `announcement_time`, `subject`, `headline`, `has_xbrl`, `attachment_size`, `attachment_url`, `source_url`, `exchange`, `scraped_at`

**Example record** (real output, run of 2026-10-31, some fields left out):

```json
{
  "announcement_id": "106838338",
  "symbol": "RELIANCE",
  "company_name": "Reliance Industries Limited",
  "isin": "INE002A01018",
  "industry": "Refineries",
  "announcement_date": "2026-10-31",
  "announcement_time": "17:34 IST",
  "subject": "Analysts/Institutional Investor Meet/Con. Call Updates"
}
```

**Run it from code** (replace YOUR_APIFY_TOKEN):

```bash
curl -X POST 'https://api.apify.com/v2/acts/nexgendata~nse-bse-announcements/run-sync-get-dataset-items' \
  -H 'Authorization: Bearer YOUR_APIFY_TOKEN' -H 'Content-Type: application/json' \
  -d '{"symbols": ["RELIANCE", "TCS"], "maxResults": 25}'
```

## India SEBI Filings Tracker — Disclosure API

Monitor India SEBI filings and disclosures — DRHP, RHP, SAST takeover, buyback, rights, debt, REIT/InvIT. Each filing gives company, type, date, SEBI page, PDF link, summary, party role and sector. Filter by company, date or type. No API key. Pay per record.

Store page: https://apify.com/nexgendata/india-sebi-filings-tracker?fpr=2ayu9b

**Output fields:** `filing_id`, `company_name`, `filing_type`, `filing_date`, `sebi_url`, `pdf_url`, `summary`, `party_role`, `sector`, `category`, `category_label`, `title_raw`, `source`, `country`, `regulator`, `scraped_at`

**Example record** (real output, run of 2026-11-02, some fields left out):

```json
{
  "filing_id": "105485",
  "company_name": "Carlsberg India Limited",
  "filing_type": "UDRHP",
  "filing_date": "2026-10-29",
  "sebi_url": "https://www.sebi.gov.in/filings/public-issues/oct-2026/carlsberg-india-limited-udrhp-1_...",
  "pdf_url": "https://www.sebi.gov.in/sebi_data/commondocs/oct-2026/Carlsberg%20India%20Limited_DA_p.pdf",
  "party_role": "issuer",
  "sector": null
}
```

**Run it from code** (replace YOUR_APIFY_TOKEN):

```bash
curl -X POST 'https://api.apify.com/v2/acts/nexgendata~india-sebi-filings-tracker/run-sync-get-dataset-items' \
  -H 'Authorization: Bearer YOUR_APIFY_TOKEN' -H 'Content-Type: application/json' \
  -d '{"filing_types": ["DRHP", "RHP", "TAKEOVER"], "days_back": 90, "max_filings": 50, "proxyConfiguration": {"useApifyProxy": true}}'
```

## Investegate RNS Scraper — UK Regulatory News (LSE/AIM)

Aggregate UK regulatory news (RNS) from Investegate for LSE- and AIM-listed companies. Clean JSON — company, ticker, ISIN, exchange, date/time, headline, RNS category, summary, and source link. No API key. Pay per record.

Store page: https://apify.com/nexgendata/investegate-rns-aggregator?fpr=2ayu9b

**Output fields:** `rns_id`, `company_name`, `ticker`, `isin`, `exchange`, `announcement_date`, `announcement_time`, `title`, `rns_category`, `summary`, `source_code`, `source_url`, `scraped_at`

**Example record** (real output, run of 2026-10-31, some fields left out):

```json
{
  "rns_id": "9851557",
  "company_name": "Roebuck Food Group Public Limited Company (CDI)",
  "ticker": "RFG",
  "isin": null,
  "exchange": null,
  "announcement_date": "2026-10-30",
  "announcement_time": "18:28",
  "title": "Proposed Placing and Subscription"
}
```

**Run it from code** (replace YOUR_APIFY_TOKEN):

```bash
curl -X POST 'https://api.apify.com/v2/acts/nexgendata~investegate-rns-aggregator/run-sync-get-dataset-items' \
  -H 'Authorization: Bearer YOUR_APIFY_TOKEN' -H 'Content-Type: application/json' \
  -d '{"maxResults": 25}'
```

---
Built by [NexGenData](https://apify.com/nexgendata?fpr=2ayu9b). Store links carry a NexGenData referral tag. Data comes from public and official sources; check each source's terms for your use.
