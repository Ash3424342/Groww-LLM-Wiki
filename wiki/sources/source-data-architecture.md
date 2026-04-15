---
title: "Source: Data Architecture"
source: raw/About the Verticle/03 - Data & Systems/Data Architecture.md
date_ingested: 2026-04-05
tags: [data, systems, segments, pipelines]
---

# Source: Data Architecture

## Summary

Technical reference for DB schemas, BigQuery datasets, Kafka topics, data pipelines, segment registry, and infrastructure. Pre-populated from internal PDFs (2026-03-27).

## What This Source Adds

- **Segment Registry**: actual Audience Manager segment IDs with full naming convention decode
- **PA segments**: `PA_{tier}_{product}_P{rank}_{version}` — HA, MA, and mystery `lia` tier
- **NTU cross-product segments**: 9 unique IDs × 2 = 18 targeting use cases (Non-TTU, not New Transacting User)
- **TTU lifecycle segments**: `TTU_L7D_Inactive` through `TTU_CM_Inactive`, `MTU_*_ar` (at-risk)
- **ML data pipelines table**: training source, inference path, refresh cadence per model
- **FCM bottleneck**: latency increased 120% even after WebEngage scaled
- **Milestone tag system**: `D{N}_{milestone}_from_{origin}` formalized

## Relationships

- supports: [[narad]], [[audience-manager]], [[bigquery]] — technical specs for systems already in wiki
- supports: [[product-affinity]], [[c-mab]] — ML pipeline details
- related: [[source-master-reference]] — Master Reference has the business context, this has the technical implementation
