---
title: BigQuery (BQ)
date_updated: 2026-04-06
tags: [entity, system, data]
---
# BigQuery
Google Cloud data warehouse. Primary data source for Audience Manager segment pipeline.
## Pipeline
```
BigQuery (daily batch) → Audience Manager (segments) → WebEngage (campaigns)
```
## ⚠️ Note on Compass
[[compass-mcp]] queries data via **Trino on platform_iceberg schemas**, not BigQuery directly. BQ still feeds the AM→WE segment pipeline but Compass bypasses it for analytics queries.
## Related
- [[audience-manager]] — downstream consumer
- [[compass-mcp]] — uses Trino, not BQ
- [[source-data-architecture]] — BQ table details
