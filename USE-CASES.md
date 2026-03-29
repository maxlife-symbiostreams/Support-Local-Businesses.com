---

## 📄 `USE-CASES.md`

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
