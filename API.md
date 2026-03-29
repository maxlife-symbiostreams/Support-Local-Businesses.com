📄 API.md
# 📡 API Documentation

**Base URL:** `https://support-local-businesses.com/api/v1`

---

## Overview

Free access to 6.4M+ U.S. business listings. No API key for basic queries. x402 micropayments on Base L2 for premium/bulk access.

---

## `GET /businesses`

| Parameter | Type | Description | Example |
|-----------|------|-------------|---------|
| `zip` | string | 5-digit ZIP | `32801` |
| `city` | string | City name | `Orlando` |
| `state` | string | 2-letter code | `FL` |
| `category` | string | Business type | `restaurant` |
| `q` | string | Keyword search | `pizza` |
| `limit` | number | Results per page (max 100) | `25` |
| `offset` | number | Pagination offset | `0` |

All parameters optional. Combine freely.

---

## Examples

```bash
# Restaurants in Orlando
curl "https://support-local-businesses.com/api/v1/businesses?city=Orlando&category=restaurant&limit=10"

# Everything in a ZIP
curl "https://support-local-businesses.com/api/v1/businesses?zip=33130&limit=50"

# Keyword search statewide
curl "https://support-local-businesses.com/api/v1/businesses?state=FL&q=plumber&limit=20"


Response
{
  "results": [
    {
      "name": "Tony's Famous Pizza",
      "address": "123 Main St",
      "city": "Orlando",
      "state": "FL",
      "zip": "32801",
      "category": "restaurant",
      "phone": "407-555-0123",
      "website": "https://tonyspizza.com",
      "claimed": false,
      "slug": "tonys-famous-pizza-orlando",
      "url": "https://support-local-businesses.com/business/tonys-famous-pizza-orlando"
    }
  ],
  "total": 1432,
  "limit": 10,
  "offset": 0
}


Rate Limits & Pricing
Tier
Access
Auth
Free
Basic queries, reasonable use
None
Premium
Bulk data, enriched fields, higher limits
x402 micropayment (Base L2)

No API keys. No subscriptions. Free for light use, pay-per-query for heavy use.
x402 discovery: /.well-known/pay

Niche Pages (Browse by Category + Location)
Every combination has a dedicated, SEO-indexed page:
County: /niche/{state}/{county}/{category}
ZIP: /niche/{state}/{zipcode}/{category}
Example: /niche/florida/32801/restaurant

---

## 📄 `AGENTS.md`

```markdown
# 🤖 AI Agent Integration Guide

SLB was built agent-first. If your AI agent needs U.S. business data, we're the easiest integration available.

---

## Discovery Endpoints

| URL | Protocol | Purpose |
|-----|----------|---------|
| [`/llms.txt`](https://support-local-businesses.com/llms.txt) | LLMs.txt | Natural-language site description |
| [`/openapi.json`](https://support-local-businesses.com/openapi.json) | OpenAPI 3.0 | Import into any agent framework |
| [`/.well-known/agent.json`](https://support-local-businesses.com/.well-known/agent.json) | Agent Card | Machine identity + capabilities |
| [`/mcp`](https://support-local-businesses.com/mcp) | MCP | Model Context Protocol server |
| [`/.well-known/pay`](https://support-local-businesses.com/.well-known/pay) | x402 | Payment discovery (Base L2) |

---

## MCP Setup (Claude, Cursor, Windsurf)

```json
{
  "mcpServers": {
    "support-local-businesses": {
      "url": "https://support-local-businesses.com/mcp",
      "description": "Search 6.4M+ US business listings by ZIP, city, state, or category"
    }
  }
}

Then just ask naturally:
"Find 5 plumbers in Miami 33130"

OpenAPI / LangChain / CrewAI
import requests
spec = requests.get("https://support-local-businesses.com/openapi.json").json()
# Feed spec to your agent framework


Agent-to-Agent Payments (x402)
No API keys. No OAuth. Your agent pays per-request in crypto on Base L2.
Agent calls API → gets 402 Payment Required
Reads payment details from response header
Sends Base L2 transaction
Gets enriched data back
Zero friction. Machine-to-machine commerce.

What Agents Use SLB For
Use Case
Example Query
Lead generation
"All unclaimed restaurants in ZIP 32801"
Market research
"How many fitness businesses in Miami-Dade?"
Local SEO
"Competitors for 'plumber' in Tampa"
Sales prospecting
"Businesses without websites in Jacksonville"
Data enrichment
"Phone + website for these 50 business names"
Content generation
"Generate a podcast about this business"


Our Agent Philosophy
We believe the next wave of internet commerce is agent-to-agent. An AI assistant asks "find me a good electrician nearby" — and it queries SLB's API, not Google. That's the future we're building for.
If you're building agents, we want to be in your tool belt.

---

## 📄 `USE-CASES.md`

```markdown
# 💡 Use Cases

Real scenarios. Real code. Copy and adapt.

---

## 1. Lead Gen Bot — Find Businesses Without Websites

```bash
curl "https://support-local-businesses.com/api/v1/businesses?city=Orlando&category=restaurant&limit=50" \
  | jq '[.results[] | select(.website == null)] | length'

Why: Businesses without websites are the hottest leads for web design agencies, marketing firms, and SaaS products.

2. Market Density Analysis
# How many fitness businesses in each Miami ZIP?
for zip in 33101 33109 33125 33130 33131 33132 33133 33134 33135 33136; do
  count=$(curl -s "https://support-local-businesses.com/api/v1/businesses?zip=$zip&category=fitness" | jq '.total')
  echo "$zip: $count"
done

Why: Spot underserved ZIPs before opening a new location.

3. Competitor Audit
curl "https://support-local-businesses.com/api/v1/businesses?zip=32801&category=restaurant&limit=100"

Why: See every restaurant in your ZIP. Check who has websites, blogs, and claimed listings. Find gaps.

4. CRM Enrichment
import requests

# Your existing leads
leads = ["Joe's Auto Repair", "Sunrise Bakery", "Palm Tree Dental"]

for name in leads:
    r = requests.get(f"https://support-local-businesses.com/api/v1/businesses?q={name}&state=FL&limit=1")
    biz = r.json()["results"][0] if r.json()["results"] else None
    if biz:
        print(f"{biz['name']}: {biz.get('phone', 'N/A')} | {biz.get('website', 'N/A')}")

Why: Enrich your existing contacts with phone, website, and address data.

5. AI Agent — Local Business Finder
# In your LangChain/CrewAI agent
tools = [
    {
        "name": "search_local_businesses",
        "description": "Search US businesses by location and category",
        "endpoint": "https://support-local-businesses.com/api/v1/businesses",
        "parameters": ["zip", "city", "state", "category", "q", "limit"]
    }
]

# Agent can now answer: "Find me a florist near 32202"


6. Unclaimed Listing Prospecting
curl "https://support-local-businesses.com/api/v1/businesses?zip=32801&limit=50" \
  | jq '[.results[] | select(.claimed == false)] | .[:5]'

Why: 99.99% of our 6.4M listings are unclaimed. That's 6.4M potential customers for anyone selling to small businesses.

7. Content Generation Pipeline
# Get businesses, then generate content for each
businesses=$(curl -s "https://support-local-businesses.com/api/v1/businesses?city=Tampa&category=restaurant&limit=5")
echo $businesses | jq -r '.results[].name'
# Feed to your content agent for blog posts, social media, newsletters


8. Neighborhood Explorer
# What types of businesses are in this ZIP?
curl "https://support-local-businesses.com/api/v1/businesses?zip=33130&limit=100" \
  | jq '[.results[].category] | group_by(.) | map({(.[0]): length}) | add'

Why: Understand the commercial makeup of any U.S. neighborhood.

9. Real Estate Intelligence
Cross-reference business density with property listings. ZIPs with growing business counts signal economic development — useful for investors, developers, and commercial real estate agents.

10. Local Government / Economic Development
City planners can query business counts by category to understand gaps in local services. "Does this ZIP have a pharmacy? A grocery store? How many?"

All examples use real endpoints. Try them now.

---

## 📄 `COOKBOOK.md`

```markdown
# 🍳 Cookbook — Copy-Paste Recipes

Quick patterns you can drop into your code or agent.

---

## Recipe 1: "Give me all pizza places in this ZIP"

```bash
curl "https://support-local-businesses.com/api/v1/businesses?zip=32801&q=pizza&limit=25"


Recipe 2: "How many businesses are in this city?"
curl -s "https://support-local-businesses.com/api/v1/businesses?city=Orlando&limit=1" | jq '.total'


Recipe 3: "Find businesses missing websites" (lead gen gold)
curl -s "https://support-local-businesses.com/api/v1/businesses?zip=33130&limit=100" \
  | jq '[.results[] | select(.website == null) | {name, phone, address}]'


Recipe 4: "Page through all results"
# Page 1
curl "https://support-local-businesses.com/api/v1/businesses?state=FL&category=fitness&limit=100&offset=0"
# Page 2
curl "https://support-local-businesses.com/api/v1/businesses?state=FL&category=fitness&limit=100&offset=100"
# And so on...


Recipe 5: "Add SLB to my MCP agent in 10 seconds"
{
  "mcpServers": {
    "slb": {
      "url": "https://support-local-businesses.com/mcp"
    }
  }
}

Done. Your agent can now search 6.4M businesses.

Recipe 6: "Build a 'businesses near me' feature"
// Get user's ZIP from their input or geolocation
const zip = "32801";
const res = await fetch(`https://support-local-businesses.com/api/v1/businesses?zip=${zip}&limit=20`);
const data = await res.json();
// Render data.results in your UI


Recipe 7: "Export a category to CSV"
curl -s "https://support-local-businesses.com/api/v1/businesses?city=Jacksonville&category=restaurant&limit=100" \
  | jq -r '.results[] | [.name, .address, .city, .zip, .phone, .website] | @csv'


---

## 📄 `COMPARISON.md`

```markdown
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
