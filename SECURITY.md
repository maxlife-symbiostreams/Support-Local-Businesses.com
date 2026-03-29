📄 SECURITY.md
# 🔒 Security & Data Handling

---

## Data Collection

- All business data comes from **public government records** and **free API tiers** (Google Places, Yelp Fusion, BBB)
- We do not scrape private databases, paywalled services, or personal social media
- We do not store Social Security numbers, financial data, or personal information beyond what's in public business registrations

## Payments

- **Stripe** handles all fiat transactions (blog posts, boosts, subscriptions). We never see or store card numbers.
- **x402 on Base L2** handles API micropayments. Transactions are on-chain and verifiable.

## Business Owner Data

- Magic link login — no passwords stored
- Google Sign-In available (OAuth, no password)
- Business owners control their listing data and can edit/remove it anytime

## Responsible Scraping

- BBB scraper respects rate limits (~10 requests/minute)
- Google Places and Yelp queries stay within free tier limits
- We honor robots.txt where applicable

## Reporting Issues

If you find a security vulnerability, please open a private issue or contact us through the site chatbot. We take security seriously and will respond within 48 hours.

