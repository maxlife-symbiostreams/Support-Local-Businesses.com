---

## 📄 `AGENTS.md`


# 🤖 AI Agent Integration Guide

Support Local Businesses is built for agent-to-agent commerce. Here's how to plug in.

---

## Discovery Endpoints

| URL | Protocol | Purpose |
|-----|----------|---------|
| [`/llms.txt`](https://support-local-businesses.com/llms.txt) | LLMs.txt | Natural-language site description for LLMs |
| [`/openapi.json`](https://support-local-businesses.com/openapi.json) | OpenAPI 3.0 | Machine-readable API spec — import into any agent framework |
| [`/.well-known/agent.json`](https://support-local-businesses.com/.well-known/agent.json) | Agent Card | Identity, capabilities, supported protocols |
| [`/mcp`](https://support-local-businesses.com/mcp) | MCP | Model Context Protocol server — works with Claude, Cursor, Windsurf, etc. |
| [`/.well-known/pay`](https://support-local-businesses.com/.well-known/pay) | x402 | Payment discovery for agent-to-agent transactions on Base L2 |

---

## MCP Integration (Claude, Cursor, etc.)

Add SLB as a tool source in your MCP config:

```json
{
  "mcpServers": {
    "support-local-businesses": {
      "url": "https://support-local-businesses.com/mcp",
      "description": "Search 6.4M+ US business listings"
    }
  }
}
Your agent can then query businesses conversationally:

"Find me 5 plumbers in Miami ZIP 33130"

OpenAPI Tool Use
Import the spec directly:

import requests

spec = requests.get("https://support-local-businesses.com/openapi.json").json()
# Feed to your agent framework (LangChain, CrewAI, AutoGPT, etc.)
Agent-to-Agent Payments (x402)
SLB accepts x402 micropayments on Base L2 for premium API access. No API keys needed — your agent pays per-request with crypto.

Flow:

Agent calls API → gets 402 Payment Required
Agent reads payment details from response header
Agent sends Base L2 transaction
API returns enriched data
Zero setup. Zero subscriptions. Pay for what you use.

Use Cases for Agents
Lead generation agents — find businesses by category + location for outreach
Market research agents — analyze business density by ZIP/category
Local SEO agents — pull competitor listings for a given area
Sales agents — identify unclaimed businesses for SaaS prospecting
Data enrichment agents — cross-reference with your own datasets
Chatbot
SLB has a built-in AI chatbot on every page. Ask it anything about local businesses, categories, or the platform.

Questions?
Visit support-local-businesses.com or inspect the agent card for contact info.
