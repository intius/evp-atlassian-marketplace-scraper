# Atlassian Marketplace Scraper & Unofficial API (Python, Node.js, MCP)

[Run Atlassian Marketplace Scraper on Apify](https://apify.com/evpp/atlassian-marketplace) to export Atlassian Marketplace data as clean JSON, CSV, Excel, or an API feed. This repository is a developer quick-start kit with working Python and Node.js clients, an MCP configuration, a real sample dataset, and an n8n automation template.

[![Run on Apify](https://img.shields.io/badge/Run%20on-Apify-orange)](https://apify.com/evpp/atlassian-marketplace)

[Open the documentation and crawlable sample explorer](https://intius.github.io/evp-labs-data-extractors/actors/atlassian-marketplace/) for quick inputs, integration links, real sample rows, and ready-made task examples.

## Why use this Atlassian Marketplace scraper?

- Export Atlassian Marketplace data without building or maintaining a custom scraper
- Get flat, schema documented JSON ready for analytics, lead generation, market research, and AI agents
- Run manually, on a schedule, through the Apify API, or through MCP compatible AI tools
- Use the included 25+ row sample dataset to prototype before running the live Actor

Built for Atlassian Marketplace vendors doing competitive intel, investors analyzing ecosystem, IT teams comparing apps.

## Quick start on Apify

Open [https://apify.com/evpp/atlassian-marketplace](https://apify.com/evpp/atlassian-marketplace) and use this input:

```json
{
  "searchQuery": "test management",
  "hosting": "cloud",
  "cost": "any",
  "includeDetails": true,
  "maxItems": 15
}
```

## Python

```bash
pip install -r requirements.txt
export APIFY_TOKEN=your_apify_token
python python/run.py
```

On Windows PowerShell, use `$env:APIFY_TOKEN="your_apify_token"` instead of `export`.

## Node.js

```bash
npm install
export APIFY_TOKEN=your_apify_token
node node/run.mjs
```

## MCP and AI agents

Add the hosted Apify MCP server from `mcp-config.json` to your MCP client:

```json
{
  "mcpServers": {
    "apify": {
      "type": "http",
      "url": "https://mcp.apify.com/?tools=evpp/atlassian-marketplace"
    }
  }
}
```

Then ask your agent to run `evpp/atlassian-marketplace`, inspect the output schema, or export the latest dataset. The direct MCP URL is `https://mcp.apify.com/?tools=evpp/atlassian-marketplace`.

## n8n automation

Import `n8n-workflow.json` into n8n, select your Apify credential, replace the webhook placeholder, and activate the schedule. The workflow runs the Actor every morning and posts fresh dataset items to your webhook.

## Output schema

| Field | Type | Description |
|---|---|---|
| `name` | string | Display name of the Marketplace app |
| `addonKey` | string | Unique app key used by the Marketplace API |
| `addonId` | string | Numeric Marketplace listing ID of the app |
| `url` | string | Public URL of the app's Marketplace listing |
| `tagline` | string | Short marketing tagline of the app |
| `summary` | string | Short description of the app, trimmed to about 400 characters |
| `vendorName` | string | Name of the app vendor |
| `vendorUrl` | string | URL of the vendor's Marketplace page |
| `categories` | string[] | Marketplace categories the app is listed under |
| `installs` | number | Total installs reported by the Marketplace distribution stats (omitted when the API does not expose it) |
| `downloads` | number | Total downloads reported by the Marketplace distribution stats |
| `rating` | number | Average review rating from 1 to 4 stars |
| `reviewCount` | number | Number of user reviews for the app |
| `lastModified` | string | ISO timestamp of the last Marketplace listing update |
| `logoUrl` | string | URL of the app's logo image |
| `hosting` | string[] | Hosting/deployment options the latest app version supports (cloud, datacenter, server, connect) |
| `pricingModel` | string | Payment model of the latest version, as reported by the API (for example atlassian, free, external) |
| `version` | string | Latest published version number of the app |
| `versionReleaseDate` | string | Release date of the latest version |
| `cloudFortified` | boolean | Whether the app holds the Cloud Fortified program status |
| `storesPersonalData` | boolean | Whether the vendor declares the app stores personal data |
| `supportUrl` | string | Vendor support portal or issue tracker URL |
| `privacyUrl` | string | Vendor privacy policy URL |
| `keywords` | string[] | Keyword tags assigned to the app listing |

## Real sample output

The first sanitized row from the included sample dataset:

```json
{
  "name": "Xray - Test Management for Jira",
  "addonKey": "com.xpandit.plugins.xray",
  "addonId": "1211769",
  "url": "https://marketplace.atlassian.com/apps/1211769/xray-test-management-for-jira",
  "tagline": "Jira-native Test Management. Plan, track, and release with confidence across DevOps workflows, powered by AI",
  "summary": "Complete your DevOps workflow with a Jira-native quality hub delivering visibility, traceability, and control across the SDLC, so teams can release the highest-quality software faster, with confidence.",
  "vendorName": "Xblend",
  "vendorUrl": "https://marketplace.atlassian.com/vendors/31085/xblend",
  "categories": [
    "Testing & QA",
    "Custom fields",
    "Dashboard gadgets",
    "Jira Software",
    "Jira Service Desk"
  ],
  "installs": 25108,
  "downloads": 378786,
  "rating": 4.3,
  "reviewCount": 555,
  "lastModified": "2026-11-23T18:28:38.130148700Z",
  "logoUrl": "https://marketplace.atlassian.com/product-listing/files/b45befef-64f0-4741-ba20-efcbb0d5246f?width=72&height=72",
  "hosting": [
    "cloud"
  ],
  "cloudFortified": true,
  "storesPersonalData": false,
  "supportUrl": "https://xraysupport.getxray.app",
  "privacyUrl": "https://www.sembi.com/legal/sembi-privacypolicy/",
  "keywords": [
    "Agile Methodology",
    "CI/CD",
    "Testing & QA",
    "Release Management"
  ],
  "version": "17.4.0",
  "pricingModel": "atlassian",
  "versionReleaseDate": "2026-11-24"
}
```

## Files in this kit

| File | Purpose |
|---|---|
| `python/run.py` | Working Python Apify API example |
| `node/run.mjs` | Working Node.js Apify API example |
| `mcp-config.json` | MCP server configuration for AI agents |
| `sample-output.json` | First five sanitized sample rows |
| `dataset-snapshot.csv` | 25+ row evaluation snapshot |
| `DATASET_CARD.md` | Dataset documentation and provenance |
| `n8n-workflow.json` | Scheduled n8n automation template |

## Fresh data

This repository contains a static evaluation sample. For current data, run the live Actor: https://apify.com/evpp/atlassian-marketplace

## Responsible use

The Actor reads public data from `marketplace.atlassian.com`. Review the source site's terms and applicable privacy rules before production use.
