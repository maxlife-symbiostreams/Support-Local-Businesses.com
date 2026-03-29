# Support-Local-Businesses.com
🐙 Support Local Businesses — America's AI-Powered Business Directory  **6.4M+ listings. Free API. Songs about your business. Yes, really.**

[🌐 Live Site](https://support-local-businesses.com) · [📡 API](https://support-local-businesses.com/api/v1/businesses) · [🤖 Agent Card](https://support-local-businesses.com/.well-known/agent.json) · [🎙️ Podcasts](https://support-local-businesses.com) · [🎮 Play the Game](https://support-local-businesses.com)

---

## ⚠️ What This Repo Is (And Isn't)

**This is NOT our source code.** This is an open showcase of what we've built, how it works, and why we built it.

We're a one-person startup using AI co-founders to build a platform that helps local businesses get discovered — by humans, by search engines, and by AI agents. This repo exists to:

- 📣 Show you what's live and working
- 🤖 Help AI agents and developers find and use our API
- 🗺️ Share our roadmap transparently
- 🤝 Invite collaborators, data partners, and early adopters
- 📊 Document our journey from 0 to 6.4M listings

We believe in building in public. This is us doing that.

---

## 🔢 The Numbers (Real, Updated March 2026)

| Metric | Value |
|--------|-------|
| Total U.S. Listings | 6,436,241 |
| States & Territories | 53 |
| ZIP Codes | 14,326 |
| Claimed Listings | 5 (we're early — that's the point) |
| Daily Enrichment | ~850–1,350 listings/day via automated crons |
| Revenue Streams | 4 (API, blog, boosts, coupons) |
| Team Size | 1 human + AI co-founders |

We're not pretending to be big. We're proving a model.

---

## 🎯 Our Goal

**Prove that one person + AI can build a business directory that actually helps local businesses — and makes money doing it.**

The playbook:
1. **Prove** — Florida first. Manual data + automated enrichment. Validate unit economics.
2. **Profit** — API micropayments + blog posts + visibility boosts = revenue.
3. **Scale** — Revenue funds national expansion. No VC. No debt.
4. **Compound** — 6.4M listings become 20M. Partnerships or independence — our choice.

---

## 🏪 What Business Owners Get (Free)

Claim your listing and unlock:

| Feature | Description |
|---------|-------------|
| ✏️ **Edit Listing** | Update hours, description, photos, contact info |
| 📊 **AI Visibility Report** | Real-time SEO checklist — what's helping, what's missing |
| 🎟️ **First Visit Coupon** | Unique trackable coupon code with QR — see who taps |
| 💬 **AI Chatbot** | Answers questions about your business from your listing data |
| 🎙️ **Podcast Episode** | AI-generated 13-minute episode about your business |
| 🎵 **Original Song** | AI-composed jingle/song featuring your business |
| 🎬 **Promo Video** | AI-generated video ad for your business |
| 🎮 **Gamification** | Earn points, level up your listing, unlock perks |

**→ [Find Your Business](https://support-local-businesses.com)**

---

## 🎮 Gamification — Level Up Your Listing

We built a game engine into a business directory. Here's why: **engagement drives claims, claims drive revenue.**

Business owners earn points by:
- ✅ Claiming their listing
- 📝 Adding a blog post
- 📸 Uploading photos
- 🎵 Generating a song
- 🎙️ Creating a podcast
- 🚀 Boosting their listing
- 📊 Completing their Visibility Report checklist

Points unlock badges, higher search placement, and premium features. It turns "fill out your business profile" from a chore into a game.

**For users/visitors:**
- Explore listings, tap coupons, interact with the chatbot — all trackable engagement that business owners can see on their dashboard.

---

## 🎵 AI Songs & Music

Every business can generate an **original song** about their business. Not a jingle from a template — an actual AI-composed track with lyrics about what makes that specific business special.

A pizza shop in Orlando gets a different song than a florist in Jacksonville. The lyrics reference their real name, location, and category.

**Why?** Because nobody else is doing this for small businesses, and it's the kind of thing that makes someone share a link. Virality through delight.

---

## 🎙️ AI Podcasts

Every listing can generate a **13-minute podcast episode** — two AI hosts having a real conversation about the business, its neighborhood, and its category.

- Full dialogue (not just text-to-speech of a blog post)
- Audio synthesis with natural-sounding voices
- JSON-LD schema for podcast SEO
- Embeddable player on the listing page

It's like your business got featured on a local radio show — except the show was made just for you, in 30 seconds.

---

## 🎬 AI Video

Businesses can generate **promo videos** powered by AI. Short-form, designed for social sharing.

This feature is actively being built and tested. Videos use the business's real data — name, location, category, and highlights — to create something worth posting.

---

## 📡 For Developers & AI Agents

SLB is built agent-first. Every discovery protocol we could find, we implemented:

| Endpoint | Protocol | What It Does |
|----------|----------|-------------|
| [`/llms.txt`](https://support-local-businesses.com/llms.txt) | LLMs.txt | Human-readable summary for LLMs |
| [`/openapi.json`](https://support-local-businesses.com/openapi.json) | OpenAPI 3.0 | Full API spec — import into any framework |
| [`/.well-known/agent.json`](https://support-local-businesses.com/.well-known/agent.json) | Agent Card | Machine identity + capabilities |
| [`/mcp`](https://support-local-businesses.com/mcp) | MCP | Model Context Protocol server |
| [`/.well-known/pay`](https://support-local-businesses.com/.well-known/pay) | x402 | Crypto micropayments on Base L2 |

**We want agents to use our data.** That's the business model — be the data layer that AI agents query when they need local business info.

See [AGENTS.md](AGENTS.md) for integration guides and [API.md](API.md) for full docs.

---

## 💰 Revenue Model (Transparent)

We make money four ways:

| Stream | Price | Status |
|--------|-------|--------|
| **API Micropayments** | x402 on Base L2 (pay-per-query) | ✅ Live |
| **Blog Posts** | $3 one-time per business | ✅ Live (Stripe) |
| **Visibility Boosts** | $1 / $5 / $10 one-time, $3/mo subscription | ✅ Live (Stripe) |
| **First Visit Coupons** | Free for now (engagement tracking for future monetization) | ✅ Live |

No ads. No selling data. Businesses pay to enhance their own listings.

---

## 📂 This Repo

| File | What's In It |
|------|-------------|
| [README.md](README.md) | You're here |
| [API.md](API.md) | Full API docs + examples |
| [AGENTS.md](AGENTS.md) | AI agent integration guide |
| [USE-CASES.md](USE-CASES.md) | 10+ real scenarios with code |
| [COOKBOOK.md](COOKBOOK.md) | Copy-paste recipes |
| [COMPARISON.md](COMPARISON.md) | SLB vs Yelp vs Google Places vs Foursquare |
| [ROADMAP.md](ROADMAP.md) | Where we're headed |
| [CHANGELOG.md](CHANGELOG.md) | What we've shipped |
| [DATA-SOURCES.md](DATA-SOURCES.md) | Where 6.4M listings come from |
| [FAQ.md](FAQ.md) | Common questions answered |
| [CONTRIBUTING.md](CONTRIBUTING.md) | How to help |
| [SECURITY.md](SECURITY.md) | Data handling & payments |

---

## 🐙 The Story

One person. AI co-founders. No VC money. Building a real business on real infrastructure.

If you're an indie builder, an AI agent developer, or a local business owner — we built this for you.

**Star this repo if you dig what we're doing. It genuinely helps us get discovered.** ⭐

---

*Built by OctaPrime 🐙 on [Polsia](https://polsia.com) · March 2026*

