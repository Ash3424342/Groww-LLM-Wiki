# Open Issues

> Known bugs, visual mismatches, and TODO items.

---

## Critical (blocks next session)

### I1: Final HTML not verified after fixes
**Status**: Closed (2026-04-03)
**Resolution**: Regenerated with light-theme chart images. All 0 validation issues. Visual match confirmed.

### I2: 915 dark email not generated
**Status**: Closed (2026-04-03)
**Resolution**: Generated 915 light (default) and 915 dark (opt-in). Both pass validation. Dark variant has correct colors, dark mode CSS, dark social icons.

### I10: server.py not wired to assembler
**Status**: Closed (2026-04-03)
**Resolution**: Rewrote server.py. Replaced `groww_generate_915_email` and `groww_generate_groww_email` with single `groww_assemble_email(recipe_json)`. Deleted `tools/email_915.py`, `tools/email_groww.py`, `templates/email/915_promotional.html`, `templates/email/groww_educational.html`. `groww_list_blocks` now reads live from blocks/ and recipes/ directories.

---

## Medium (address this week)

### I3: Old monolithic templates not deleted
**Status**: Closed (2026-04-08)
**Resolution**: Already resolved in Session 2b. `templates/email/` was deleted. `templates/charts/` remains because it's actively used by the chart-image-agent for PNG generation.

### I4: Brand voice module not built
**Status**: Open
**Description**: ARCHITECTURE.md defines a `voice/` module with Groww and 915 tone rules (lead with numbers, no fear language, Indian formatting, forbidden phrases). Not yet implemented.
**Action**: Build `voice/groww.py` and `voice/nine15.py`. Low priority — doesn't block email generation.

### I5: Missing email types
**Status**: Partially closed (2026-04-08)
**Description**: No samples or recipes for: transactional (order confirmation, SIP executed), alert (price alert, margin call), digest (daily wrap, portfolio summary), onboarding (welcome, KYC, first investment).
**Resolution**: 9 onboarding recipes created (full 7-day journey). 3 new 915 recipes (market alert, daily wrap, event invite). 2 transactional recipes (order confirmation, SIP execution). Remaining: alert (price alert, margin call, 52W H/L), digest (portfolio summary, weekly roundup), 915 educational, resurrection.
**Action**: Build remaining alert and digest recipes.

### I6: Actual Groww asset URLs not confirmed
**Status**: Open
**Description**: Tokens reference `cms-resources.groww.in` URLs for logos and social icons. These were extracted from email HTML source but need verification that they're stable/permanent.
**Action**: Check with Groww team whether these CDN URLs are production-stable.

---

## Low (nice to have)

### I7: insight_card vs factor_card merge
**Status**: Open
**Description**: Email 7 uses "insight cards" with #eaf3f0 bg. Email 8 uses "factor cards" with #E6FCF5 bg. Structurally identical — only bg color differs. Should these be the same block with a color param?
**Action**: Merge into single `factor_card` block with `bg_color` override. Already parameterized.

### I8: Chart-image-agent commodity icons are SVG, not PNG
**Status**: Open
**Description**: Barrel icons in chart-image-agent are inline SVGs, not the actual Groww app icons. They look functional but don't match the polished 3D barrel illustrations in the Groww app.
**Action**: Get actual barrel/gold/gas/silver icon PNGs from Groww design team, embed as base64 or host on CDN.

### I11: asyncio.run() conflict in chart MCP tool
**Status**: Closed (2026-04-05)
**Resolution**: Renderer now detects running async event loop and offloads Playwright to a separate `threading.Thread`. Works from both sync (CLI) and async (MCP server) contexts. Verified working with `groww_generate_chart_image` tool.

### I12: Figma file "Groww Email Assets" not yet created
**Status**: Open
**Description**: The Figma MCP workflow is documented in CLAUDE.md but the actual Figma file with components (Price Card, Listing Card, Factor Card, etc.) has not been created yet. Without this file, the Figma MCP primary path cannot be used and sessions will fall back to chart-image-agent.
**Action**: Either create manually in Figma (~2 hours) or use Claude Code + `use_figma` tool to set up programmatically. Need Groww design team's actual commodity icons (barrel, gold, gas, silver illustrations). See CLAUDE.md "Figma file structure" section for the full spec.

### I9: No automated visual regression testing
**Status**: Open
**Description**: Verification is manual (open in browser, compare visually). Should have automated pixel-diff comparison.
**Action**: Consider Percy, BackstopJS, or custom Playwright screenshot diffing. Low priority.
