---
title: "Source: Compass MCP Documentation (3 PDFs)"
source: raw/Compass-MCP/
date_ingested: 2026-04-06
tags: [compass, mcp, data-platform, analytics-skills, trino, superset, datahub]
---

# Source: Compass MCP Documentation

## Summary

Three PDFs from the Groww Data Platform team (Saurabh Dubey) documenting Compass MCP — the unified data platform interface that connects AI coding assistants to DataHub, Superset, and Trino via MCP.

## Files

| PDF | Pages | Contents |
|-----|-------|----------|
| Compass MCP - BETA | 14 | Product overview, 9 hero features, 80+ tools, architecture, setup |
| Analytics Skills Deep Dive | 18 | All 16 skills with tables, dimensions, guardrails, example queries |
| Setup Guide | 5 | Prerequisites, proxy setup, IDE configs, troubleshooting, FAQ |

## What This Source Establishes

- **Compass MCP** is Groww's DataHub metadata platform exposed via MCP
- Unifies **DataHub** (data catalog), **Superset** (visualization), **Trino** (SQL engine)
- **16 analytics skills** = domain-specific knowledge packages (tables, columns, filters, guardrails)
- **80+ tools** across 12 categories
- Architecture: `IDE → Local Proxy (127.0.0.1:3100) → Compass MCP (VPN) → DataHub/Superset/Trino`
- Skills are loaded automatically when AI detects the domain in user's question

## Relationships

- supersedes: previous understanding of Compass (was unknown, now fully documented)
- supports: [[narad]] — Engagement skill documents the `engagement_pn_narad_master` table
- supports: [[bigquery]] — Compass queries data via Trino, not BQ directly (platform_iceberg schemas)
- supports: [[superset]] — Compass can create charts/dashboards via Superset tools
- related: [[groww-email-system]] — Engagement & Communications skill (#12) is the data layer for email/push
