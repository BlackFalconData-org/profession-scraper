# Profession.hu Job Scraper

Extract structured data from [profession.hu](https://profession.hu) — job listings from profession.hu — Hungary's largest job portal. Extract title, company, salary, location, requirements, and full description.

**[Profession.hu Job Scraper on Apify →](https://apify.com/blackfalcondata/profession-scraper?fpr=1h3gvi)**


## 🚀 How to use this actor

> ### 💚 $5 free Apify credits — every month
> No credit card required. No commitment. Cancel anytime.

### 👉 [Sign up free on Apify →](https://console.apify.com/sign-up?fpr=1h3gvi)

1. **Click sign up** — pick GitHub, Google, or email; takes ~30 seconds
2. **Open this actor** — input is pre-filled with a working example
3. **Click Start** — export results as JSON, CSV, or Excel

Your **$5 monthly platform credit** is enough to run this actor right away — and again every month — scraping typically several hundred to several thousand results per run, depending on your input.



## 🚀 How to use this actor

> ### 💚 $5 free Apify credits — every month
> No credit card required. No commitment. Cancel anytime.

### 👉 [Sign up free on Apify →](https://console.apify.com/sign-up?fpr=1h3gvi)

1. **Click sign up** — pick GitHub, Google, or email; takes ~30 seconds
2. **Open this actor** — input is pre-filled with a working example
3. **Click Start** — export results as JSON, CSV, or Excel

Your **$5 monthly platform credit** is enough to run this actor right away — and again every month — scraping typically several hundred to several thousand results per run, depending on your input.


---

## Key features








**Search with filters** — Search by keyword and location. Filter by 📁 category, 💼 employment type, remote / hybrid, and more.

**Detail enrichment** — Fetch full job descriptions, salary data, contact information for each listing.

**Incremental mode** — Only get new or changed listings since your last run. Content hash per listing — no duplicates, no re-processing.

**Change classification** — Track unchanged, expired, cross-run repost detection across runs. Build audit trails of how listings evolve over time.

**Compact output** — Emit core fields only (AI-agent / MCP-friendly). Keeps response size small for LLM workflows.

**Description truncation** — Cap description length per listing to control output size and cost.

**Result cap** — Stop after N listings (up to 10.000). Set to 0 for the full catalog.

**Export anywhere** — Download as JSON, CSV, or Excel. Stream via Apify API, webhooks, or integrations with Make, Zapier, Airbyte, Keboola.

**Structured data** — Every listing returns the same schema with consistent field naming. All fields always present — `null` when unavailable, never omitted.

---

## Use cases








**Data pipeline automation**
Integrate with your ETL pipeline to collect structured listings from profession.hu on a schedule. Export to CSV, JSON, or directly to your database. Use compact mode to control output size.

**Market research**
Monitor listings, track trends, and analyze market dynamics with structured, deduplicated data from profession.hu.

**Change monitoring**
Run daily or hourly in incremental mode to capture only new, updated, or expired listings. Perfect for price-tracking, churn analysis, and alerting pipelines.

**Compensation benchmarking**
Aggregate salary ranges across roles, industries, and locations on profession.hu to inform pricing decisions, hiring plans, or candidate negotiations.

**AI / LLM training data**
Structured JSON per listing is ready for RAG pipelines, embeddings, and agent workflows. Compact mode trims tokens for LLM context windows.

---

## Quick start

```json
{
  "query": "developer",
  "location": "Budapest",
  "maxResults": 10,
  "includeDetails": true
}
```

---

## Input parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `query` | string | — | Job search keywords (e.g. "developer", "marketing", "SAP"). |
| `location` | string | — | City or county name (e.g. "Budapest", "Győr-Moson-Sopron"). Leave empty for all of Hungary. |
| `locationId` | integer | — | Direct numeric location ID for profession.hu. Overrides the Location field when set. Find IDs from profession.hu URL segments. |
| `category` | string | — | Job category slug to filter by (e.g. "informatika-telekommunikacio"). Maps to the category segment in profession.hu URLs. |
| `employmentType` | enum | — | Filter by employment type. |
| `remoteFilter` | enum | — | Filter by work arrangement. |
| `experienceLevel` | enum | — | Filter by required experience. |
| `maxResults` | integer | `50` | Maximum number of job listings to return. 0 = unlimited. |
| `includeDetails` | boolean | `true` | Fetch each job's detail page for full description, skills, benefits, and more. Slower but much richer data. |
| `descriptionMaxLength` | integer | `0` | Truncate description HTML to N characters. 0 = no truncation. |
| `compact` | boolean | `false` | Return only core fields (jobId, title, company, location, salary, employment type, URL, posted date). Ideal for AI-agent/MCP workflows. |
| `incrementalMode` | boolean | `false` | Only output jobs that are new or changed since the previous run. |
| `stateKey` | string | — | Unique key for incremental state. Use different keys for different search queries. |

---

## FAQ

<!-- WRITE: 4-6 Q&A pairs relevant to this product -->

**Is it legal to scrape profession.hu?**
Web scraping of publicly available data is generally legal. This actor only accesses publicly visible information. Always check the target site's terms of service for your specific use case.

**How does incremental mode work?**
Each listing gets a content hash. On subsequent runs, only new or changed listings are emitted — saving time, compute, and storage.

---

## Known limitations

<!-- WRITE: 4-6 honest limitations -->

- <!-- WRITE: limitation 1 -->
- <!-- WRITE: limitation 2 -->


## Output fields

Every listing returns the same 37-field schema. Missing values are `null` — never omitted.

- `jobId`
- `numericId`
- `title`
- `url`
- `portalUrl`
- `companyName`
- `companyId`
- `companyLogoUrl`
- `companyProfileUrl`
- `companyRating`
- `location`
- `locationDetail`
- `addressRegion`
- `postalCode`
- `country`
- `category`
- `subcategory`
- `occupationalCategory`
- `employmentType`
- `experienceRequired`
- `educationRequirements`
- `workHours`
- `remoteType`
- `salaryText`
- `benefits`
- `requirements`
- `description`
- `responsibilities`
- `skills`
- `techStack`
- `taskSnippet`
- `postedAt`
- `validThrough`
- `applyUrl`
- `applicationType`
- `scrapedAt`
- `source`


## Sample output

One object per listing. Here is a real example from a production run:

```json
{
  "jobId": "006ad039ac3a206538ed78e15079768ae56d754c1e804b08e5710fdf3fc710ca",
  "numericId": 2849228,
  "title": "Java Developer",
  "url": "https://www.profession.hu/allas/java-developer-shiwaforce-com-zrt-budapest-2849228",
  "portalUrl": "https://www.profession.hu/allas/java-developer-shiwaforce-com-zrt-budapest-2849228/optimum",
  "companyName": "ShiwaForce.com Zrt",
  "companyId": 29402,
  "companyLogoUrl": "https://www.profession.hu/images/logos/2/9/29402_1728031517.png",
  "companyProfileUrl": "https://www.profession.huhttps://www.profession.hu/allasok/shiwaforce-com-zrt/1,0,0,0,0,0,0,0,0,0,29402",
  "companyRating": null,
  "location": "Hibrid • Budapest XII.kerület",
  "locationDetail": "Hibrid • Budapest XII.kerület"
}
```

*Truncated — full records contain 37 fields. See Output fields for the complete schema.*


**[Try Profession.hu Job Scraper now — $5 free credit, no credit card →](https://apify.com/blackfalcondata/profession-scraper?fpr=1h3gvi)**


## Pricing

Pay only for what you extract. No subscription required — Apify's free $5 credit covers thousands of results.

| Event | Price (USD) |
| --- | --- |
| Actor Start | $0.01 |
| Result | $0.002 |

See the [actor on Apify](https://apify.com/blackfalcondata/profession-scraper?fpr=1h3gvi) for current pricing.

---

## Related products by Black Falcon Data








- [StepStone Scraper](https://apify.com/blackfalcondata/stepstone-scraper?fpr=1h3gvi) — Job listings from 18 European portals
- [Indeed Job Scraper](https://apify.com/blackfalcondata/indeed-job-scraper?fpr=1h3gvi) — Indeed job listings with salary data
- [LinkedIn Jobs Scraper](https://apify.com/blackfalcondata/linkedin-jobs-scraper?fpr=1h3gvi) — World's largest professional network — global job listings, no login required
- [Glassdoor Job Scraper](https://apify.com/blackfalcondata/glassdoor-job-scraper?fpr=1h3gvi) — Glassdoor listings with company ratings
- [Arbeitsagentur Scraper](https://apify.com/blackfalcondata/arbeitsagentur-scraper?fpr=1h3gvi) — Germany's official job portal (1M+ listings)
- [SEEK Scraper](https://apify.com/blackfalcondata/seek-scraper?fpr=1h3gvi) — Australia & NZ's largest job board

---


## About Black Falcon Data

Black Falcon Data builds production-grade web scrapers for job boards and marketplace data. Browse our full actor catalog at [www.blackfalcondata.com](https://www.blackfalcondata.com).

---

## Getting started with Apify

New to Apify? [Create a free account with $5 credit](https://console.apify.com/sign-up?fpr=1h3gvi) — no credit card required.

1. [Sign up free](https://console.apify.com/sign-up?fpr=1h3gvi) — $5 credit included
2. Open the actor and paste your input
3. Click Start — results download as JSON, CSV, or Excel

Need more volume? [See pricing](https://apify.com/pricing?fpr=1h3gvi).

---

---

*Last updated: 2026 03*
