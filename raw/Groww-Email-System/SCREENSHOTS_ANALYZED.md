# Screenshots Analyzed

> All reference emails cataloged with type, blocks identified, and token gaps found.

---

## Email catalog

| # | Type | Sub-type | Brand | Source | New blocks found | Status |
|---|------|----------|-------|--------|------------------|--------|
| 1 | Educational | Commodity explainer | Groww | Built (v6) | factor_card, contract_row | Migrated to recipe |
| 2 | Promotional | Event invite | 915 | Built | hero_image (dark) | Migrated to recipe |
| 3 | Marketing | F&O hero mockup | Groww | SVG screenshot | hero_phone_mockup | Cataloged only |
| 4 | Listing | Dark mode commodities | 915 | SVG screenshot | (dark variant of existing) | Dark theme added |
| 5 | Feature launch | MTF SL/TGT | Groww | HTML source | step_instruction, social_proof_banner | Recipe created |
| 6 | IPO notification | Jyoti CNC Automation | Groww | HTML source | ipo_details, team_signature | Cataloged only |
| 7 | Educational | Market commentary | Groww | HTML source | insight_card | Recipe created |
| 8 | Educational | Commodity explainer v2 (production) | Groww | HTML source | (validates existing) | **Token source of truth** |

---

## Detailed analysis per email

### Email 5: Feature launch — MTF SL/TGT
- **Subject**: "SL & TGT IN MTF"
- **Structure**: logo → hero image (app screenshot) → body text → "How to convert" steps with screenshots → CTA ("TRY IT NOW" blue #5367ff) → social proof → footer
- **Font**: Inter Tight
- **CTA color**: Blue #5367ff (not green)
- **New pattern**: Step-by-step instruction with numbered screenshots

### Email 6: IPO notification — Jyoti CNC
- **Subject**: IPO notification
- **Structure**: logo → hero banner → personalized greeting (merge tag) → IPO details table → company description → CTA ("APPLY NOW" blue #4f74ee) → "Team Groww" signature → footer
- **Merge tags**: `{{user['system']['first_name']}}`
- **New pattern**: Key-value detail table (bidding period, price band, lot size, subscription rate, listing date)

### Email 7: Educational — Sailing through volatile markets
- **Subject**: "Sailing through bearish markets"
- **Structure**: logo banner → headline (30px bold) → hero illustration → body (geopolitical context) → data chart image → historical examples → "Why does this happen?" → 3 insight cards (#eaf3f0 bg) → closing → CTA ("EXPLORE MARKETS" blue #5367ff) → social proof → footer
- **Insight card bg**: #eaf3f0 (slightly different from email 8's #E6FCF5)

### Email 8: Educational — What moved Crude Oil this March? (PRODUCTION)
- **Subject**: "Crude Oil moved ~40% in March. Here's why."
- **Structure**: logo banner → hero headline (21px/800, green-colored "Crude Oil") → subtitle → chart PNG (hosted, border-radius 16px) → 3 factor cards (#E6FCF5, 12px radius, centered) → divider → contract list PNG (hosted) → CTA ("EXPLORE COMMODITIES" green #00b386) → social proof (#f4fdf9) → footer
- **This is the source of truth for tokens**
- Chart and contract list are pre-rendered PNGs (not HTML), confirming our chart-image-agent approach

---

## Token gaps discovered across samples

| Token | Email 5 | Email 6 | Email 7 | Email 8 (truth) | Resolution |
|-------|---------|---------|---------|-----------------|------------|
| Text primary | #000000 | #000000 | #000000 | #353839 | Use #353839 default, override via token_overrides |
| CTA color | #5367ff (blue) | #4f74ee (blue) | #5367ff (blue) | #00b386 (green) | Two CTA styles: green (default) + blue (feature) |
| Factor bg | — | — | #eaf3f0 | #E6FCF5 | Use #E6FCF5 default, parameterize per block |
| Social proof bg | #edfffb | — | #f4fdf9 | #f4fdf9 | Use #f4fdf9 |
| Footer font | Roboto | Roboto | Roboto | Inter Tight | Use Inter Tight (newer emails use it) |
