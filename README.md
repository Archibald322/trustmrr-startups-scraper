# TrustMRR SaaS Startups & Revenue Scraper

[![Apify Actor](https://img.shields.io/badge/Apify-Actor%20Store-orange?logo=apify)](https://apify.com/moneygain/trustmrr-startups-scraper)
[![Python Version](https://img.shields.io/badge/Python-3.10%20%7C%203.11%20%7C%203.12-blue?logo=python)](https://github.com/Archibald322/trustmrr-startups-scraper)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> **Live Apify Store Actor:** [https://apify.com/moneygain/trustmrr-startups-scraper](https://apify.com/moneygain/trustmrr-startups-scraper)

This repository provides an open-source Python runner and documentation for **[TrustMRR SaaS Startups & Revenue Scraper](https://apify.com/moneygain/trustmrr-startups-scraper)**.

---

## ⚡ Quickstart

### Option 1: Run in Cloud (No Code)
Launch directly from your browser via the Apify Store console:
👉 **[Open TrustMRR SaaS Startups & Revenue Scraper on Apify Store](https://apify.com/moneygain/trustmrr-startups-scraper)**

### Option 2: Run via Python SDK
```bash
git clone https://github.com/Archibald322/trustmrr-startups-scraper.git
cd trustmrr-startups-scraper
pip install -r requirements.txt
export APIFY_TOKEN="your_apify_token_here"
python run.py
```

---

# 🚀 TrustMRR SaaS Startups & Verified Revenue Scraper

**Scrape TrustMRR SaaS startup data to JSON, CSV, or Excel in seconds without browser overhead.** Extract real-time, Stripe-verified SaaS financial metrics, Monthly Recurring Revenue (MRR), 30-day revenue, all-time revenue, active paying subscribers, growth rates, direct company websites, and verified founder Twitter/X contacts from **TrustMRR.com** — the premier marketplace for buying, selling, and tracking transparent software startups.

Designed for venture capital analysts, private equity scouts, M&A deal sourcing teams, B2B lead generation specialists, and autonomous AI agents. Powered by lightweight HTTP requests with **zero browser overhead** and **100% Pay-Per-Event (PPE) pricing** — you only pay for verified startup records delivered.

---

## ⚡ Speed & Value Comparison

| Feature | Our Lightweight TrustMRR Scraper | Heavy Browser Scrapers (Playwright / Puppeteer) |
|---|---|---|
| **Memory Consumption** | **128 MB – 256 MB** | 2 GB – 4 GB |
| **Startup Cost** | **$0.00 (Zero Start Fee)** | $0.05 – $0.10 per run |
| **Extraction Speed** | **0.2s – 0.5s per startup** | 8s – 15s per page |
| **Pricing Model** | **Pay-Per-Event ($0.005 / startup)** | Expensive Monthly Flat Rate ($30–$50/mo) |
| **Data Enrichment** | **Clean root domains + Founder X handles** | Raw HTML / basic uncleaned card data |
| **AI & MCP Ready** | **Instant clean JSON for Claude / Cursor MCP** | Bulky payloads requiring heavy LLM cleanup |

---

## 📦 Sample JSON Output

```json
{
  "id": "postiz",
  "name": "Postiz",
  "slug": "postiz",
  "profileUrl": "https://trustmrr.com/startup/postiz",
  "directWebsite": "https://postiz.com",
  "websiteDomain": "postiz.com",
  "description": "Postiz is the ultimate agentic social media scheduler tool",
  "mrr": 430896,
  "revenue30Days": 472378,
  "allTimeRevenue": 1946080,
  "activeSubscriptions": 12674,
  "momGrowthPercent": 52.0,
  "rank": 62,
  "categories": [
    "Social Media",
    "AI",
    "Content Creation",
    "Saas",
    "Marketing"
  ],
  "founderName": "Nevo David",
  "founderHandle": "wickedguro",
  "founderTwitterUrl": "https://x.com/wickedguro",
  "scrapedAt": "2026-11-17T14:45:00.000000+00:00"
}
```

---

## 🎯 Use Cases & Business Value

- **Venture Capital & M&A Deal Sourcing**: Discover high-growth bootstrapped and indie SaaS startups before they hit public brokerages or funding rounds. Filter by Stripe-verified MRR ($1,000 to $500,000+).
- **Competitor Benchmarking**: Benchmark real verified revenue, MoM growth rates, and paying subscriber counts across AI, Developer Tools, Marketing, and FinTech categories.
- **Direct Founder Outreach**: Extract clean company domains (`websiteDomain`) and verified founder Twitter/X profiles (`founderTwitterUrl`) for high-conversion B2B partnership and acquisition outreach.
- **Market Sizing & Pricing Research**: Analyze subscription pricing models, active subscriber volumes, and revenue multiples across 12,000+ live SaaS products.

---

## ⚙️ Input Parameters

| Parameter | Type | Default | Description |
|---|---|---|---|
| `mode` | String | `"top_leaderboard"` | Scrape mode: `top_leaderboard` (fastest & highest MRR), `category`, `sitemap` (12,000+ startups), or `custom_urls`. |
| `category` | String | `"ai"` | Category niche if mode is `category` (`ai`, `saas`, `developer-tools`, `marketing`, `ecommerce`, `fintech`, `productivity`, etc.). |
| `startUrls` | Array | `["https://trustmrr.com/startup/postiz"]` | Custom TrustMRR startup URLs to scrape. |
| `minMrr` | Number | `0` | Minimum Stripe-verified Monthly Recurring Revenue ($). Filter for startups above a specific revenue threshold (e.g. `5000`). |
| `maxItems` | Integer | `10` | Maximum number of verified startup records to push to the dataset (Prefilled for instant 5-second test runs). |
| `proxyConfiguration` | Object | `{"useApifyProxy": false}` | Optional proxy settings. Direct connection works with 100% reliability at maximum speed. |

---

## 🤖 Integrate with AI Agents & No-Code Platforms

### 1. Claude Desktop & Cursor via Apify MCP Server
Connect this actor directly to Cursor, Claude Desktop, Windsurf, or LangChain agents using the official Apify MCP Server:

```json
{
  "mcpServers": {
    "apify": {
      "command": "npx",
      "args": ["-y", "@apify/mcp-server"],
      "env": {
        "APIFY_TOKEN": "YOUR_APIFY_API_TOKEN"
      }
    }
  }
}
```
*Prompt example:*
> *"Find 10 AI SaaS startups on TrustMRR with at least $10,000 MRR and give me their direct website, active subscriptions, and founder contact info using trustmrr-startups-scraper."*

### 2. n8n Automation Workflows
1. Add an **Apify Node** or **HTTP Request Node** in your n8n workflow.
2. Select `Run an Actor` with Actor ID: `moneygain/trustmrr-startups-scraper`.
3. Pipe the resulting JSON dataset directly into Airtable, HubSpot, Google Sheets, or Slack.

### 3. Make.com (Integromat)
1. Add the **Apify Module** ➔ `Run Actor and get dataset items`.
2. Map `directWebsite`, `mrr`, and `founderTwitterUrl` into your CRM (Salesforce, Notion, Pipedrive).

### 4. Clay.com Enrichment
1. Use the **Apify Integration** inside Clay.
2. Enrich target domain lists by passing root company domains into TrustMRR to pull verified ARR/MRR metrics.

### 5. Python SDK Integration
```python
from apify_client import ApifyClient

client = ApifyClient("YOUR_APIFY_API_TOKEN")
run_input = {
    "mode": "top_leaderboard",
    "minMrr": 5000,
    "maxItems": 25
}
run = client.actor("moneygain/trustmrr-startups-scraper").call(run_input=run_input)

for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(f"{item['name']} | MRR: ${item['mrr']} | Website: {item['directWebsite']}")
```

---

## ❓ Frequently Asked Questions (SEO FAQ)

### Q1: Is it legal to scrape data from TrustMRR?
**Yes.** This scraper extracts only publicly available directory listings, verified Stripe revenue milestones, and public founder social handles. It does not access private account dashboards, passwords, or personal payment card details. Always comply with local regulations (such as GDPR / CCPA) when processing founder contact data.

### Q2: How much does it cost to scrape 1,000 startups?
Under our **Pay-Per-Event (PPE)** pricing model, you only pay **$0.005 per verified startup record**, meaning 1,000 enriched startups cost exactly **$5.00**. There are zero startup fees, zero monthly subscription mandates, and Bronze/Silver/Gold/Diamond Apify subscribers receive automatic discounts of up to 20% ($4.00 per 1,000).

### Q3: Can I export TrustMRR data to Excel, CSV, or Google Sheets?
**Yes.** Apify provides 1-click export options in JSON, CSV, XML, Excel (.xlsx), and HTML table formats. You can also sync datasets automatically to Google Sheets via Apify Integrations or webhooks.

### Q4: Do I need residential proxies to scrape TrustMRR?
**No.** TrustMRR allows fast direct HTTP connections. Our scraper utilizes modern Chrome TLS fingerprint impersonation (`curl_cffi`), eliminating the need for expensive proxy bandwidth fees while maintaining 100% extraction reliability.

### Q5: How often is the revenue and MRR data updated?
TrustMRR synchronizes Stripe metrics directly from connected startup founders in near real-time. Running this scraper on a recurring schedule (e.g. weekly or monthly via Apify Tasks) enables you to track month-over-month growth trajectories and emerging bootstrapped winners dynamically.

---

## 🔗 Explore More High-Speed B2B Scrapers & Enrichers by Our Team

Supercharge your data pipelines, sales outreach, and AI agents with our suite of lightweight, Pay-Per-Event scrapers:

| Scraper | Segment / Target | Key Value | Store Link |
|---|---|---|---|
| **TrustMRR SaaS Startups Scraper** | SaaS Revenue & M&A Data | Stripe-verified MRR, 30d revenue, active subscriptions & founder contacts | [Open on Apify Store](https://apify.com/moneygain/trustmrr-startups-scraper) |
| **Ashby ATS Tech Jobs Scraper** | Next-Gen ATS Career Feeds | Direct ATS API extraction, salaries, departments & remote flags | [Open on Apify Store](https://apify.com/moneygain/ashby-jobs-scraper) |
| **Clutch B2B Agencies Scraper** | B2B Agencies & IT Services | Decoded direct websites, review ratings, hourly rates & service focus | [Open on Apify Store](https://apify.com/moneygain/clutch-agencies-scraper) |
| **Wellfound Startup Talent Scraper** | AI & Tech Startup Jobs | Startup jobs, compensation ranges, equity & tech stack tags | [Open on Apify Store](https://apify.com/moneygain/wellfound-jobs-scraper) |
| **TheProtocol.it IT Careers Scraper** | IT Salaries & Vacancies | Verified salary brackets, tech requirements & seniority levels | [Open on Apify Store](https://apify.com/moneygain/theprotocol-scraper) |
| **Bulldogjob Tech Recruitment Scraper** | Tech Recruitment Feeds | B2B/Employment rates, tech tags & recruiter contacts | [Open on Apify Store](https://apify.com/moneygain/bulldogjob-scraper) |
