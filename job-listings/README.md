# LinkedIn Jobs Scraper API: job listings data from LinkedIn and Singapore MyCareersFuture

Pull public job listings as JSON: job title, company, location, posting date, salary where shown, seniority and the job URL.

Sources: public LinkedIn job search pages (no login, no cookies) and Singapore's official MyCareersFuture job portal.

Used for hiring-signal sales prospecting, labour-market research and job aggregation.

<!-- ngd-site-links -->
## On thenextgennexus.com

- [I’m a solo recruiter with no coding skills. How can I pull LinkedIn job listings into a spreadsheet?](https://thenextgennexus.com/linkedin-jobs-scraper/)
- [How can I pull open jobs from a company’s Greenhouse, Lever or Ashby careers page?](https://thenextgennexus.com/company-job-board-scraper/)
- [NexGenData’s LinkedIn Jobs Scraper vs other LinkedIn job scrapers on Apify: what’s the difference?](https://thenextgennexus.com/nexgendata-linkedin-jobs-scraper-vs-other-scrapers/)
- [LinkedIn’s official job API or a scraper: what are the options for pulling public LinkedIn job listings?](https://thenextgennexus.com/linkedin-jobs-recruiter-stack/)
- [All NexGenData guides by topic](https://thenextgennexus.com/tools/#every-page)
<!-- /ngd-site-links -->

## Which tool to use

| You want | Tool (Apify Store) | Returns |
|---|---|---|
| LinkedIn Jobs Scraper | [nexgendata/linkedin-jobs-scraper](https://apify.com/nexgendata/linkedin-jobs-scraper?fpr=2ayu9b) | `job_title`, `company_name`, `location`, `posted_date`, `job_url`, `job_id`, `salary`, `job_type` |
| Singapore MyCareersFuture Jobs | [nexgendata/singapore-mycareersfuture-jobs](https://apify.com/nexgendata/singapore-mycareersfuture-jobs?fpr=2ayu9b) | `job_id`, `title`, `company`, `company_uen`, `company_url`, `sector`, `location`, `is_overseas` |

Each tool runs on Apify and charges per record returned. Current prices are on each Store page.

## LinkedIn Jobs Scraper — No Login, by Keyword & Location

Scrape public LinkedIn job listings without login or cookies. Search by keyword, location, and job type; get title, company, salary, seniority, posting date, applicant count, and apply links. Read hiring-intent signals for sales or source roles for recruiting. No API key. Pay per record.

Store page: https://apify.com/nexgendata/linkedin-jobs-scraper?fpr=2ayu9b

**Output fields:** `job_title`, `company_name`, `location`, `posted_date`, `job_url`, `job_id`, `salary`, `job_type`, `description`, `seniority_level`, `employment_type`, `job_function`, `industries`, `applicants`

**Example record** (real output, run of 2026-10-31, some fields left out):

```json
{
  "job_title": "Automobilverkäufer",
  "company_name": "Autohaus Rüdiger GmbH",
  "location": "Dresden, Saxony, Germany",
  "posted_date": "2026-10-28",
  "job_url": "https://de.linkedin.com/jobs/view/automobilverk%C3%A4ufer-at-autohaus-r%C3%BCdiger-gmbh...",
  "job_id": "4482510245",
  "salary": null,
  "job_type": "Not specified"
}
```

**Run it from code** (replace YOUR_APIFY_TOKEN):

```bash
curl -X POST 'https://api.apify.com/v2/acts/nexgendata~linkedin-jobs-scraper/run-sync-get-dataset-items' \
  -H 'Authorization: Bearer YOUR_APIFY_TOKEN' -H 'Content-Type: application/json' \
  -d '{"keywords": "python developer", "maxResults": 50, "enrich_companies": false}'
```

## Singapore MyCareersFuture Jobs — Listings API

Search Singapore job listings on MyCareersFuture by keyword. Each listing gives title, company and UEN, sector, location, salary range (SGD), employment type, seniority, experience, posting and expiry dates, skills and job URL. No API key. Pay per record.

Store page: https://apify.com/nexgendata/singapore-mycareersfuture-jobs?fpr=2ayu9b

**Output fields:** `job_id`, `title`, `company`, `company_uen`, `company_url`, `sector`, `location`, `is_overseas`, `salary_min_sgd`, `salary_max_sgd`, `salary_type`, `employment_type`, `seniority`, `minimum_years_experience`, `posting_date`, `original_posting_date`, `expiry_date`, `vacancies`, `job_url`, `skills_required`, `ssoc_code`, `occupation_id`, `description_summary`, `data_source`

**Example record** (real output, run of 2026-10-31, some fields left out):

```json
{
  "job_id": "220bfa22de67f54e71f6b82ce6982a4b",
  "title": "🚀 (Entry-Level) Customer Service Events Coordinator 🚀",
  "company": "AURATALENTSG",
  "company_uen": "53530480C",
  "company_url": null,
  "location": "115 CLEMENTI STREET 13 SUNSET WAY RESIDENCE, Singapore 120115 (West)",
  "is_overseas": false,
  "salary_min_sgd": 3000
}
```

**Run it from code** (replace YOUR_APIFY_TOKEN):

```bash
curl -X POST 'https://api.apify.com/v2/acts/nexgendata~singapore-mycareersfuture-jobs/run-sync-get-dataset-items' \
  -H 'Authorization: Bearer YOUR_APIFY_TOKEN' -H 'Content-Type: application/json' \
  -d '{"searchQuery": "software engineer", "salaryMin": 0, "salaryMax": 0, "employmentType": "ALL", "postedWithinDays": 30, "maxResults": 50}'
```

---
Built by [NexGenData](https://apify.com/nexgendata?fpr=2ayu9b). Store links carry a NexGenData referral tag. Data comes from public and official sources; check each source's terms for your use.
