---

## 📄 `COMPARISON.md`

# ⚖️ SLB vs The Competition

Honest comparison. We win some, they win some.

---

| Feature | SLB | Google Places | Yelp Fusion | Foursquare |
|---------|-----|---------------|-------------|------------|
| **U.S. Listings** | 6.4M+ | Millions | Millions | Millions |
| **Free Tier** | ✅ Unlimited basic | 10K/month | 500/day | 950/day |
| **API Key Required** | ❌ No | ✅ Yes | ✅ Yes | ✅ Yes |
| **MCP Server** | ✅ Yes | ❌ No | ❌ No | ❌ No |
| **Agent Card** | ✅ Yes | ❌ No | ❌ No | ❌ No |
| **x402 Payments** | ✅ Yes | ❌ No | ❌ No | ❌ No |
| **OpenAPI Spec** | ✅ Public | ❌ | ❌ | ✅ Yes |
| **LLMs.txt** | ✅ Yes | ❌ No | ❌ No | ❌ No |
| **Claim & Manage** | ✅ Free | Via Google Business | Via Yelp Biz | ❌ No |
| **AI Podcast** | ✅ Yes | ❌ No | ❌ No | ❌ No |
| **AI Song** | ✅ Yes | ❌ No | ❌ No | ❌ No |
| **AI Video** | 🔨 Building | ❌ No | ❌ No | ❌ No |
| **Gamification** | ✅ Yes | ❌ No | ❌ No | Partial (legacy) |
| **Blog Feature** | ✅ $3 | ❌ No | ❌ No | ❌ No |
| **Cost at Scale** | Micropayments | $$$$ | $229/mo+ | $$$$ |
| **Reviews** | ❌ Not yet | ✅ Yes | ✅ Yes | ✅ Yes |
| **Photos** | 🔨 Building | ✅ Yes | ✅ Yes | ✅ Yes |
| **Global Coverage** | ❌ U.S. only | ✅ Global | ✅ Global | ✅ Global |

---

## Where We Win

- **Agent-readiness** — we're the only directory with MCP, Agent Card, LLMs.txt, AND x402. If you're building AI agents, we're plug-and-play. Everyone else requires API keys, OAuth, and human signup.
- **Zero-friction access** — no API key for basic queries. No account creation. Just `curl` and go.
- **Business owner features** — podcasts, songs, gamification, visibility reports. Nobody else generates a custom song for your pizza shop.
- **Price** — free for basic, micropayments for bulk. No $229/mo surprise bills.

## Where They Win

- **Reviews & photos** — Google and Yelp have years of user-generated content. We don't (yet).
- **Global coverage** — we're U.S. only. They're worldwide.
- **Brand recognition** — everyone knows Yelp. We're brand new.
- **Data depth** — their listings have richer metadata (hours, menus, etc.) for now. We're enriching daily.

## Our Take

We're not trying to replace Google or Yelp. We're building the **agent-native** business directory — the one AI assistants query when they need local business data. Different game, different rules.
📄 ROADMAP.md
# 🗺️ Roadmap

Where we've been and where we're headed. Updated monthly.

---

## ✅ Shipped (Live Now)

- [x] 6.4M+ U.S. business listings across 53 states/territories
- [x] REST API with free tier
- [x] MCP server for AI agents
- [x] Agent Card, OpenAPI spec, LLMs.txt
- [x] x402 micropayments on Base L2
- [x] Business claim & management dashboard
- [x] AI Visibility Report
- [x] Blog feature ($3 Stripe checkout)
- [x] Visibility boosts ($1/$5/$10 + $3/mo subscription)
- [x] First Visit Coupons with QR codes + tracking
- [x] AI podcast generation (13-min episodes)
- [x] AI song/jingle generation
- [x] Gamification engine (points, levels, badges)
- [x] Server-side rendering + JSON-LD schema
- [x] Chatbot on every page
- [x] Google Sign-In
- [x] County + ZIP niche directory pages
- [x] Daily automated enrichment crons (Google Places + Yelp + BBB)
- [x] FL government data pipeline (DBPR, FLDFS, FDACS)

---

## 🔨 In Progress (March 2026)

- [ ] AI video generation for business listings
- [ ] QA dashboard at `/admin/enrichment` for enrichment monitoring
- [ ] Expanding enrichment to full FL metro coverage
- [ ] Music feature QA + polish

---

## 🎯 Next Up (Q2 2026)

- [ ] Email outreach to unclaimed FL businesses (Brevo integration)
- [ ] Review system — let customers leave reviews on listings
- [ ] Photo uploads for business owners
- [ ] Business hours field + enrichment
- [ ] "Near Me" geolocation search on mobile
- [ ] Weekly enrichment growth report emails

---

## 🔮 Future (Q3-Q4 2026)

- [ ] National enrichment expansion (TX, CA, NY next)
- [ ] Business owner mobile app (or PWA)
- [ ] Agent marketplace — let third-party agents offer services to listed businesses
- [ ] Franchise/multi-location management
- [ ] Premium API tier with webhooks and real-time data
- [ ] Embed widget — businesses put their SLB listing on their own site

---

## 🌙 Dream Features

- [ ] Voice search ("Hey, find me a plumber in Orlando")
- [ ] AR "point your camera at a storefront" → see their listing
- [ ] Community-contributed data (wiki-style editing)
- [ ] International expansion

---

## How We Prioritize

Revenue-generating features first. Everything else follows the money.

We're self-funded — every feature has to earn its keep or directly enable something that does.
