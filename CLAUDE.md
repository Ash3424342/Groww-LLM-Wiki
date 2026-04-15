# Groww LLM Knowledge Base

> Pattern: [Karpathy's LLM Wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)
> "The LLM is the programmer; Obsidian is the IDE; the wiki is the codebase."

## What This Is

An LLM-maintained wiki that **compiles** raw sources into a persistent, interlinked knowledge base — not RAG. Knowledge is built up once and kept current, not re-derived on every query. The wiki is a compounding artifact: cross-references are already there, contradictions already flagged, synthesis already reflects everything ingested.

**You** curate sources, direct analysis, ask questions, think about what it means.
**The LLM** does summarizing, cross-referencing, filing, bookkeeping, and maintenance.

## Architecture

```
Groww-LLM-Wiki/
├── raw/                        # IMMUTABLE — never modify. Source of truth.
│   ├── About the Verticle/     # Growth vertical: strategy, pods, data, ML, campaigns
│   ├── Groww-Email-System/     # Email system: blocks, recipes, tokens, architecture
│   └── assets/                 # Images from web clips (Obsidian Web Clipper)
├── wiki/                       # LLM-owned. All pages generated & maintained by LLM.
│   ├── index.md                # Content catalog — every page with one-line summary
│   ├── log.md                  # Chronological operations log (append-only)
│   ├── overview.md             # High-level synthesis of entire KB
│   ├── entities/               # People, teams, products, systems, channels
│   ├── concepts/               # Metrics, funnels, strategies, frameworks
│   ├── sources/                # One summary page per raw source
│   ├── comparisons/            # Side-by-side analyses
│   └── analyses/               # Query answers worth keeping
├── CLAUDE.md                   # This file — the schema (co-evolved by you + LLM)
└── .obsidian/                  # Obsidian config
```

## Three Layers

| Layer | Owner | Purpose |
|-------|-------|---------|
| `raw/` | You | Immutable source documents. LLM reads, never writes. |
| `wiki/` | LLM | Compiled knowledge. LLM creates, updates, cross-links, maintains. |
| `CLAUDE.md` | Both | Schema & conventions. Co-evolved as you figure out what works. |

## Domain Context

**Groww** — India's largest retail investment platform (~10Cr registered users).

This KB covers:
- **Growth Vertical**: User acquisition (0→1 / FID), retention (1→N / RID), cross-sell
- **Products**: MF, Stocks/CNC, F&O, IPO, Commodities, MTF, MIS, Pay, US Stocks, Gold, FDs
- **5 Pods**: Invest Activation, Invest RID, Invest Personalization, Trading, Other Businesses
- **6 Channels**: Push (WebEngage→FCM), WhatsApp (COSMOS), Email (Netcore), RCS/SMS, In-app Stories, Feed
- **9 ML Models**: Product Affinity, C-MAB, Campaign Affinity, Cross-sell, Retention Propensity, Widget Ranker, Instrument Affinity, Rf Score, and more
- **Data Stack**: NARAD (CRM), BigQuery, Audience Manager, WebEngage, Superset, COSMOS
- **Email System**: Block-based HTML email generation (tokens → blocks → recipes)

## Operations

### 1. INGEST — Processing a new source

When user adds a file to `raw/` or pastes content:

1. Read the source thoroughly
2. Discuss key takeaways with the user (don't skip this — **don't delegate understanding**)
3. Create summary in `wiki/sources/` with frontmatter:
   ```yaml
   ---
   title: Source Title
   source: raw/path/to/file.md
   date_ingested: YYYY-MM-DD
   tags: [growth, ml, campaigns]
   ---
   ```
4. Update/create entity pages in `wiki/entities/` for people, products, systems mentioned
5. Update/create concept pages in `wiki/concepts/` for metrics, strategies, frameworks
6. Add **typed links** between pages — not just `[[backlinks]]` but indicate relationship:
   - `supports: [[page]]` — new source reinforces existing knowledge
   - `contradicts: [[page]]` — new source conflicts (flag prominently)
   - `supersedes: [[page]]` — new source replaces outdated info
   - `related: [[page]]` — general connection
7. Update `wiki/index.md` — add new page with one-line summary
8. Update `wiki/overview.md` if big-picture changes
9. Append to `wiki/log.md`:
   ```
   ## [YYYY-MM-DD] ingest | Source Title
   - Summary: one line
   - Pages created: [list]
   - Pages updated: [list]
   - Contradictions: [list or "none"]
   ```

### 2. QUERY — Answering questions

1. Read `wiki/index.md` to find relevant pages
2. Read those pages + linked pages
3. If wiki is insufficient, fall back to `raw/` sources
4. Synthesize answer with `[[citations]]`
5. **File good answers back**: substantial analyses → `wiki/analyses/`, comparisons → `wiki/comparisons/`. This is how queries compound into the KB.
6. Log the query in `wiki/log.md`

### 3. LINT — Health check

When user says "lint", "health check", or "maintain":

1. Scan for:
   - Contradictions between pages
   - Stale claims superseded by newer sources
   - Orphan pages (no inbound links)
   - Concepts mentioned but lacking own page
   - Missing cross-references
   - Data gaps worth investigating
2. Report as checklist
3. Fix with user approval
4. Log in `wiki/log.md`

## Conventions

- **File names**: `lowercase-kebab-case.md` (e.g., `product-affinity-model.md`)
- **Links**: Obsidian `[[wikilinks]]` with typed relationship in context
- **Frontmatter**: YAML with `title`, `tags`, `date_ingested` (for sources), `date_updated`
- **Metrics**: Always cite number + date + source (e.g., "TTU-MAU% retention: ~73% (Jan 2024, Master Reference)")
- **Images**: Store in `raw/assets/`, reference with relative paths
- **Entities to track**: People, Products, Systems/Tools, Channels, ML Models, Campaigns
- **Log format**: Parseable — `## [YYYY-MM-DD] operation | Title` so `grep "^##" wiki/log.md | tail -10` works

## Important Principles

1. **Never modify `raw/`** — immutable source of truth
2. **Don't delegate understanding** — always discuss takeaways with user before filing. The wiki helps the user think, it doesn't replace thinking.
3. **Verify before filing** — LLM-compiled pages should be checked by the user. Flag uncertainty with `⚠️` markers.
4. **Typed relationships matter** — a link should tell you *how* things relate, not just *that* they relate
5. **Compound knowledge** — good query answers get filed back as wiki pages
6. **The wiki is never "done"** — it grows with every source and question

## Key Raw Sources

| File | What it covers |
|------|----------------|
| `raw/About the Verticle/01 - Strategy/Master Reference.md` | 850+ lines — metrics, tools, people, open questions |
| `raw/About the Verticle/02 - Pods/Pod Playbooks.md` | 650+ lines — all 8 pod strategies |
| `raw/About the Verticle/06 - Reference/Concepts & Notes.md` | 730+ lines — deep-dives for eng audience |
| `raw/About the Verticle/03 - Data & Systems/Data Architecture.md` | NARAD, BigQuery, segments, pipelines |
| `raw/About the Verticle/03 - Data & Systems/ML Systems.md` | 9 ML models with specs |
| `raw/About the Verticle/04 - Analytics/Analytics & Metrics.md` | KPI tree, dashboards, cohorts |
| `raw/About the Verticle/05 - Campaigns/Campaign Library.md` | Live campaigns and SOPs |
| `raw/About the Verticle/06 - Reference/Vocabulary.md` | A-Z glossary (✅ confirmed / ⚠️ uncertain / ❓ unknown) |
| `raw/Groww-Email-System/ARCHITECTURE.md` | Email system three-layer design |

## Session Start Checklist

1. Read this file (`CLAUDE.md`)
2. Read `wiki/index.md` — current wiki state
3. Read `wiki/project-map.md` — what's built, where code lives, what's not built yet
4. Read last 10 entries of `wiki/log.md` — recent activity
5. Ask: **ingest, query, or lint?**

## Project Map

`wiki/project-map.md` connects wiki concepts to actual files on disk. When an LLM needs to:
- Find code for a wiki concept → check project-map
- Know if something is built or just documented → check project-map
- Understand which file to edit → check project-map

Key project locations:
- **Email system code**: `/Users/ashishch/Downloads/To Build/groww-creative-mcp/`
- **Chart agent code**: `/Users/ashishch/Downloads/To Build/chart-image-agent/`
- **Claude Code skills**: `~/.claude/skills/`
- **This wiki**: `~/Desktop/Groww-LLM-Wiki/`
- **Original vault**: `~/Desktop/Groww/` (immutable source)
