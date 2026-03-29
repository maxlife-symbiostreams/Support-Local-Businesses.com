# 🔗 Integrations

## 🥇 Yutori — AI Browser Agents + SLB Data

[Yutori](https://yutori.com) builds the most accurate browser-use AI agents available.
SLB provides the data layer. Together: **your agent finds any U.S. business and acts on it.**

### Why This Combo Works
Yutori agents browse, click, and fill forms on real websites.
SLB tells them WHERE to go — 6.4M businesses with addresses, phones, websites, and categories.

Agent finds target → SLB provides data → Yutori agent visits their website → extracts/acts.

### Recipe: "Find businesses without websites, then research them"

```python
from yutori import YutoriClient
import requests

yutori = YutoriClient(api_key="your-key")

# Step 1: SLB finds businesses missing websites in Orlando
slb = requests.get(
    "https://support-local-businesses.com/api/v1/businesses",
    params={"zip": "32801", "category": "restaurant", "limit": 20}
).json()

no_website = [b for b in slb["results"] if not b.get("website")]

# Step 2: Yutori agent researches each one
for biz in no_website[:5]:
    result = yutori.research.run(
        query=f"Find website and social media for {biz['name']} at {biz['address']}, {biz['city']} FL"
    )
    print(f"{biz['name']}: {result.summary}")
Recipe: "Agent claims a listing on SLB"
# Yutori Browsing API navigates SLB like a real user
task = yutori.browse.run(
    url="https://support-local-businesses.com",
    instruction="Search for 'Tony's Pizza Orlando', click on the listing, click 'Claim Your Listing', fill out the form with test data"
)
print(task.status)  # completed
print(task.recording_url)  # watch the agent do it
MCP: Add Both to Your Agent
{
  "mcpServers": {
    "support-local-businesses": {
      "url": "https://support-local-businesses.com/mcp",
      "description": "Search 6.4M+ US business listings"
    },
    "yutori": {
      "command": "uvx",
      "args": ["yutori-mcp"],
      "description": "AI browser agent — browse, click, fill forms on any website"
    }
  }
}
Now your agent can search SLB for data AND use Yutori to act on it. Full autonomy.

What You Can Build With This
Scenario	SLB Does	Yutori Does
Lead enrichment	Finds businesses missing data	Visits their sites, extracts info
Competitor analysis	Lists all businesses in a category/ZIP	Browses each site for pricing/menus
Automated outreach	Identifies unclaimed listings	Navigates contact forms
Market research	Provides density data by location	Deep-dives specific businesses
QA testing	Provides test targets	Runs user-journey tests on SLB itself
Yutori is #1 on browser-use benchmarks. SLB is the largest agent-ready U.S. business directory. Better together.
