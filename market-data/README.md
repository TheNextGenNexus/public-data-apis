# Stock Screener and Market Data API: Finviz screener, Kalshi odds, ETF holdings, unusual options and CFTC COT

Get market data as JSON: stock screener rows (ticker, sector, market cap, P/E, price), prediction-market odds, ETF holdings and weights, unusual options activity, and weekly Commitment of Traders positions.

Sources: Finviz screener pages, the Kalshi public market data, public ETF holdings pages, Nasdaq/Cboe options-chain quotes and the CFTC Commitment of Traders reports.

Used by analysts, quant researchers and AI agents. Data only, not investment advice.

## Which tool to use

| You want | Tool (Apify Store) | Returns |
|---|---|---|
| Finviz Stock Screener | [nexgendata/finviz-stock-screener](https://apify.com/nexgendata/finviz-stock-screener?fpr=2ayu9b) | `ticker`, `company`, `sector`, `industry`, `country`, `market_cap_mkt_cap`, `pe`, `price` |
| Kalshi Prediction Markets | [nexgendata/kalshi-prediction-markets-tracker](https://apify.com/nexgendata/kalshi-prediction-markets-tracker?fpr=2ayu9b) | `ticker`, `title`, `yesSubTitle`, `eventTicker`, `eventTitle`, `eventSubTitle`, `seriesTicker`, `category` |
| ETF Holdings Tracker | [nexgendata/etf-holdings-tracker](https://apify.com/nexgendata/etf-holdings-tracker?fpr=2ayu9b) | `etf_symbol`, `etf_name`, `etf_issuer`, `etf_aum_billion_usd`, `etf_aum_usd`, `holding_symbol`, `holding_name`, `holding_sector` |
| Unusual Options Activity Tracker | [nexgendata/options-unusual-activity](https://apify.com/nexgendata/options-unusual-activity?fpr=2ayu9b) | `symbol`, `company_name`, `current_stock_price`, `option_type`, `strike_price`, `expiration_date`, `days_to_expiration`, `volume` |
| CFTC COT Enhanced | [nexgendata/cftc-cot-position-velocity-tracker](https://apify.com/nexgendata/cftc-cot-position-velocity-tracker?fpr=2ayu9b) | `commodity_name`, `contract_market_name`, `contract_code`, `market_and_exchange_names`, `exchange`, `report_date`, `report_week`, `report_type` |

Each tool runs on Apify and charges per record returned. Current prices are on each Store page.

## Finviz Stock Screener — US Market Data API

Screen US (NYSE/Nasdaq) stocks via any Finviz screener URL — ticker, sector, market cap, P/E, price as clean JSON. For analysts and AI agents. No API key. Pay per record.

Store page: https://apify.com/nexgendata/finviz-stock-screener?fpr=2ayu9b

**Output fields:** `ticker`, `company`, `sector`, `industry`, `country`, `market_cap_mkt_cap`, `pe`, `price`, `change_chg`, `volume_vol`, `sourceUrl`

**Example record** (real output, run of 2026-10-31, some fields left out):

```json
{
  "ticker": "AAPL",
  "company": "Apple Inc",
  "sector": "Technology",
  "industry": "Consumer Electronics",
  "country": "USA",
  "market_cap_mkt_cap": "5029.59B",
  "pe": "39.51",
  "price": "344.63"
}
```

**Run it from code** (replace YOUR_APIFY_TOKEN):

```bash
curl -X POST 'https://api.apify.com/v2/acts/nexgendata~finviz-stock-screener/run-sync-get-dataset-items' \
  -H 'Authorization: Bearer YOUR_APIFY_TOKEN' -H 'Content-Type: application/json' \
  -d '{"screenerUrl": "https://finviz.com/screener.ashx?v=111&f=cap_largeover", "maxResults": 50}'
```

## Kalshi Prediction Markets — Odds, Probabilities, Volume

Track live Kalshi prediction markets: yes/no bid/ask, last price, implied probability, volume, liquidity, and close time. For traders, researchers, and media tracking event odds. No API key. Pay per record.

Store page: https://apify.com/nexgendata/kalshi-prediction-markets-tracker?fpr=2ayu9b

**Output fields:** `ticker`, `title`, `yesSubTitle`, `eventTicker`, `eventTitle`, `eventSubTitle`, `seriesTicker`, `category`, `status`, `yesBid`, `yesAsk`, `noBid`, `noAsk`, `lastPrice`, `previousPrice`, `impliedYesProbability`, `volume`, `volume24h`, `openInterest`, `liquidity`, `openTime`, `closeTime`, `expirationTime`, `marketType`, `rulesPrimary`

**Example record** (real output, run of 2026-11-02, some fields left out):

```json
{
  "ticker": "CONTROLH-2026-R",
  "title": "Will Republicans win the House in 2026?",
  "yesSubTitle": "Republican Party",
  "eventTicker": "CONTROLH-2026",
  "eventTitle": "Who will control the House?",
  "eventSubTitle": "In 2026",
  "seriesTicker": "CONTROLH",
  "category": "Elections"
}
```

**Run it from code** (replace YOUR_APIFY_TOKEN):

```bash
curl -X POST 'https://api.apify.com/v2/acts/nexgendata~kalshi-prediction-markets-tracker/run-sync-get-dataset-items' \
  -H 'Authorization: Bearer YOUR_APIFY_TOKEN' -H 'Content-Type: application/json' \
  -d '{"status": "open", "maxResults": 25}'
```

## ETF Holdings Tracker — Daily Constituents & Weights API

Track the top holdings and weights of US-listed ETFs — parsed from public ETF pages into source-linked JSON for analysts, funds and AI agents. No API key. Pay per record.

Store page: https://apify.com/nexgendata/etf-holdings-tracker?fpr=2ayu9b

**Output fields:** `etf_symbol`, `etf_name`, `etf_issuer`, `etf_aum_billion_usd`, `etf_aum_usd`, `holding_symbol`, `holding_name`, `holding_sector`, `weight_pct`, `shares_held`, `market_value_usd`, `holding_country`, `as_of_date`, `etf_holdings_url`, `data_source`

**Example record** (real output, run of 2026-11-03, some fields left out):

```json
{
  "etf_symbol": "SPY",
  "etf_name": "State Street SPDR S&P 500 ETF",
  "etf_issuer": "State Street",
  "etf_aum_billion_usd": 811.55,
  "etf_aum_usd": 811550000000,
  "holding_symbol": "AAPL",
  "holding_name": "Apple Inc.",
  "holding_sector": "Technology"
}
```

**Run it from code** (replace YOUR_APIFY_TOKEN):

```bash
curl -X POST 'https://api.apify.com/v2/acts/nexgendata~etf-holdings-tracker/run-sync-get-dataset-items' \
  -H 'Authorization: Bearer YOUR_APIFY_TOKEN' -H 'Content-Type: application/json' \
  -d '{"etf_symbols": ["SPY", "QQQ", "VTI"], "limit": 25, "max_holdings_per_etf": 100, "min_weight_pct": 0, "country": "all", "issuer": "all"}'
```

## Unusual Options Activity Tracker — Flow & Volume API

Track unusual options activity from public US options-chain quotes (Nasdaq, with Cboe delayed quotes as fallback) — source-linked JSON for analysts, funds and AI agents. No API key. Pay per record.

Store page: https://apify.com/nexgendata/options-unusual-activity?fpr=2ayu9b

**Output fields:** `symbol`, `company_name`, `current_stock_price`, `option_type`, `strike_price`, `expiration_date`, `days_to_expiration`, `volume`, `open_interest`, `volume_oi_ratio`, `last_trade_price`, `bid`, `ask`, `mid`, `implied_volatility_pct`, `delta`, `gamma`, `theta`, `vega`, `total_premium_traded_usd`, `moneyness`, `unusual_score`, `occ_symbol`, `data_source`, `source_url`, `as_of_date`, `fetched_at_utc`

**Example record** (real output, run of 2026-11-02, some fields left out):

```json
{
  "symbol": "NVDA",
  "company_name": "NVIDIA CORP",
  "current_stock_price": 205.2499,
  "option_type": "Call",
  "strike_price": 237.5,
  "expiration_date": "2026-11-20",
  "days_to_expiration": 18,
  "volume": 39256
}
```

**Run it from code** (replace YOUR_APIFY_TOKEN):

```bash
curl -X POST 'https://api.apify.com/v2/acts/nexgendata~options-unusual-activity/run-sync-get-dataset-items' \
  -H 'Authorization: Bearer YOUR_APIFY_TOKEN' -H 'Content-Type: application/json' \
  -d '{"limit": 25, "option_type": "all", "min_volume": 500, "min_volume_oi_ratio": 2.0, "max_days_to_expiration": 60, "min_open_interest": 100, "min_premium_traded_usd": 10000, "moneyness": "any"}'
```

## CFTC COT Enhanced — Position Velocity & Percentile Tracker

Weekly CFTC Commitment of Traders with the percentile + velocity overlay every commodity desk builds in Excel: net position, 3-yr percentile, week-over-week velocity for managed money, swap dealers, commercials, non-reportables. Legacy, disaggregated, TFF families. From publicreporting.cftc.gov.

Store page: https://apify.com/nexgendata/cftc-cot-position-velocity-tracker?fpr=2ayu9b

**Output fields:** `commodity_name`, `contract_market_name`, `contract_code`, `market_and_exchange_names`, `exchange`, `report_date`, `report_week`, `report_type`, `category`, `long_positions`, `short_positions`, `spread_positions`, `net_position`, `open_interest_all`, `percentile_3yr`, `percentile_window_weeks`, `velocity_week_over_week_pct`, `source_url`, `data_source`

**Example record** (real output, run of 2026-11-02, some fields left out):

```json
{
  "commodity_name": "CRUDE OIL",
  "contract_market_name": "WTI-PHYSICAL",
  "contract_code": "067651",
  "market_and_exchange_names": "WTI-PHYSICAL - NEW YORK MERCANTILE EXCHANGE",
  "exchange": "NEW YORK MERCANTILE EXCHANGE",
  "report_date": "2026-10-27",
  "report_week": "2026 Report Week 43",
  "report_type": "disaggregated"
}
```

**Run it from code** (replace YOUR_APIFY_TOKEN):

```bash
curl -X POST 'https://api.apify.com/v2/acts/nexgendata~cftc-cot-position-velocity-tracker/run-sync-get-dataset-items' \
  -H 'Authorization: Bearer YOUR_APIFY_TOKEN' -H 'Content-Type: application/json' \
  -d '{"commodity": "WTI CRUDE OIL", "report_type": "disaggregated", "weeks_back": 52, "category": "managed_money", "max_records": 25}'
```

---
Built by [NexGenData](https://apify.com/nexgendata?fpr=2ayu9b). Store links carry a NexGenData referral tag. Data comes from public and official sources; check each source's terms for your use.
