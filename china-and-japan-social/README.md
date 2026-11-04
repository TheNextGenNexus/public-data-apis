# Bilibili, Xiaohongshu (RedNote), China trending topics and 5ch data API

Get Chinese and Japanese social and video data as JSON: Bilibili video search results, Xiaohongshu (RedNote) notes, trending topics from Weibo, Baidu, Toutiao and Douyin, and 5ch (5channel) threads.

Sources: Bilibili keyword search (no login), Xiaohongshu public notes, the public hot-search lists of Weibo, Baidu, Toutiao and Douyin, and 5ch boards.

Used for China and Japan market research, brand and trend monitoring, and as input for AI agents.

<!-- ngd-site-links -->
## On thenextgennexus.com

- [如何用 API 按关键词批量抓取B站视频数据？](https://thenextgennexus.com/zh/guides/bilibili-video-search/)
- [如何用 API 获取微博热搜和中国各平台热榜？](https://thenextgennexus.com/zh/guides/weibo-trends/)
- [中国市场数据全家桶 China Market Data Suite](https://thenextgennexus.com/china/)
- [🇯🇵 日本市場データツール Japan Data Toolkit](https://thenextgennexus.com/japan/)
- [All NexGenData guides by topic](https://thenextgennexus.com/tools/#every-page)
<!-- /ngd-site-links -->

## Which tool to use

| You want | Tool (Apify Store) | Returns |
|---|---|---|
| Bilibili Video Search by Keyword | [nexgendata/bilibili-video-search](https://apify.com/nexgendata/bilibili-video-search?fpr=2ayu9b) | `bvid`, `aid`, `url`, `title`, `description`, `author`, `mid`, `duration` |
| Xiaohongshu Scraper | [nexgendata/rednote-scraper](https://apify.com/nexgendata/rednote-scraper?fpr=2ayu9b) | `post_id`, `author`, `author_id`, `title`, `body`, `image_urls`, `hashtags`, `likes_count` |
| China Trends Tracker | [nexgendata/china-trends-tracker](https://apify.com/nexgendata/china-trends-tracker?fpr=2ayu9b) | `source`, `rank`, `topic`, `score`, `label`, `url`, `scraped_at` |
| 5ch Thread Tracker | [nexgendata/5ch-thread-tracker](https://apify.com/nexgendata/5ch-thread-tracker?fpr=2ayu9b) | `board`, `thread_id`, `title`, `post_count`, `thread_url`, `last_active`, `data_source`, `as_of_timestamp` |

Each tool runs on Apify and charges per record returned. Current prices are on each Store page.

## Bilibili Video Search by Keyword · B站视频搜索 (No Login)

Search Bilibili (B站, Chinese video platform) for videos by keyword — no login, no API key, no cookie. Returns BV-id, title, author, play count, likes, danmaku, duration, publish date and thumbnail. Keyword search (not URL-by-URL) for Chinese AI corpora & trends. Pay per record.

Store page: https://apify.com/nexgendata/bilibili-video-search?fpr=2ayu9b

**Output fields:** `bvid`, `aid`, `url`, `title`, `description`, `author`, `mid`, `duration`, `play_count`, `danmaku_count`, `favorites`, `likes`, `tag`, `pub_date`, `thumbnail`, `keyword`, `scraped_at`

**Run it from code** (replace YOUR_APIFY_TOKEN):

```bash
curl -X POST 'https://api.apify.com/v2/acts/nexgendata~bilibili-video-search/run-sync-get-dataset-items' \
  -H 'Authorization: Bearer YOUR_APIFY_TOKEN' -H 'Content-Type: application/json' \
  -d '{"keyword": "机器学习", "max_results": 30, "addonSentimentScored": false, "addonSocialHandlesExtracted": false}'
```

## Xiaohongshu Scraper — RedNote Scraper for Trending & Notes

Xiaohongshu scraper (RedNote scraper) across 6 modes: trending, note_detail, user_posts, hashtag, keyword_search, topic_probe. Trending, note detail and user posts run cookieless; keyword/hashtag search is login-gated. Clean JSON + metrics. No API key. Pay per record.

Store page: https://apify.com/nexgendata/rednote-scraper?fpr=2ayu9b

**Output fields:** `post_id`, `author`, `author_id`, `title`, `body`, `image_urls`, `hashtags`, `likes_count`, `comments_count`, `shares_count`, `collected_count`, `engagement_total`, `posted_at`, `url`, `category`, `mode`, `query`, `data_source`, `as_of_timestamp`

## China Trends Tracker · 中国趋势汇总(微博/百度/头条/抖音)

Aggregate real-time trending topics from China's top platforms: Weibo Hot Search, Baidu Hot, Toutiao Hot Board and Douyin Hot Search. Returns topic, rank, score and source URL in one call. No API key. Pay per record.

Store page: https://apify.com/nexgendata/china-trends-tracker?fpr=2ayu9b

**Output fields:** `source`, `rank`, `topic`, `score`, `label`, `url`, `scraped_at`

**Run it from code** (replace YOUR_APIFY_TOKEN):

```bash
curl -X POST 'https://api.apify.com/v2/acts/nexgendata~china-trends-tracker/run-sync-get-dataset-items' \
  -H 'Authorization: Bearer YOUR_APIFY_TOKEN' -H 'Content-Type: application/json' \
  -d '{"proxyConfiguration": {"useApifyProxy": true, "apifyProxyGroups": ["RESIDENTIAL"]}}'
```

## 5ch Thread Tracker — 5ちゃんねる API

Track Japan 5ch (5channel) threads and posts. Clean JSON for analysts, quants and AI agents.

Store page: https://apify.com/nexgendata/5ch-thread-tracker?fpr=2ayu9b

**Output fields:** `board`, `thread_id`, `title`, `post_count`, `thread_url`, `last_active`, `data_source`, `as_of_timestamp`

**Run it from code** (replace YOUR_APIFY_TOKEN):

```bash
curl -X POST 'https://api.apify.com/v2/acts/nexgendata~5ch-thread-tracker/run-sync-get-dataset-items' \
  -H 'Authorization: Bearer YOUR_APIFY_TOKEN' -H 'Content-Type: application/json' \
  -d '{"mode": "board-threads", "board": "newsplus", "maxItems": 20, "proxyConfiguration": {"useApifyProxy": true}}'
```

---
Built by [NexGenData](https://apify.com/nexgendata?fpr=2ayu9b). Store links carry a NexGenData referral tag. Data comes from public and official sources; check each source's terms for your use.
