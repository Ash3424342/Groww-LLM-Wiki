---
title: Project Map — Wiki ↔ Code Reference
date_updated: 2026-04-09
tags: [meta, project-map, reference, code]
---

# Project Map

**Purpose**: Connect wiki concepts to actual files on disk so any LLM can look at the wiki and know exactly where to find what's built, what's a doc, and what's not built yet.

---

## Built Projects (on disk)

### 1. Groww Email System (Content Engine)

**Path**: `/Users/ashishch/Downloads/To Build/groww-creative-mcp/`
**Wiki page**: [[groww-email-system]]
**Status**: Phase 6 (915 + Transactional) — in progress

| Component | Path | What it does |
|-----------|------|-------------|
| `server.py` | `./server.py` | MCP server entry point |
| `__main__.py` | `./__main__.py` | CLI entry point |
| `cli.py` | `./cli.py` | CLI interface |
| `assembler/engine.py` | `./assembler/engine.py` | Recipe JSON → rendered HTML |
| `assembler/validator.py` | `./assembler/validator.py` | 102KB, SEBI, alt text validation |
| `analyzer/` | `./analyzer/` | Email analysis pipeline (classifier, detector, parser, models) |
| `tools/chart_image.py` | `./tools/chart_image.py` | Chart image tool |
| `tools/content_planner.py` | `./tools/content_planner.py` | Content planning tool |
| `tokens/groww.py` | `./tokens/groww.py` | Groww light theme tokens |
| `tokens/nine15.py` | `./tokens/nine15.py` | 915 dark theme tokens |
| `tokens/shared.py` | `./tokens/shared.py` | Spacing, constraints, icon SVGs |
| `blocks/` | `./blocks/` | **34 Jinja2 partials** |
| `recipes/` | `./recipes/` | **56 JSON email configs** |
| `tests/test_all_recipes.py` | `./tests/` | Automated test suite (all recipes pass) |
| `formatters.py` | `./formatters.py` | Indian number formatting (₹) |
| `renderer.py` | `./renderer.py` | Playwright screenshot (async-safe) |
| `skills/create-email/` | `./skills/create-email/` | Bundled email creation skill |
| `output/` | `./output/` | Generated test emails |

#### Blocks (34 files in `blocks/`)

| Block | File | Category |
|-------|------|----------|
| Base skeleton | `_base_email.html` | Core |
| Header logo | `header_logo.html` | Core |
| Hero text | `hero_text.html` | Core |
| Hero image | `hero_image.html` | Core |
| Article section | `article_section.html` | Core |
| Factor card | `factor_card.html` | Core |
| CTA button | `cta_button.html` | Core |
| Social proof banner | `social_proof_banner.html` | Core |
| Divider | `divider.html` | Core |
| Footer standard | `footer_standard.html` | Core |
| Card wrapper | `card_wrapper.html` | Core |
| Chart image | `chart_image.html` | Data |
| Step instruction | `step_instruction.html` | Data |
| Contract row | `contract_row.html` | Data |
| Filter pills | `filter_pills.html` | Data |
| Listing header | `listing_header.html` | Data |
| App screenshot pair | `app_screenshot_pair.html` | Onboarding |
| Product category grid | `product_category_grid.html` | Onboarding |
| Social showcase | `social_showcase.html` | Onboarding |
| Transaction summary | `transaction_summary.html` | Transactional |
| Status badge | `status_badge.html` | Transactional |
| Bulletin header | `bulletin_header.html` | Newsletter |
| Index ticker | `index_ticker.html` | Newsletter |
| Section heading | `section_heading.html` | Newsletter |
| Concept card | `concept_card.html` | Newsletter |
| Feedback buttons | `feedback_buttons.html` | Newsletter |
| Dot divider | `dot_divider.html` | Newsletter |
| Team signoff | `team_signoff.html` | Newsletter |
| Stock table | `stock_table.html` | Newsletter |
| Callout | `callout.html` | Newsletter |
| Content cards | `content_cards.html` | Promotional |
| Featured question | `featured_question.html` | Promotional |
| IPO card | `ipo_card.html` | Promotional |
| Step card | `step_card.html` | Promotional |

#### Recipes (56 files in `recipes/`)

**Educational (14)**
| Recipe | File |
|--------|------|
| Basics of commodities | `groww_educational_basics.json` |
| Commodity (crude oil) | `groww_educational_commodity.json` |
| Natural gas | `groww_educational_natgas.json` |
| Natural gas mini | `groww_educational_natgas_mini.json` |
| Pre-trading guide | `groww_educational_pretrading.json` |
| First trade | `groww_educational_first_trade.json` |
| Market commentary | `groww_educational_commentary.json` |
| April expiry calendar | `groww_educational_april_expiry.json` |
| IPO guide | `groww_educational_ipo.json` |
| Cashless MTF | `groww_educational_cashless_mtf.json` |
| MTF awareness | `groww_educational_mtf_awareness.json` |
| MTF cross-sell | `groww_educational_mtf_cross_sell.json` |
| MIS cross-sell | `groww_educational_mis_cross_sell.json` |
| Gold/silver rally | `groww_educational_gold_silver_rally.json` |
| Research report | `groww_educational_research_report.json` |

**Onboarding (10)**
| Recipe | File | Day |
|--------|------|-----|
| Welcome | `groww_onboarding_welcome.json` | D0 |
| Stocks | `groww_onboarding_stocks.json` | D1 |
| SIP | `groww_onboarding_sip.json` | D2 |
| Stock tools | `groww_onboarding_stocks_tools.json` | D3 |
| MF explore | `groww_onboarding_mf_explore.json` | D4 |
| Stock features | `groww_onboarding_stocks_features.json` | D5a |
| MF features | `groww_onboarding_mf_features.json` | D5b |
| F&O | `groww_onboarding_fno.json` | D6 |
| Brand story | `groww_onboarding_brand.json` | D7 |
| F&O journey D0 | `groww_onboarding_fno_journey_day0.json` | D0 (F&O) |

**Newsletter (8)**
| Recipe | File |
|--------|------|
| Trading bulletin | `groww_newsletter_trading_bulletin.json` |
| Daily digest | `groww_newsletter_daily_digest.json` |
| Investment weekly | `groww_newsletter_investment_weekly.json` |
| Weekly digest | `groww_newsletter_weekly_digest.json` |
| Week roundup | `groww_newsletter_week_roundup.json` |
| Monthly roundup | `groww_newsletter_monthly_roundup.json` |
| AMFI report | `groww_newsletter_amfi_report.json` |
| CEO product update | `groww_newsletter_ceo_product_update.json` |

**915 Brand (7)**
| Recipe | File |
|--------|------|
| Market alert | `915_alert_market.json` |
| Daily wrap digest | `915_digest_daily_wrap.json` |
| Event invite | `915_promotional_event_invite.json` |
| Event confirmation | `915_promotional_event_confirmation.json` |
| Feature update | `915_feature_update.json` |
| Promotional drip | `915_promotional_drip.json` |
| Referral | `915_promotional_referral.json` |

**Promotional (6)**
| Recipe | File |
|--------|------|
| Budget Day | `groww_promotional_budget_day.json` |
| Commodity GTM | `groww_promotional_commodity_gtm.json` |
| Groww Next | `groww_promotional_groww_next.json` |
| NFO launch | `groww_promotional_nfo_launch.json` |
| W Club invite | `groww_promotional_w_club_invite.json` |
| AIKI city event | `groww_promotional_aiki_city_event.json` |

**Transactional (6)**
| Recipe | File |
|--------|------|
| Order confirmation | `groww_transactional_order_confirmation.json` |
| SIP execution | `groww_transactional_sip_execution.json` |
| SIP autopay migration | `groww_transactional_sip_autopay_migration.json` |
| Negative balance | `groww_transactional_negative_balance.json` |
| Groww Next confirmation | `groww_transactional_groww_next_confirmation.json` |
| Product update | `groww_transactional_product_update.json` |

**Alert (2)**
| Recipe | File |
|--------|------|
| IPO corner | `groww_alert_ipo_corner.json` |
| IPO open | `groww_alert_ipo_open.json` |

**Other (3)**
| Recipe | File |
|--------|------|
| Feature launch | `groww_feature_launch.json` |
| Infosec: digital arrests | `groww_infosec_digital_arrests.json` |

### 2. Chart Image Agent

**Path**: `/Users/ashishch/Downloads/To Build/chart-image-agent/`
**Wiki page**: [[groww-email-system]] (sub-project section)
**Status**: Functional

| Component | Path | What it does |
|-----------|------|-------------|
| `chart_agent/config.py` | `./chart_agent/config.py` | COLORS_LIGHT/DARK, ICONS |
| `chart_agent/generator.py` | `./chart_agent/generator.py` | Config → HTML → PNG pipeline |
| `chart_agent/renderer.py` | `./chart_agent/renderer.py` | Playwright screenshot (async-safe) |
| `chart_agent/formatters.py` | `./chart_agent/formatters.py` | Price formatting, SVG paths |
| `chart_agent/templates/` | `./chart_agent/templates/` | 6 HTML chart templates |
| `examples/` | `./examples/` | 5 example configs |

#### Chart Templates (6)

| Template | File | Output |
|----------|------|--------|
| Price card | `price_card.html` | Single instrument price + sparkline |
| Listing card | `listing_card.html` | Multiple instruments list |
| Comparison | `comparison.html` | Side-by-side comparison |
| Metric | `metric.html` | Single KPI metric card |
| Portfolio | `portfolio.html` | Portfolio overview |
| Base | `_base.html` | Shared HTML skeleton |

---

## Claude Code Skills (on disk)

**Path**: `~/.claude/skills/`

| Skill | Directory | Wiki page | Relevance |
|-------|-----------|-----------|-----------|
| `wiki-kb` | `~/.claude/skills/wiki-kb/` | This wiki's operating skill | Core |
| `groww-email` | `~/.claude/skills/groww-email/` | [[groww-email-system]] | Core |
| `915-email` | `~/.claude/skills/915-email/` | (915 variant) | Core |
| `create-email` | `~/.claude/skills/create-email/` | Unified email creation | Core |
| `chart-image` | `~/.claude/skills/chart-image/` | Chart generation | Core |
| `pdf` | `~/.claude/skills/pdf/` | PDF processing | Utility |
| `pptx` | `~/.claude/skills/pptx/` | PowerPoint | Utility |
| `docx` | `~/.claude/skills/docx/` | Word docs | Utility |
| `mermaid` | `~/.claude/skills/mermaid/` | Diagrams | Utility |
| `mcp-builder` | `~/.claude/skills/mcp-builder/` | MCP server creation | Dev tool |
| `skill-creator` | `~/.claude/skills/skill-creator/` | Skill creation meta-tool | Dev tool |

---

## Documentation Vaults (on disk)

| Vault | Path | Wiki page | Purpose |
|-------|------|-----------|---------|
| Original Obsidian vault | `~/Desktop/Groww/` | — | Source of truth (don't modify) |
| LLM Knowledge Base | `~/Desktop/Groww-LLM-Wiki/` | This wiki | Compiled wiki (LLM-maintained) |
| Compass MCP docs | `~/Downloads/My task - Groww/Compass MCP/` | [[compass-mcp]] | 3 PDFs |
| Task notes (images) | `~/Downloads/My task - Groww/` | [[source-handwritten-notes]] | 2 handwritten photos |

---

## External Systems (not on disk — accessed via network)

| System | Access | Wiki page |
|--------|--------|-----------|
| Compass MCP | `http://127.0.0.1:3100/mcp` (local proxy → VPN) | [[compass-mcp]] |
| DataHub | Via Compass MCP tools | [[compass-mcp]] |
| Superset | Via Compass MCP tools | [[superset]] |
| Trino | Via `run_trino_query` | [[compass-mcp]] |
| WebEngage | Internal tool (browser) | [[webengage]] |
| NARAD | Internal tool | [[narad]] |
| Audience Manager | Internal tool | [[audience-manager]] |
| Netcore | Email ESP | [[netcore]] |
| Figma | Via Figma MCP (needs auth) | [[groww-email-system]] |

---

## NOT Yet Built (from notes + wiki gaps)

| Item | Where it should go | Status |
|------|-------------------|--------|
| Alert: price alert recipe | `recipes/` | Not started |
| Alert: margin call recipe | `recipes/` | Not started |
| Alert: 52W H/L recipe | `recipes/` | Not started |
| 915 bg_image support | `blocks/_base_email.html` | Not started (dark theme background) |
| 915 educational recipes | `recipes/` | Not started |
| Resurrection email recipes | `recipes/` | Not started |
| Figma "Groww Email Assets" file | Figma (cloud) | I12: needs manual creation |
| ~50 real app screenshots | hosted/assets | Need design team or app captures |
| Segment ID → Recipe automation | Not designed | How a segment triggers a specific recipe |

---

## Growth Summary

| Metric | Session 5 | Session 8 | Current |
|--------|----------|----------|---------|
| Blocks | 19 | 30 | **34** |
| Recipes | 13 | 24 | **56** |
| Skills | 10 | 10 | **11** |
| Chart templates | 6 | 6 | 6 |
| Phase | 5 | 6 | 6 |

---

## How an LLM Should Use This Page

1. **"Where's the code for X?"** → Check the Built Projects section
2. **"Is X built or just documented?"** → Check Built vs NOT Yet Built
3. **"What file do I edit to change Y?"** → Follow the component tables
4. **"What systems can I access?"** → External Systems section
5. **"What skills are available?"** → Claude Code Skills section
6. **"What email types exist?"** → Recipes section, organized by type

This page is the bridge between the wiki (knowledge) and the codebase (implementation).
