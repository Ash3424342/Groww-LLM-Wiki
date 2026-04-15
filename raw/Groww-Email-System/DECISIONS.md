# Decisions

> Key architectural decisions and the reasoning behind them.

---

### D1: Component-based blocks over monolithic templates
**Date**: 2026-04-03
**Decision**: Build 15 reusable blocks that snap together via JSON recipes, instead of one Jinja2 template per email type.
**Why**: The Groww educational email took 6 iterations as a monolithic template. Every new email type would repeat this pain. Blocks share the design system automatically — when Groww updates their green, you change one token, not 20 templates.
**Trade-off**: Slightly more complex assembly engine, but dramatically faster per-email iteration.

### D2: SVG path for chart lines over Chart.js canvas
**Date**: 2026-04-03
**Decision**: Generate chart lines as inline SVG `<path>` elements instead of Chart.js `<canvas>`.
**Why**: SVG scales perfectly at any DPI. Canvas can have sub-pixel rendering artifacts at 3x screenshot scale. SVG also renders instantly (no animation wait needed).
**Trade-off**: Lose Chart.js interactivity and tooltips. Acceptable since output is a static PNG.

### D3: Playwright screenshot over matplotlib for chart PNGs
**Date**: 2026-04-03
**Decision**: Render charts as HTML/CSS, screenshot with Playwright at 3x, instead of generating with matplotlib.
**Why**: Side-by-side comparison showed Playwright output is near-identical to Groww's app screenshots. Matplotlib output looks "generated" — fonts feel off, spacing is awkward, rounded corners require hacky patches.
**Trade-off**: Requires Chromium dependency. Acceptable for a build-time tool.

### D4: Token source of truth is production email 8
**Date**: 2026-04-03
**Decision**: Lock design tokens from the actual shipped "What moved Crude Oil this March?" email.
**Why**: Across 8 samples, colors were inconsistent (email 7 uses #000000 for primary, email 8 uses #353839). Production email is the most recent and most polished.
**Trade-off**: Older emails may look slightly different when recreated. Mitigated by `token_overrides` in recipes.

### D5: Token overrides per recipe
**Date**: 2026-04-03
**Decision**: Recipes can specify `meta.token_overrides` dict that merges on top of brand defaults.
**Why**: Not all Groww emails use identical colors. Rather than creating multiple token sets, allow per-recipe tweaks. Example: `{"text_primary": "#000000"}` for emails that use pure black headings.

### D6: Images always hosted, never base64 in email HTML
**Date**: 2026-04-03
**Decision**: Chart PNGs are hosted on CDN (or referenced via CID), never embedded as base64.
**Why**: Base64 images bloat HTML size. A single chart at 3x can be 200KB+ as base64, blowing past Gmail's 102KB clipping limit instantly. Production email 8 confirms Groww hosts images on `cms-resources.groww.in`.

### D7: Card wrapper in Phase 2, not deferred
**Date**: 2026-04-03
**Decision**: Build `card_wrapper` block immediately, not defer it.
**Why**: The commodity listing email has two separate card groups (regular contracts + Mini contracts). Without card_wrapper, you can't reproduce that visual separation. Originally deferred, corrected before build.

### D8: Two CTA colors, not one
**Date**: 2026-04-03
**Decision**: Support green (#00b386) and blue (#5367ff) CTA buttons via a `style` param.
**Why**: Production emails use green for market/educational CTAs and blue for feature launch CTAs. This is intentional brand design, not inconsistency.
