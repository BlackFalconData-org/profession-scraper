# Profession.hu Job Scraper

Extract structured data from [profession.hu](https://profession.hu) — job listings from profession.hu — Hungary's largest job portal. Extract title, company, salary, location, requirements, and full description.

**[Profession.hu Job Scraper on Apify →](https://apify.com/blackfalcondata/profession-scraper)**

---

## Key features




**Search with filters** — Search by keyword and location. Filter by employment type, remote / hybrid, experience level, and more.

**Detail enrichment** — Fetch full job descriptions, salary data, direct apply URLs for each listing.

**Incremental mode** — Only get new or changed listings since your last run. Content hash per listing — no duplicates, no re-processing.

---

## Use cases




**Data pipeline automation**
Integrate with your ETL pipeline to collect structured listings from profession.hu on a schedule. Export to CSV, JSON, or directly to your database. Use compact mode to control output size.

**Market research**
Monitor listings, track trends, and analyze market dynamics with structured, deduplicated data from profession.hu.

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

---

## Related products by Black Falcon Data




- [StepStone Scraper](https://github.com/BlackFalconData-org/stepstone-scraper) — Job listings from 18 European portals
- [Indeed Job Scraper](https://github.com/BlackFalconData-org/indeed-job-scraper) — Indeed job listings with salary data
- [Glassdoor Job Scraper](https://github.com/BlackFalconData-org/glassdoor-job-scraper) — Glassdoor listings with company ratings

---

*Last updated: 2026 03*
