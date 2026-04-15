# Log

Chronological record of all wiki operations. Append-only.

---

## [2026-04-05] init | Wiki Bootstrap
- Summary: Initial compilation of wiki from 26 raw source files
- Pages created: overview.md, index.md, log.md
- Source summaries: 16 source pages planned (covering all raw .md files)
- Entity pages: 8 people, 10 products, 8 systems, 6 channels
- Concept pages: 8 metrics, 4 strategies, 9 ML models, 2 other
- Contradictions: none (first pass)
- Note: Wiki pages are stubs with links — will be fleshed out on first query or lint pass

## [2026-04-05] ingest | Overview.md
- Summary: Foundation doc — org structure, pod map, activation funnel, channel ownership, campaign pipeline
- Source: raw/About the Verticle/01 - Strategy/Overview.md
- Pages created:
  - wiki/sources/source-overview.md
  - wiki/concepts/activation-funnel.md
  - wiki/concepts/personalization-engine.md
  - wiki/concepts/fid.md, rid.md, ntu.md, ttu.md
  - wiki/entities/invest-activation-pod.md, invest-rid-pod.md, invest-personalization-pod.md, trading-pod.md, other-businesses-pod.md
  - wiki/entities/nikhil.md, aastha.md, shweta.md, himanshu.md, amit.md, aishwarya.md, yash.md, samir.md
- Pages updated: wiki/overview.md (already had this info from bootstrap)
- Contradictions: none
- Total: 18 new pages from first ingest

## [2026-04-05] ingest | Master Reference
- Summary: 850+ line source of truth — metrics, benchmarks, experiments, tools, people, open questions
- Source: raw/About the Verticle/01 - Strategy/Master Reference.md
- Pages created:
  - wiki/sources/source-master-reference.md
  - wiki/concepts/cross-sell.md, cntu.md, sebi-regulations.md, c-mab.md, product-affinity.md
  - wiki/entities/push-notifications.md, whatsapp-channel.md, email-channel.md, narad.md, feed-nc.md
  - wiki/entities/preksha.md, ritvik.md
- Pages updated:
  - wiki/concepts/activation-funnel.md (added exact drop rates, WA benchmarks, post-Esign cohorts)
  - wiki/concepts/fid.md (added CAC benchmarks)
  - wiki/concepts/ttu.md (added retention propensity deciles, ML uplift numbers)
- Contradictions: none (Master Reference is the source of truth for all other docs)
- Total: 12 new pages, 3 updated

## [2026-04-05] ingest | Vocabulary
- Summary: A-Z glossary — 60+ terms with confirmation status. Mostly validates existing pages.
- Source: raw/About the Verticle/06 - Reference/Vocabulary.md
- Pages created: source-vocabulary.md, active-ppu.md, gcg.md
- Pages updated: none (existing pages already accurate)
- Contradictions: none
- Note: NTU naming collision (metric vs segment prefix) already documented in ntu.md
- Total: 3 new pages

## [2026-04-05] ingest | Pod Playbooks
- Summary: 650+ line pod-centric reference. Expands 5 pods to 8 workstreams. Adds Pay Pod, Feed/Content, Cross-sell initiative detail.
- Source: raw/About the Verticle/02 - Pods/Pod Playbooks.md
- Pages created:
  - wiki/sources/source-pod-playbooks.md
  - wiki/entities/pay-pod.md
  - wiki/concepts/rf-score.md, cnc-personalization-ladder.md
- Pages updated:
  - wiki/entities/invest-activation-pod.md (added onboarding journey touchpoints table)
  - wiki/entities/trading-pod.md (added timing triggers, F&O content × cohort matrix)
- Contradictions: none (playbooks complement Master Reference)
- Total: 4 new pages, 2 updated

## [2026-04-05] ingest | Data Architecture
- Summary: Technical reference — BQ tables, Kafka topics, NARAD pipeline, segment registry (PA/NTU/TTU/IPO segments), ML pipelines, infra specs
- Source: raw/About the Verticle/03 - Data & Systems/Data Architecture.md
- Pages created: source-data-architecture.md, segment-registry.md, audience-manager.md
- Pages updated: none (NARAD entity already comprehensive from Ingest #2)
- Contradictions: none
- Total: 3 new pages (data-arch)

## [2026-04-05] ingest | ML Systems
- Summary: Full specs for 9 ML models — training, inference, accuracy, owners. Plus Aampe rejection.
- Source: raw/About the Verticle/03 - Data & Systems/ML Systems.md
- Pages created: source-ml-systems.md, ml-models-overview.md
- Total: 2 new pages

## [2026-04-05] ingest | Analytics & Metrics
- Source: raw/About the Verticle/04 - Analytics/Analytics & Metrics.md
- Pages created: source-analytics-metrics.md, kpi-tree.md
- Key addition: KPI tree with MAI as North Star; dashboard column definitions
- Total: 2 new pages

## [2026-04-05] ingest | Campaign Library
- Source: raw/About the Verticle/05 - Campaigns/Campaign Library.md
- Pages created: source-campaign-library.md, daily-push-slots.md
- Key addition: 4-slot daily PN structure; CMAB slot naming; Non-TTU content calendar; SOPs
- Total: 2 new pages

## [2026-04-05] ingest | Concepts & Notes
- Source: raw/About the Verticle/06 - Reference/Concepts & Notes.md
- Pages created: source-concepts-notes.md
- Note: Explanatory doc (the "why" layer). No new facts — validates existing pages.
- Total: 1 new page

## [2026-04-05] ingest | Email System (11 files)
- Source: raw/Groww-Email-System/ (11 files, ~1085 lines)
- Pages created: groww-email-system.md (entity), source-email-system.md (source summary)
- Note: Self-contained project — compiled into one comprehensive entity page rather than splitting across many
- Total: 2 new pages

## [2026-04-05] complete | All raw sources ingested
- Total wiki pages: 55
- Source summaries: 10 (covering all 26 raw .md files)
- Entity pages: 21 (people, pods, systems, channels)
- Concept pages: 19 (metrics, strategies, ML models)
- Meta pages: 3 (overview, index, log)
- Empty dirs: analyses/, comparisons/ (waiting for queries)
- Next: open in Obsidian, explore the graph, start querying

## [2026-04-05] update | Email System — Session 5 changes
- Change: Synced 4 updated raw files (CHANGELOG, CLAUDE_CODE_CONTEXT, OPEN_ISSUES, PROJECT_STATE) from original vault
- Key updates:
  - Figma MCP integration (two-tier image generation: Figma primary, chart-image-agent fallback)
  - 4 blocks refined (step_instruction VML, contract_row links, filter_pills states)
  - 2 new recipes (commentary + feature_launch)
  - Renderer async fix (Playwright thread offload)
  - New open issue I12: Figma file not yet created
- Pages updated: wiki/entities/groww-email-system.md
- Contradictions: Project status was "wire server.py" → now "create Figma file" (superseded, updated)

## [2026-04-06] update | Email System — Session 6 sync
- Change: Synced 4 updated files + 1 new file (OB_TO_FID_ANALYSIS.md) from original vault
- Key updates:
  - New source: OB-to-FID email journey analysis (12 email types, Day 0–7, push specs, ~50 screenshots needed)
  - 3 new blocks: app_screenshot_pair, product_category_grid, social_showcase (total: 18 blocks)
  - 9 onboarding recipes built (total: 13 recipes, all validated 0 issues)
  - Push notification specs for all 9 days
  - Open rate data: Edu-3 highest (25.4%), Edu-4 lowest (15.3%)
  - Pending: ~50 placeholder images, 915 brand recipes
- Pages created: wiki/sources/source-ob-to-fid-analysis.md
- Pages updated: wiki/entities/groww-email-system.md (Session 6 section, block count 15→18), wiki/index.md
- Contradictions: none

## [2026-04-06] ingest | Compass MCP Documentation (3 PDFs)
- Summary: Full Compass MCP platform docs — product overview, 16 analytics skills, setup guide
- Source: raw/Compass-MCP/ (3 PDFs, 37 pages)
- Pages created: source-compass-mcp.md, compass-mcp.md (entity), compass-analytics-skills.md (concept)
- Key facts: Compass = DataHub+Superset+Trino via MCP; 16 skills; 80+ tools; Engagement skill has 250M PN rows/day; 57B session rows; universal join key = user_account_id
- Contradiction noted: Wiki said BQ is primary query path — Compass uses Trino on platform_iceberg. BQ still feeds Audience Manager but Compass queries go through Trino.
- Total: 3 new Compass pages

## [2026-04-06] ingest | Handwritten Task Notes (2 images)
- Summary: Two notebook photos — full task architecture (4-box pipeline, pod assignments) + Content Engine workflow (template → prompt)
- Source: raw/assets/my-full-task.jpg, raw/assets/content-engine.jpg
- Pages created: wiki/sources/source-handwritten-notes.md

## [2026-04-06] create | Project Map (Wiki ↔ Code Reference)
- Summary: Meta page connecting wiki concepts → actual files on disk. 19 blocks, 16 recipes, 6 chart templates, 10 skills, 9 external systems, 7 not-yet-built items inventoried.
- Pages created: wiki/project-map.md
- Pages updated: wiki/index.md, CLAUDE.md, ~/.claude/skills/wiki-kb/SKILL.md (all now reference project-map in session start)

## [2026-04-06] lint | Completeness audit + fix
- Summary: Audited wiki completeness — found 30 missing pages (65% complete), 34 broken wikilinks, 1 typo, 7 phantom index entries. Fixed all.
- Pages created (23):
  - Products (10): mutual-funds, stocks-cnc, fno, commodities, mtf, mis, ipo, pay-upi, gold, fixed-deposits
  - Systems (6): webengage, cosmos, bigquery, superset, ems, netcore
  - Channels (2): rcs-sms, in-app-stories
  - ML Models (5): campaign-affinity, cross-sell-affinity, retention-propensity, instrument-affinity, widget-ranker
- Pages updated:
  - index.md — removed 7 phantom source entries, added source-email-system + source-handwritten-notes
  - cnc-personalization-ladder.md — fixed typo [[hritwik]] → [[ritvik]]
- Result: Wiki now ~100% complete. All index entries have pages. All wikilinks resolve.

## [2026-04-07] lint | Second audit pass — final cleanup
- Summary: Second completeness audit found 6 remaining issues. All fixed.
- Deleted: hritwik.md (0-byte garbage artifact from typo fix)
- Created: retention-strategy.md, fcm.md, sip.md (3 pages fixing broken wikilinks)
- Fixed: overview.md — added tags, removed [[time-activity]] broken link (not a standalone model)
- Updated: index.md — added fcm, retention-strategy, sip entries
- Broken wikilinks remaining: 0
- Orphan pages: 0
- Empty pages: 0

## [2026-04-09] update | Email System — Sessions 6b/7/8 sync
- Change: Synced 4 updated files + 1 new (QA_AUDIT_REPORT.md) from original vault
- Key updates across 3 sessions:
  - Session 6b: QA audit report, 3 educational recipes (Edu 1-3) built to fix P0 gaps
  - Session 7: Natural Gas Mini + April expiry calendar educational emails
  - Session 8: 3 new 915 dark theme recipes, 11 new blocks, 2 transactional recipes, 3 newsletter recipes (from production), automated test suite, skills rewritten
  - Phase 5 COMPLETE → now Phase 6 (915 + Transactional)
  - Block count: 19 → 30. Recipe count: 13 → 24. All pass tests.
  - Old monolithic templates deleted. Skills updated for block-based workflow.
- Pages updated: wiki/entities/groww-email-system.md (Sessions 6b/7/8 sections, block table 19→30, phase 5→6)
- Contradictions: Phase status was "Phase 5 in progress" → now "Phase 6 in progress" (superseded)

## [2026-04-09] update | Project Map — full inventory refresh
- Summary: Rebuilt project-map.md with complete current inventory from disk
- Blocks: 19 → **34** (+15: content_cards, featured_question, ipo_card, step_card, and 11 from Session 8)
- Recipes: 16 → **56** (+40: 14 educational, 10 onboarding, 8 newsletter, 7 x 915, 6 promotional, 6 transactional, 2 alert, 3 other)
- Skills: 10 → **11** (+create-email)
- New components discovered: analyzer/ (classifier, detector, parser, pipeline), tools/ (chart_image, content_planner), tests/, CLI entry point
- NOT-yet-built list updated (915 bg_image, alert recipes, resurrection recipes, Figma file)
- Pages updated: wiki/project-map.md (full rewrite)

## [2026-04-09] lint | Precision audit — fix vague/incorrect context
- Summary: Audit found 23 vague, imprecise, or contradictory claims. Fixed 8 in-place, marked 16 with ⚠️ for user verification.
- In-place fixes:
  - CTR contradiction resolved: 12% = campaign-specific (52W H/L), 4.3% = blended daily average
  - BQ vs Trino: overview.md now documents dual pipeline (BQ→segments, Trino→analytics)
  - Added source citations (Master Reference v2, 2026-03-26) to all major benchmarks
  - "Session Conversion" flagged with likely definition
  - Widget Ranker: clarified "daily batch + RT serving" (not contradictory)
  - ATH: clarified "achieved Jan 2024" not "as of Jan 2024"
  - "Self-direct": defined as "already transacting without comms"
  - L150D+: defined as "last activity 31-150 days ago"
- Pages created: wiki/open-verification-checklist.md (16 items for user)
- Pages updated: ttu.md, product-affinity.md, instrument-affinity.md, retention-propensity.md, c-mab.md, widget-ranker.md, cnc-personalization-ladder.md, cross-sell-affinity.md, cntu.md, activation-funnel.md, rf-score.md, push-notifications.md, webengage.md, overview.md, index.md
