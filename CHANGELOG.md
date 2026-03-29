📄 CHANGELOG.md
# 📋 Changelog

What we've shipped, most recent first.

---

## March 2026

### Week of Mar 24–29
- 🔧 Fixed directory page timeouts — added 3 DB indexes on 6.4M-row table, 300x faster
- 🔧 Built FL government pipeline cron — DBPR, FLDFS, FDACS auto-import daily at 11pm EST
- 🆕 Built 3-tier enrichment cron — Google Places (357/day) → Yelp (500/day) → BBB scraper
- 🆕 QA enrichment dashboard at `/admin/enrichment` — coverage stats, growth charts, stale alerts
- 🆕 Startup cache warm for top 30 FL ZIP codes
- 🧪 Launched browser QA tests — 3 fake businesses across Orlando, Miami, Jacksonville

### Week of Mar 17–23
- 🆕 First Visit Coupon feature live — forest green banner, unique codes, QR, Meta Pixel tracking
- 🆕 Coupon engagement sidebar on business profiles
- 🔧 Music generation fixes (3 iterations)
- 🆕 Podcast JSON-LD schema
- 🆕 Game engine live

### Earlier March
- 🆕 Agent discovery suite: `/llms.txt`, `/openapi.json`, `/.well-known/agent.json`, `/mcp`, `/.well-known/pay`
- 🆕 x402 micropayments on Base L2
- 🆕 Google Sign-In
- 🆕 ZIP-level niche pages
- 🆕 Chatbot with daily token limits
- 📊 6,436,241 total listings confirmed

---

## February 2026
- 🆕 County-level niche directory pages
- 🆕 AI Visibility Report
- 🆕 Boost tiers (Stripe checkout)
- 🆕 Blog feature (Stripe checkout)
- 🔧 Server-side rendering across all pages
- 📊 Crossed 6M listings

---

*Updated weekly. Star the repo to follow along.* ⭐
