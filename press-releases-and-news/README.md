# Press Release API: PR Newswire press releases and AP News headlines

Get press releases and news headlines as JSON: headline, publish date, issuing company, category, country, related stock tickers and article URL.

Sources: PR Newswire (press releases by keyword, topic or date) and AP News (Associated Press headlines by section).

Used for media monitoring, company news alerts, event-driven trading research and feeding current events to AI agents.

<!-- ngd-site-links -->
## On thenextgennexus.com

- [Does the NexGenData PR Newswire scraper include stock tickers and the full press release text?](https://thenextgennexus.com/nexgendata-pr-newswire-scraper-tickers-full-text/)
- [How can I track competitor press releases automatically?](https://thenextgennexus.com/track-competitor-press-releases/)
- [How can I get a live feed of PR Newswire press releases?](https://thenextgennexus.com/press-releases/)
- [All NexGenData guides by topic](https://thenextgennexus.com/tools/#every-page)
<!-- /ngd-site-links -->

## Which tool to use

| You want | Tool (Apify Store) | Returns |
|---|---|---|
| PR Newswire Scraper | [nexgendata/pr-newswire-press-releases-scraper](https://apify.com/nexgendata/pr-newswire-press-releases-scraper?fpr=2ayu9b) | `url`, `issuer`, `title`, `time_label`, `summary`, `image_url`, `date_published`, `date_modified` |
| AP News Scraper | [nexgendata/ap-news-scraper](https://apify.com/nexgendata/ap-news-scraper?fpr=2ayu9b) | `title`, `url`, `publishedAt`, `source`, `scrapedAt` |

Each tool runs on Apify and charges per record returned. Current prices are on each Store page.

## PR Newswire Scraper — Press Releases by Company, Topic & Date

Scrape PR Newswire press releases by keyword, topic, or date. Each release returns clean JSON — headline, summary, publish date, category, country, related stock tickers, and article URL. No API key. Pay per record.

Store page: https://apify.com/nexgendata/pr-newswire-press-releases-scraper?fpr=2ayu9b

**Output fields:** `url`, `issuer`, `title`, `time_label`, `summary`, `image_url`, `date_published`, `date_modified`, `description`, `body_text`, `tickers`, `category`, `country`, `source`, `truncated`, `truncation_reason`, `pages_fetched`

**Example record** (real output, run of 2026-10-31, some fields left out):

```json
{
  "url": "https://www.prnewswire.com/news-releases/settle-secures-up-to-100-million-in-forward-fl...",
  "issuer": "Settle Inc.",
  "title": "SETTLE SECURES UP TO $100 MILLION IN FORWARD-FLOW FINANCING FROM 3JANE",
  "time_label": null,
  "date_published": "2026-10-30T15:00:00Z",
  "date_modified": "2026-10-30T15:00:41Z",
  "category": null,
  "country": null
}
```

**Run it from code** (replace YOUR_APIFY_TOKEN):

```bash
curl -X POST 'https://api.apify.com/v2/acts/nexgendata~pr-newswire-press-releases-scraper/run-sync-get-dataset-items' \
  -H 'Authorization: Bearer YOUR_APIFY_TOKEN' -H 'Content-Type: application/json' \
  -d '{"keyword": "", "dateFrom": "", "dateTo": "", "includeFullBody": false, "maxReleases": 5, "proxyConfiguration": {"useApifyProxy": true, "apifyProxyGroups": ["RESIDENTIAL"]}}'
```

## AP News Scraper — Breaking News Headlines & Links

Scrape breaking-news headlines from AP News (Associated Press). Returns each story as clean JSON — headline, article URL, source, and capture time — ready for news monitoring, media dashboards, alerting, and feeding current-events context to AI agents. No login required. No API key. Pay per record.

Store page: https://apify.com/nexgendata/ap-news-scraper?fpr=2ayu9b

**Output fields:** `title`, `url`, `publishedAt`, `source`, `scrapedAt`

**Example record** (real output, run of 2026-11-03, some fields left out):

```json
{
  "title": "US job postings jumped sharply in September, potentially a good sign for anyone seeking...",
  "url": "https://apnews.com/article/job-openings-economy-inflation-layoffs-4f6f06216c943fc2f8306...",
  "publishedAt": "2026-11-03T16:20:00Z",
  "source": "AP News",
  "scrapedAt": "2026-11-03T16:50:48.270886Z"
}
```

**Run it from code** (replace YOUR_APIFY_TOKEN):

```bash
curl -X POST 'https://api.apify.com/v2/acts/nexgendata~ap-news-scraper/run-sync-get-dataset-items' \
  -H 'Authorization: Bearer YOUR_APIFY_TOKEN' -H 'Content-Type: application/json' \
  -d '{"maxArticles": 20, "section": "business"}'
```

---
Built by [NexGenData](https://apify.com/nexgendata?fpr=2ayu9b). Store links carry a NexGenData referral tag. Data comes from public and official sources; check each source's terms for your use.
