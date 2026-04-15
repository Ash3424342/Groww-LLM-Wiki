# Groww Knowledge Base — Master Index

> Navigation file. Find where everything lives, and where to file new data.
> Last updated: 2026-03-30

---

## File Map

| File | What it contains | Dump types that go here |
|------|-----------------|------------------------|
| **[[01 - Strategy/Master Reference]]** | People, pods, metrics definitions, channel benchmarks, tool descriptions, experiment results — the exhaustive lookup | Experiment results, new benchmarks, new people, channel data, tool updates |
| **[[02 - Pods/Pod Playbooks]]** | Everything organized by pod (Activation, RID, CNC, Personalization, Trading, Pay, Feed, Cross-sell) | Pod-level context, team changes, pod-specific experiment outcomes |
| **[[06 - Reference/Concepts & Notes]]** | Deep explanations of how things work — the "why" behind every concept | Explanations you've written or want stored, frameworks, mental models |
| **[[01 - Strategy/Overview]]** | High-level vertical overview, org structure, macro strategy | Org changes, strategy pivots, vertical-level direction |
| **[[06 - Reference/Vocabulary]]** | All acronyms, terms, tag naming conventions — A-Z with status (✅ / ⚠️ / ❓) | New acronym, unknown term, naming convention, tag format |
| **[[03 - Data & Systems/Data Architecture]]** | DB schemas, BigQuery tables, Kafka topics, data pipelines, segment registry | Raw schema dumps, table definitions, SQL, pipeline configs, ERDs |
| **[[04 - Analytics/Analytics & Metrics]]** | OKRs, metric baselines, KPI trees, dashboard guide, funnel numbers, cohort sizes | OKR doc dumps, metric updates, funnel data, dashboard schema |
| **[[05 - Campaigns/Campaign Library]]** | Active campaigns, SOPs, campaign templates, frequency caps, channel rules | Campaign briefs, SOPs, frequency rules, what's running or planned |
| **[[03 - Data & Systems/ML Systems]]** | ML model specs, feature lists, training data, inference pipelines, model performance | Model documentation, feature schemas, training configs, score distributions |
| **[[00 - Meta/PDF Processing Log]]** | Track of all 62 internal PDFs — what was read and extracted | Internal use only |

---

## How Dumps Get Filed

When you dump raw data, Claude will:

1. **Identify the type** — schema? metric baseline? campaign SOP? model spec?
2. **Extract what matters** — understand what the data means, don't just copy-paste
3. **Find the right file** — route to the table above
4. **Write in structured format** — tables, bullet points, relationships explicit
5. **Cross-reference** — if it connects to something already documented, link it

### Quick filing guide

| You dump... | Goes to |
|-------------|---------|
| BigQuery table schema / column list | Data Architecture |
| Kafka topic names / event schemas | Data Architecture |
| Pipeline diagram or data flow | Data Architecture |
| SQL query with business logic | Data Architecture (+ note which metric it computes) |
| Segment IDs / audience manager names | Data Architecture → Segment Registry |
| OKR document / quarterly goals | Analytics & Metrics |
| Funnel numbers / cohort sizes | Analytics & Metrics |
| Dashboard screenshot / metric table | Analytics & Metrics (schema only — no snapshot values) |
| Current campaign configs / what's live | Campaign Library |
| Campaign SOP / process doc | Campaign Library |
| Frequency cap rules / targeting rules | Campaign Library |
| ML model feature list / spec | ML Systems |
| Model evaluation results | ML Systems |
| Experiment design doc | Master Reference (experiment results) OR Campaign Library (SOP) |
| New person / team structure | Master Reference (People Directory) + relevant Pod Playbook |
| Tool documentation | Master Reference (Tools & Systems) + Data Architecture if technical |
| Unknown term or acronym | Vocabulary → ❓ Unknown section |

---

## Key People (Quick Ref)

| Person | Pod | Primary ownership |
|--------|-----|------------------|
| Nikhil | Invest Activation + RID | Strategy, WA channel |
| Himanshu Khandelwal | RID + Personalization | ML models, email infra |
| Amit | Invest RID (MF) | MF strategy, instrument affinity |
| Shweta | Invest Activation + RID | Campaign strategy + orchestration |
| Aishwarya | Invest Activation | Execution, RCS, SMS, Stories |
| Aastha | Trading (possibly vertical lead) | Trading pod strategy |
| Yash | Trading | 9:15 comms, WA trading, GrowwFlix |
| Samir | Trading | Trading comms execution |
| Preksha Vyas | Personalization | Product affinity model (OB/NTU) |
| Ritvik Pandey | RID (MF) + Feed | MF TTU personalization, Feed strategy |
| Hritwik Sahay | RID (CNC) | CNC alert personalization |

---

## Core Funnel (Quick Ref)

```
Registered → KYC done → FID (First Investment Done) → RID (Repeat) → TTU (Total Transacting Users)
                                                          ↓
                                                   CNTU (Cross-sell NTU — first tx in second product)
```

## Active Tools (Quick Ref)

| Tool | Role |
|------|------|
| NARAD | In-house CRM + real-time F&O pipeline (Kafka + Spark → master_tables) |
| WebEngage | Campaign orchestration + push delivery |
| BigQuery | Data warehouse |
| Audience Manager | Segment builder |
| COSMOS | Journey/automation system (WA journeys live here) |
| FCM | Push delivery (Google) |
| Netcore | Email ESP |
| Superset | Dashboards / BI |
| EMS | Event Management System (replacing WE data pipeline for C-MAB) |
