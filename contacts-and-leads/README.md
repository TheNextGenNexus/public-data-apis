# Website Contact Scraper and Email Finder API: B2B contact and tech stack data

Turn a list of company websites into JSON rows: the emails, phone numbers and social profiles each site publishes, plus the technologies it runs (CMS, analytics, ecommerce, hosting).

Source: the companies' own public websites (home, contact, about and team pages). Only details the company publishes itself.

Used for B2B lead lists, CRM enrichment and finding sites that run a given technology (a Wappalyzer / BuiltWith alternative).

<!-- ngd-site-links -->
## On thenextgennexus.com

- [What tool can extract emails and phone numbers from a list of websites?](https://thenextgennexus.com/extract-emails-phone-numbers-from-websites/)
- [How can I find the email addresses a company publishes on its website?](https://thenextgennexus.com/company-email-finder/)
- [How can I generate a lead list filtered by job title?](https://thenextgennexus.com/b2b-leads-finder/)
- [What tools can extract contacts and build B2B prospect lists?](https://thenextgennexus.com/lead-generation-data-tools/)
- [All NexGenData guides by topic](https://thenextgennexus.com/tools/#every-page)
<!-- /ngd-site-links -->

## Which tool to use

| You want | Tool (Apify Store) | Returns |
|---|---|---|
| Website Contact Details Extractor | [nexgendata/contact-info-scraper](https://apify.com/nexgendata/contact-info-scraper?fpr=2ayu9b) | `url`, `domain`, `type`, `value`, `email`, `http_status`, `status` |
| Company Email Finder | [nexgendata/company-email-finder](https://apify.com/nexgendata/company-email-finder?fpr=2ayu9b) | `email`, `emailType`, `source`, `domain`, `companyName`, `emailProvider`, `mxRecords`, `verified` |
| Lead Enrichment | [nexgendata/lead-list-enricher](https://apify.com/nexgendata/lead-list-enricher?fpr=2ayu9b) | `domain`, `url`, `status`, `company`, `emails`, `phones`, `socials`, `technologies` |
| Wappalyzer Alternative | [nexgendata/wappalyzer-replacement](https://apify.com/nexgendata/wappalyzer-replacement?fpr=2ayu9b) | `url`, `status_code`, `tech_count`, `categories`, `technologies`, `scan_time_ms`, `final_url`, `scan_status` |

Each tool runs on Apify and charges per record returned. Current prices are on each Store page.

## Website Contact Details Extractor — Contact Scraper

Website contact details extractor and website contact scraper: paste a list of website URLs to extract emails and phones from websites, plus social profiles — homepage and auto-discovered contact, about and team pages. One clean row per contact found. No API key. Pay per record.

Store page: https://apify.com/nexgendata/contact-info-scraper?fpr=2ayu9b

**Output fields:** `url`, `domain`, `type`, `value`, `email`, `http_status`, `status`

**Run it from code** (replace YOUR_APIFY_TOKEN):

```bash
curl -X POST 'https://api.apify.com/v2/acts/nexgendata~contact-info-scraper/run-sync-get-dataset-items' \
  -H 'Authorization: Bearer YOUR_APIFY_TOKEN' -H 'Content-Type: application/json' \
  -d '{"urls": ["https://www.shopify.com", "https://www.hubspot.com", "https://www.atlassian.com"], "crawl_contact_pages": true, "max_pages_per_site": 3, "request_timeout_secs": 20, "proxyConfiguration": {"useApifyProxy": true}}'
```

## Company Email Finder — B2B Contact Discovery API

Find the business emails a company publishes on its own website. Give it company domains, get one row per address — email, role or personal type, source page, email provider and an MX check that the domain accepts mail. Delivers to Notion via Apify MCP connectors. No API key. Pay per record.

Store page: https://apify.com/nexgendata/company-email-finder?fpr=2ayu9b

**Output fields:** `email`, `emailType`, `source`, `domain`, `companyName`, `emailProvider`, `mxRecords`, `verified`

**Run it from code** (replace YOUR_APIFY_TOKEN):

```bash
curl -X POST 'https://api.apify.com/v2/acts/nexgendata~company-email-finder/run-sync-get-dataset-items' \
  -H 'Authorization: Bearer YOUR_APIFY_TOKEN' -H 'Content-Type: application/json' \
  -d '{"domains": ["stripe.com"]}'
```

## Lead Enrichment — Enrich Leads with Emails, Phones & Tech

Lead enrichment from any company website: upload domains or company URLs to enrich leads with emails, phone numbers, social profiles and tech stack. Bulk domain enrichment for sales teams — a Clearbit & ZoomInfo alternative. No API key. Pay per record.

Store page: https://apify.com/nexgendata/lead-list-enricher?fpr=2ayu9b

**Output fields:** `domain`, `url`, `status`, `company`, `emails`, `phones`, `socials`, `technologies`, `server`, `contacts_count`, `enriched_at`

**Run it from code** (replace YOUR_APIFY_TOKEN):

```bash
curl -X POST 'https://api.apify.com/v2/acts/nexgendata~lead-list-enricher/run-sync-get-dataset-items' \
  -H 'Authorization: Bearer YOUR_APIFY_TOKEN' -H 'Content-Type: application/json' \
  -d '{"domains": ["apple.com", "stripe.com"], "maxContactsPerDomain": 5, "crawlContactPages": true}'
```

## Wappalyzer Alternative — Tech Stack Detector & BuiltWith API

Wappalyzer alternative and tech stack detector: point it at any website and get its technologies as clean JSON — CMS, analytics, ecommerce, JS frameworks, hosting, ad tech — grouped by category, with a tech-name list and count. BuiltWith API alternative. No API key. Pay per record.

Store page: https://apify.com/nexgendata/wappalyzer-replacement?fpr=2ayu9b

**Output fields:** `url`, `status_code`, `tech_count`, `categories`, `technologies`, `scan_time_ms`, `final_url`, `scan_status`, `tech_names`, `category_list`

**Run it from code** (replace YOUR_APIFY_TOKEN):

```bash
curl -X POST 'https://api.apify.com/v2/acts/nexgendata~wappalyzer-replacement/run-sync-get-dataset-items' \
  -H 'Authorization: Bearer YOUR_APIFY_TOKEN' -H 'Content-Type: application/json' \
  -d '{"urls": ["https://stripe.com", "https://shopify.com"], "include_confidence": true, "include_versions": true, "timeout_seconds": 15}'
```

---
Built by [NexGenData](https://apify.com/nexgendata?fpr=2ayu9b). Store links carry a NexGenData referral tag. Data comes from public and official sources; check each source's terms for your use.
