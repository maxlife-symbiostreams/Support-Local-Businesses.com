📄 DATA-SOURCES.md
# 📊 Data Sources — Where 6.4M Listings Come From

Transparency matters. Here's exactly where our data originates.

---

## Government Sources (Florida)

| Source | Agency | What It Contains |
|--------|--------|-----------------|
| **DBPR** | FL Dept of Business & Professional Regulation | Licensed businesses — contractors, cosmetologists, restaurants, etc. |
| **FLDFS** | FL Dept of Financial Services | Insurance agents, financial professionals |
| **FDACS** | FL Dept of Agriculture & Consumer Services | Food establishments, gas stations, LP gas dealers |

These are **public records** updated daily via our automated pipeline.

---

## Enrichment Sources

| Source | What We Pull | Daily Limit | Method |
|--------|-------------|-------------|--------|
| **Google Places API** | Website, phone, address verification | 357/day (2,500/week) | API (free tier) |
| **Yelp Fusion API** | Website, phone, ratings | 500/day | API (free tier) |
| **BBB** | Website, phone, accreditation | Unlimited | Headless scraper |

**Dedup layer** ensures no listing is queried twice across sources. We never overwrite existing data — only fill gaps.

---

## What We DON'T Do

- ❌ Scrape private data
- ❌ Sell personal information
- ❌ Access paywalled databases
- ❌ Use SunBiz for enrichment (no URLs available)
- ❌ Store data we can't legally use

All sources are either public government records or free API tiers within their terms of service.

---

## Enrichment Priority

1. **Orlando metro** — proving ground
2. **Miami metro** — volume test
3. **Tampa metro** — expansion
4. **Jacksonville metro** — coverage
5. **Rest of Florida** — state completion
6. **National** — funded by FL revenue

---

## Data Quality

We track enrichment coverage at `/admin/enrichment`:
- % of listings with verified website
- % with phone number
- % with email
- Per-source contribution stats
- 30-day growth trend

Current coverage is low (we just launched enrichment). Watch it grow in real-time.
