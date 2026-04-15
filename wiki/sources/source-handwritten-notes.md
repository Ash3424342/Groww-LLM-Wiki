---
title: "Source: Handwritten Task Notes (2 images)"
source: raw/assets/my-full-task.jpg, raw/assets/content-engine.jpg
date_ingested: 2026-04-06
tags: [task, architecture, handwritten, content-engine]
---

# Source: Handwritten Task Notes

## Summary

Two handwritten notebook pages capturing Ashish's full task scope and Content Engine architecture. These are the original vision docs.

## Image 1: My Full Task (`raw/assets/my-full-task.jpg`)

### Compass → Skillsets → Pod mapping

```
MCP Compass → Skillsets → pod branches:
  - OB/Act (N) — Nikhil
  - Investing Pool (N/H) — Nikhil/Himanshu
  - Trading Pool (A) — Aastha
  - New Biz
  - 915 (Y) — Yash
  - W (Amit) — Wealth
  - AMC (Amit)
```

### Data flow

```
Text-to-SQL ↓
Segmentation (Audience Manager) via MCP (SQL)
  ↓
Segment ID → Comms & Pers (then)
           → Weekly WBR
           → Monthly MBR
```

### The 4-box pipeline (drawn at bottom)

```
[Analytics] → [Segmentation] → [Content] → [Campaign] → NARAD → Approve
```

### Data scale

5000 core raw tables → 25000 derived tables

## Image 2: Content Engine (`raw/assets/content-engine.jpg`)

### Content creation flow

```
UE Team ↔ Creative Team → Figma → 3rd Party → HTML/MC
  ↓
WE/NARAD
```

### Pre-defined templates

- 4 series (Commodity)
- 1, 5
- Images
- GMF/AMC
- 90 days → Emails/templates → Edit format

### What's being built (Content Manager / CM)

```
CM →
  1) Choose a template
  2) Prompt → what I'm building
  3) Images → Prompt
  4) Text → Prompt
```

This is the Content Engine: prompt-driven email assembly from templates + images + text.

## Relationships

- supports: [[project-map]] — maps these notes to actual built files
- supports: [[groww-email-system]] — Content Engine is this system
- supports: [[compass-mcp]] — Compass is the Analytics + Segmentation boxes
- related: [[activation-funnel]], [[narad]] — the pipeline these notes describe
