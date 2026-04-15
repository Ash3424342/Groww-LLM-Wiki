---
title: Compass MCP
date_updated: 2026-04-06
tags: [entity, system, data-platform, mcp]
---

# Compass MCP

Groww's unified data platform interface. Connects AI coding assistants (Claude Code, Cursor, Cline, VS Code) to the entire data infrastructure via Model Context Protocol.

**Built by**: Saurabh Dubey (Data Platform team)
**Status**: BETA

## What It Is

An MCP server that unifies three systems into one conversational interface:

| System | Role | Via Compass |
|--------|------|-------------|
| **DataHub** | Data catalog (metadata, lineage, ownership) | Search, schema, lineage, metadata management |
| **Superset** | Visualization (charts, dashboards) | Create/update charts, dashboards, reports |
| **Trino** | SQL engine (query execution) | `run_trino_query` — read-only, 5K rows, 600s timeout |

## Architecture

```
IDE (Claude Code / Cursor)
    ↓
Local Proxy (127.0.0.1:3100, auto-starts on login)
    ↓ (has VPN access)
Compass MCP Server (VPN endpoint)
    ↓
DataHub + Superset + Trino
```

**Proxy**: macOS LaunchAgent. Required because desktop apps can't reach VPN endpoints directly.

## 80+ Tools (12 Categories)

| Category | Count | Examples |
|----------|-------|---------|
| Analytics Skills | 16 | Domain-specific knowledge packages |
| SQL Execution | 5 | Trino queries, Superset SQL, SQL Lab |
| Charts | 8 | Create, preview, update, get data |
| Dashboards | 6 | Create, add charts, list, update |
| Data Discovery | 6 | Search, schema fields, entity details |
| Metadata | 10 | Descriptions, owners, tags, domains |
| Lineage | 1 | Upstream/downstream with configurable depth |
| Reports & Alerts | 4 | Scheduled reports, data alerts |
| Datasets | 4 | Create, get info, list, delete |
| Databases | 3 | List databases, schemas, tables |
| Tags (Superset) | 4 | Create, add to object, list, delete |
| Identity & Admin | 4 | Identity, MCP token, instance info |

## Two SQL Engines

| Engine | Tool | Best For | Limits |
|--------|------|---------|--------|
| Trino (Direct) | `run_trino_query` | Ad-hoc analysis on data lake | Read-only, 5K rows, 600s timeout |
| Superset SQL | `superset > execute_sql` | Queries on Superset-connected DBs | Read-only, 10K rows, 300s timeout |

## Safety Guardrails

- **Read-only**: Only SELECT statements
- **Partition enforcement**: Skills ensure partition filters on billion-row tables
- **Timeout protection**: Default 120s, max 600s
- **Row limits**: Default 500, max 5,000
- **Stale table prevention**: Skills warn against deprecated tables
- **Date range capping**: Skills add upper-bound date filters

## Schema Directory

| Schema | Tables | Domain |
|--------|--------|--------|
| `platform_iceberg.core_invest` | Stocks, F&O, MF, MTF, Commodity, 915 | Trading & Investment |
| `platform_iceberg.core_bgv` | Growth, Onboarding, UPI, Engagement, H&S | User Lifecycle & Operations |
| `platform_iceberg.dwh_invest` | MF enriched | MF Data Warehouse |
| `platform_iceberg.dump_invest` | 915 cohorts | Periodic Snapshots |
| `platform_iceberg.ems` | Event data (Iceberg) | Raw Events |
| `platform_dp_pinot.default` | Event data (Pinot — sampled!) | Sampled Events (fast, approximate) |

## Biggest Tables (Must Filter!)

| Table | Rows | Skill | Must Filter? |
|-------|------|-------|-------------|
| `user_product_txn_master_fact` | **8.3B** | User Master | `order_date` |
| `fact_transaction_stocks` | **7.1B** | Stocks | `order_date` |
| `fno_order_master` | **3.8B** | F&O | `pt` |
| `core_stocks_order` | **2.5B** | Stocks | `order_date` |
| `engagement_session_indepth` | **57B total** | Engagement | `session_date` (1 day only!) |
| `engagement_pn_narad_master` | **250M/day** | Engagement | `event_date` |

## Stale Tables (Do Not Use)

| Table | Last Data | Use Instead |
|-------|----------|-------------|
| `stocks_order` | Oct 2025 | `core_stocks_order` |
| `invest_user_fid_info` | Jun 2024 | `fact_onboarding_invest` FID columns |
| `daily_onb_conversions` | EMPTY | `daily_onboarding_and_fid` |
| `hns_freshchat_tickets_master_trino` | BROKEN | Do not use |
| `fno_usersegmentation_monthly` | Oct 2025 | Use order tables |
| `mtf_transactions_v2` | Nov 2024 | `aay_mtf_fid_agg` |

## Universal Join Key

All user-level tables: `user_account_id` (format: `ACC<digits>`)

## Related

- [[compass-analytics-skills]] — the 16 domain skills
- [[superset]] — visualization layer Compass controls
- [[narad]] — Engagement skill queries NARAD's `engagement_pn_narad_master`
- [[bigquery]] — ⚠️ Compass uses Trino on platform_iceberg, not BigQuery directly
