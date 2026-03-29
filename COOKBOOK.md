---

## 📄 `COOKBOOK.md`

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
