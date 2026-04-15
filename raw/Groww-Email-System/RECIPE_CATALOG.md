# Recipe Catalog

> All email recipes (JSON configs that define emails as block sequences).
> Location: `groww-creative-mcp/recipes/`

---

## Built recipes

### `groww_educational_commodity.json`
- **Brand**: Groww (light)
- **Type**: Educational / Commodity explainer
- **Based on**: Production email 8 ("What moved Crude Oil this March?")
- **Blocks used**: header_logo → hero_text → hero_image (subtitle) → chart_image → article_section → factor_card (x3) → divider → chart_image (contract list) → cta_button (green) → social_proof_banner → footer_standard

### `groww_educational_commentary.json`
- **Brand**: Groww (light)
- **Type**: Educational / Market commentary
- **Based on**: Email 7 ("Sailing through volatile markets")
- **Blocks used**: header_logo → hero_text → hero_image → article_section → hero_image (data chart) → article_section → factor_card (x3) → article_section → cta_button (blue) → social_proof_banner → footer_standard

### `groww_feature_launch.json`
- **Brand**: Groww (light)
- **Type**: Feature launch
- **Based on**: Email 5 ("SL & TGT in MTF")
- **Blocks used**: header_logo → hero_image → article_section → step_instruction → cta_button (blue) → social_proof_banner → footer_standard

---

## Planned recipes (not yet built)

| Recipe | Brand | Type | Blocks needed | Blocking on |
|--------|-------|------|---------------|-------------|
| `groww_alert_price.json` | Groww | Alert / Price alert | header_logo, metric_highlight, article_section, cta_button, footer | No metric_highlight block sample |
| `groww_digest_daily.json` | Groww | Digest / Daily wrap | header_logo, hero_text, metric_highlight, chart_image (comparison), article_section, cta_button, footer | No digest email sample |
| `groww_ipo_notification.json` | Groww | Transactional / IPO | header_logo, hero_image, article_section, ipo_details, cta_button, footer | ipo_details block not built |
| `nine15_promotional_event.json` | 915 | Promotional / Event invite | header_logo, hero_image, article_section, cta_button, footer | Need to migrate from old monolithic template |
| `nine15_educational_dark.json` | 915 (dark) | Educational | Same as groww_educational_commodity but with `brand: "915", theme: "dark"` | Dark assembly not tested yet |
