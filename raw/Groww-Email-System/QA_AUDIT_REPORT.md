# QA AUDIT REPORT — OB-to-FID Email System
> **Auditor**: Ruthless QA
> **Date**: 2026-04-06
> **Scope**: All artifacts built from PDF analysis (OB to FID_Feb_v3.pdf split into 1.pdf + 2.pdf)
> **Verdict**: Multiple issues found. See below.

---

## 1. SOURCE VERIFICATION

### PDF 1 (Educational Email Series) — Re-extraction vs Analysis

| Field | PDF Source (re-extracted) | Analysis Doc | Recipe | Verdict |
|-------|-------------------------|--------------|--------|---------|
| **Email 1 title** | "Email 1: Basics of commodities trading" | "Email Edu-1: Basics of Commodities Trading" | N/A (no recipe built) | 🕳️ MISSING — No recipe exists for Edu-1 |
| **Email 1 open rate** | ~24.8% (partially cut in image) | ~24.8% | N/A | ⚠️ SUSPICIOUS — value read from low-res crop, could be 24.4% or 24.8% |
| **Email 1 headline** | "Commodities trading, simplified" | "Commodities trading, simplified" | N/A | 🕳️ MISSING — recipe not built |
| **Email 2 title** | "Email 2: Key things to know before trading" | Matches | N/A | 🕳️ MISSING — recipe not built |
| **Email 2 open rate** | 21.1% | 21.1% | N/A | ✅ VERIFIED |
| **Email 2 headline** | "Your guide to trading Commodities" (Commodities in green) | Matches | N/A | 🕳️ MISSING — recipe not built |
| **Email 2 content sections** | Global & macro news, Weekly inventory reports, Monthly contract expiries | Matches | N/A | 🕳️ MISSING |
| **Email 2 video link** | "Watch this video to learn more..." | Noted in analysis | N/A | 🕳️ MISSING — video link not captured |
| **Email 3 title** | "Email 3: How to place your first trade" | Matches | N/A | 🕳️ MISSING — recipe not built |
| **Email 3 open rate** | 25.4% | 25.4% | N/A | ✅ VERIFIED |
| **Email 3 headline** | "Your first Commodities trade, made simple" | Matches | N/A | 🕳️ MISSING |
| **Email 3 steps** | Option Chain → Basket order → Quantity/margin → Place order (4 steps) | "4 steps" noted | N/A | 🕳️ MISSING |
| **Email 4 title** | "Email 4: Focused on Crude Oil" | Matches | groww_educational_commodity.json (partial) | ⚠️ SUSPICIOUS — existing recipe is "What moved Crude Oil this March?" not the same email |
| **Email 4 open rate** | 15.3% | 15.3% | N/A | ✅ VERIFIED |
| **Email 4 CTA** | "EXPLORE NOW" (GREEN button) | "EXPLORE NOW" green | Matches existing recipe | ✅ VERIFIED |
| **Email 4 emoji** | "Check how prices are moving today. 👍" (pointing down emoji) | Not captured in analysis | Not in recipe | ⚠️ SUSPICIOUS — emoji present in PDF but not captured |

### PDF 2 (OB-to-FID Onboarding Journey) — Re-extraction vs Analysis

| Field | PDF Source (re-extracted) | Analysis Doc | Recipe Built | Verdict |
|-------|-------------------------|--------------|-------------|---------|
| **Day 0 subject** | "Congratulations on your account setup 👏" | "Congratulations on your account setup" | "Congratulations on your account setup" | ❌ WRONG — **Emoji 👏 missing** from both analysis and recipe |
| **Day 0 greeting** | "Congratulations \<Name\>," | Not captured with personalization token | Recipe uses no personalization in greeting | ❌ WRONG — **PDF shows "\<Name\>" personalization in Day 0 greeting; recipe omits it** |
| **Day 0 app screens** | Search bar, NIFTY50 23,465.60 +264.15, SENSEX 81,475.00 -807.15, Stocks/MF/F&O/IPO tabs | Partially captured | Product grid has 4 categories but no market data | ⚠️ SUSPICIOUS — Market indices (NIFTY/SENSEX) shown in PDF but not in recipe |
| **Day 0 push CTA** | "EXPLORE NOW" | "EXPLORE NOW" | "EXPLORE NOW" | ✅ VERIFIED |
| **Day 1 subject** | "Your first stock is just a few taps away" | Matches | Matches | ✅ VERIFIED |
| **Day 1 push title** | "Ready to buy your first stock?" | Matches | Matches | ✅ VERIFIED |
| **Day 1 push body** | "View trending stocks, today's top movers & popular ETFs — all on Stocks explore. Start investing today." | Matches | Matches | ✅ VERIFIED |
| **Day 1 copy "Most brought"** | PDF text shows "Most brought" (likely typo for "Most bought") | Analysis says "Most Bought" | Recipe says "Most Bought" | ⚠️ SUSPICIOUS — PDF literally says "brought" not "bought"; recipes corrected the typo silently |
| **Day 2 subject** | "Investing in SIPs - The Easy Way" | Matches | Matches | ✅ VERIFIED |
| **Day 2 push title** | "Ready to start your SIP? 💰" | "Ready to start your SIP?" | "Ready to start your SIP?" | ❌ WRONG — **Emoji 💰 missing** from analysis and recipe |
| **Day 3 subject** | "Track, analyse & invest with confidence" | Matches | Matches | ✅ VERIFIED |
| **Day 3 push title** | "📊 Catch the latest market trends" | "Catch the latest market trends" | "Catch the latest market trends" | ❌ WRONG — **Emoji 📊 missing** from analysis and recipe |
| **Day 3 content** | PDF shows: Screener, Intraday, Market trends, News, Events, Watchlists, Limit orders | Analysis captures most | Recipe has: Screener, Market Trends, Screeners (quick), Watchlist | ⚠️ SUSPICIOUS — **News, Events, Intraday, Limit orders sections missing from recipe** |
| **Day 4 subject** | "Discover mutual funds made for you" | Matches | Matches | ✅ VERIFIED |
| **Day 4 push title** | "🤔 Not sure where to start?" | "Not sure where to start?" | "Not sure where to start?" | ❌ WRONG — **Emoji 🤔 missing** |
| **Day 4 push body** | "Explore mutual funds with highest returns over the past 3 years. Start investing today." | Matches | Matches | ✅ VERIFIED |
| **Day 5a subject** | "Making investing in stocks delightful" (from image, "Day5" label) | Matches | Matches | ✅ VERIFIED |
| **Day 5a push title** | "More than just stocks 📈" | "More than just stocks" | "More than just stocks" | ❌ WRONG — **Emoji 📈 missing** |
| **Day 5b subject** | "Making investing in mutual funds delightful" | Matches | Matches | ✅ VERIFIED |
| **Day 5b push title** | "⚡ Calculate fund returns, in seconds" | "Calculate fund returns, in seconds" | "Calculate fund returns, in seconds" | ❌ WRONG — **Emoji ⚡ missing** |
| **Day 6 subject** | "Get Started with F&O in Minutes" | Matches | Matches | ✅ VERIFIED |
| **Day 6 alt subject** | "F&O Trading Made Effortless" | Noted in analysis | Not used in recipe | ⚠️ SUSPICIOUS — alternative subject exists in PDF but not captured as variant |
| **Day 6 push title** | "⚡ Looking for ultra-fast F&O trading?" | "Looking for ultra-fast F&O trading?" | "Looking for ultra-fast F&O trading?" | ❌ WRONG — **Emoji ⚡ missing** |
| **Day 6 push body** | "Experience faster trades, advanced charts, smarter tools & pro-level features — all on Groww F&O." | Matches | Matches | ✅ VERIFIED |
| **Day 7 subject** | "More than just an investment app" | Matches | Matches | ✅ VERIFIED |
| **Day 7 push title** | "🚀 . Cr investors are on Groww" (likely "12+ Cr" with emoji) | "12+ Cr investors are on Groww" | "12+ Cr investors are on Groww" | ❌ WRONG — **Emoji 🚀 missing**, "12+" was interpreted (PDF shows ". Cr" which is garbled OCR for "12+ Cr") |
| **Day 7 "AB INDIA KAREGA GROWW"** | Text shows "AB INDIA KAREGA GROWW" — educational initiative branding | Mentioned in analysis | **Not in recipe** | 🕳️ MISSING — PDF content not captured in recipe |
| **Day 7 "200+ cities"** | "Our offline tour across 200+ cities, spreading financial literacy." | Not in analysis | Not in recipe | 🕳️ MISSING |

---

## 2. WORKFLOW INTEGRITY CHECK

### Steps that exist in recipes but have NO PDF source:

| Recipe | Content | Source in PDF | Verdict |
|--------|---------|--------------|---------|
| All recipes: preheader text | Preheader strings in all 9 recipes | **Not visible in any PDF** — PDFs show visual email design, not preheader | ⚠️ SUSPICIOUS — All preheaders are **fabricated/invented copy**, not from PDFs |
| Day 1: "Browse through 1500+ stocks" | app_screenshot_pair caption | Not in PDF text or images | ❌ WRONG — **Hallucinated copy** |
| Day 2: "Let's take you on a tour of how you can invest in mutual funds" | article_section paragraph | From Day 7/5b text, not Day 2 | ⚠️ SUSPICIOUS — **Copy from wrong email re-used** |
| Day 3: "Swift screeners for a quick entry" | app_screenshot_pair caption_heading | Not visually confirmed in PDF | ⚠️ SUSPICIOUS — May be from PDF but unreadable at this resolution |
| Day 5a: "Get up to 4x leverage. Make the most of it with MTF." | app_screenshot_pair caption | Not explicit in PDF text | ⚠️ SUSPICIOUS — Paraphrased from app screen content, not email copy |
| Day 7: "Daily videos. Real talk. Zero jargon." | social_showcase channel label | Not in PDF text extraction | ⚠️ SUSPICIOUS — Plausible Groww social media tagline but not confirmed in PDF |

### PDF rules/content that have NO corresponding recipe:

| PDF Content | Where in PDF | Implementation | Verdict |
|-------------|-------------|----------------|---------|
| Educational Email 1 (Basics of commodities) | PDF 1, leftmost column | **No recipe exists** | 🕳️ MISSING |
| Educational Email 2 (Key things to know) | PDF 1, second column | **No recipe exists** | 🕳️ MISSING |
| Educational Email 3 (How to place first trade) | PDF 1, third column | **No recipe exists** | 🕳️ MISSING |
| Day 0: Market indices display (NIFTY50/SENSEX) | PDF 2, Day 0 column | Not in recipe | 🕳️ MISSING |
| Day 3: News & Events sections | PDF 2, Day 3 column | Only Screener/Trends/Watchlist in recipe | 🕳️ MISSING |
| Day 3: Limit order feature | PDF 2, Day 3 column | Not in recipe | 🕳️ MISSING |
| Day 5a: Holdings/Positions/Orders tabs | PDF 2, Day 5 column | Not in recipe (recipe jumps to MTF) | 🕳️ MISSING |
| Day 7: "AB INDIA KAREGA GROWW" initiative | PDF 2, Day 7 column | Not in recipe | 🕳️ MISSING |
| Day 7: "200+ cities" educational tour | PDF 2, Day 7 column | Not in recipe | 🕳️ MISSING |
| All emails: "Follow us yet?" social section | PDF 2, visible in most emails | Only in Day 7 recipe | ⚠️ SUSPICIOUS — PDF shows it in most emails, recipe only has it in Day 7 |
| Push notification emojis | PDF 2, bottom of each column | **Stripped from all recipes** | ❌ WRONG — Systematic omission |
| Alternative push notifications | PDF 2, extra push specs shown | Not captured | 🕳️ MISSING |

---

## 3. LOGIC & ACCURACY AUDIT

### Subject line accuracy:
| Day | PDF (exact) | Recipe (exact) | Match? |
|-----|-------------|---------------|--------|
| 0 | "Congratulations on your account setup 👏" | "Congratulations on your account setup" | ❌ Missing emoji |
| 1 | "Your first stock is just a few taps away" | "Your first stock is just a few taps away" | ✅ |
| 2 | "Investing in SIPs - The Easy Way" | "Investing in SIPs - The Easy Way" | ✅ |
| 3 | "Track, analyse & invest with confidence" | "Track, analyse & invest with confidence" | ✅ |
| 4 | "Discover mutual funds made for you" | "Discover mutual funds made for you" | ✅ |
| 5a | Visual only, text garbled | "Making investing in stocks delightful" | ⚠️ Unverifiable |
| 5b | Visual only | "Making investing in mutual funds delightful" | ⚠️ Unverifiable |
| 6 | "Get Started with F&O in Minutes" | "Get Started with F&O in Minutes" | ✅ |
| 7 | "More than just an investment app" | "More than just an investment app" | ✅ |

### Push notification emoji audit:
**Every single push notification title has emojis in the PDF that were stripped:**

| Day | PDF push title | Recipe push title | Emoji stripped? |
|-----|---------------|------------------|----------------|
| 0 | "Congrats! Your account setup is complete 🎉" | "Congrats! Your account setup is complete" | ❌ YES — 🎉 stripped |
| 2 | "Ready to start your SIP? 💰" | "Ready to start your SIP?" | ❌ YES — 💰 stripped |
| 3 | "📊 Catch the latest market trends" | "Catch the latest market trends" | ❌ YES — 📊 stripped |
| 4 | "🤔 Not sure where to start?" | "Not sure where to start?" | ❌ YES — 🤔 stripped |
| 5a | "More than just stocks 📈" | "More than just stocks" | ❌ YES — 📈 stripped |
| 5b | "⚡ Calculate fund returns, in seconds" | "Calculate fund returns, in seconds" | ❌ YES — ⚡ stripped |
| 6 | "⚡ Looking for ultra-fast F&O trading?" | "Looking for ultra-fast F&O trading?" | ❌ YES — ⚡ stripped |
| 6 alt | "⚡ Trade F&O in milliseconds" | Not captured | ❌ YES |
| 7 | "🚀 12+ Cr investors are on Groww" | "12+ Cr investors are on Groww" | ❌ YES — 🚀 stripped |

**Root cause**: CLAUDE.md rule says "Only use emojis if the user explicitly requests it." This was applied to push notification metadata even though the PDFs explicitly show emojis as part of the push copy. Push notifications are NOT Jinja2 templates — they're metadata for the campaign team and should preserve the source exactly.

### CTA button accuracy:
| Day | PDF CTA text | Recipe CTA text | PDF CTA color | Recipe CTA style | Verdict |
|-----|-------------|----------------|---------------|-----------------|---------|
| 0 | Not clearly visible | "EXPLORE GROWW" | Green | green | ⚠️ Unverifiable |
| 1 | Not clearly visible | "EXPLORE STOCKS" | Green | green | ⚠️ Unverifiable |
| 2 | "START SIP" visible in some views | "EXPLORE MUTUAL FUNDS" | Green | green | ⚠️ SUSPICIOUS — PDF may show "START SIP" not "EXPLORE MUTUAL FUNDS" |
| 3 | Not clearly visible | "EXPLORE STOCKS" | Green | green | ⚠️ Unverifiable |
| 6 | "TRY IT NOW" / "EXPLORE F&O" | "TRY IT NOW" | Blue | blue | ✅ |
| 7 | Multiple CTAs visible | "EXPLORE GROWW" | Green | green | ⚠️ Multiple CTAs in PDF, recipe has only 1 |

### Day-to-content mapping accuracy:
| Day | PDF shows this content | Recipe implements | Verdict |
|-----|----------------------|-------------------|---------|
| 0 | Welcome + product overview + Nifty/Sensex | Welcome + product grid (no market data) | ⚠️ Partial |
| 1 | Stock search + trending + buy flow (detailed) | Search + detail + 2-step buy | ⚠️ Simplified |
| 2 | MF search + popular + SIP flow | Search + popular + 2-step SIP | ⚠️ Simplified |
| 3 | 6 tools (Screener, Intraday, Trends, News, Events, Watchlist) + Limit orders | 4 tools (Screener, Trends, Screeners, Watchlist) | ❌ WRONG — Missing News, Events, Intraday, Limit orders |
| 4 | Sort/filter + Collections + Compare + Calculator + Import | Sort + Collections + Compare + Import | ⚠️ Missing SIP calculator |
| 5a | Holdings + Positions + MTF + ETFs + Intraday + IPO | MTF + IPO + ETFs + Intraday | ⚠️ Missing Holdings/Positions |
| 5b | Trending + Fund detail + Performance + Popular + "crowd favourite" | Trending + Popular + Performance + Collections | ⚠️ Close but reworded |
| 6 | Index selection + Option chain + Order + Charts + Positions | 3-step instruction + Charts | ✅ Adequate |
| 7 | Brand story + "AB INDIA KAREGA GROWW" + 200+ cities + Digest + YouTube + Social | Brand story + Digest + YouTube | ⚠️ Missing educational initiative + offline tour |

---

## 4. EDGE CASES & GAPS

### Empty/null/missing data handling:

| Scenario | Handled? | Evidence |
|----------|---------|---------|
| `app_screenshot_pair` with no `caption_heading` | ✅ Yes | Template uses `d.get('caption_heading')` |
| `app_screenshot_pair` with no `caption` | ✅ Yes | Template uses `d.get('caption')` |
| `product_category_grid` with odd number of categories | ✅ Yes | Template renders empty cell for odd item |
| `social_showcase` with no channels | ✅ Yes | Template loops over empty list safely |
| `push_notification` field missing from recipe meta | ✅ Yes | Field is metadata only, assembler ignores it |
| `{{name}}` personalization token | ❌ No | Recipes use literal `{{name}}` but no merge tag system exists. Assembler renders it literally as "{{name}}" in HTML output. This is a **Netcore/ESP merge tag** that should be `{{name}}` or similar — needs validation that the ESP handles it. |
| Missing image URLs (placeholder fails to load) | ⚠️ Partial | Placeholder images work for testing but will show "placehold.co" in production |

### PDF scenarios silently ignored:

| PDF Feature | Status |
|------------|--------|
| **Alternative subject lines** — Day 6 shows two subject options | 🕳️ MISSING — Only one captured |
| **Alternative push notifications** — Multiple push specs shown for some days | 🕳️ MISSING — Only primary captured |
| **"Follow us yet?" appears in MOST emails** — not just Day 7 | 🕳️ MISSING — Only implemented in Day 7 recipe |
| **Conditional branching** — Does user get stocks vs MF email based on behavior? | ⚠️ No branching logic detected in PDF, but Day 5 splits into 5a/5b, suggesting some segmentation |
| **Educational series emails 1-3** — Not built as recipes at all | 🕳️ MISSING — Only Email 4 partially matches existing commodity recipe |

---

## 5. FINAL VERDICT TABLE

### Onboarding Recipes:

| Recipe | Subject | Push emojis | Copy accuracy | Content completeness | Block structure | Overall |
|--------|---------|-------------|---------------|---------------------|----------------|---------|
| Day 0 Welcome | ❌ Missing 👏 | ❌ Missing 🎉 | ⚠️ Missing \<Name\> personalization | ⚠️ Missing market indices | ✅ | ⚠️ SUSPICIOUS |
| Day 1 Stocks | ✅ | ⚠️ No emoji issues this day | ⚠️ Some copy fabricated | ⚠️ Simplified buy flow | ✅ | ⚠️ SUSPICIOUS |
| Day 2 SIP | ✅ | ❌ Missing 💰 | ⚠️ Cross-contaminated copy | ⚠️ Simplified SIP flow | ✅ | ⚠️ SUSPICIOUS |
| Day 3 Tools | ✅ | ❌ Missing 📊 | ⚠️ Partial | ❌ Missing 3 of 7 sections | ✅ | ❌ WRONG |
| Day 4 MF Explore | ✅ | ❌ Missing 🤔 | ⚠️ Acceptable | ⚠️ Missing SIP calculator | ✅ | ⚠️ SUSPICIOUS |
| Day 5a Stocks Features | ⚠️ Unverifiable | ❌ Missing 📈 | ⚠️ Paraphrased | ⚠️ Missing Holdings/Positions | ✅ | ⚠️ SUSPICIOUS |
| Day 5b MF Features | ⚠️ Unverifiable | ❌ Missing ⚡ | ⚠️ Acceptable | ⚠️ Reworded sections | ✅ | ⚠️ SUSPICIOUS |
| Day 6 F&O | ✅ | ❌ Missing ⚡ | ✅ Good match | ✅ Adequate | ✅ | ⚠️ SUSPICIOUS (emoji only) |
| Day 7 Brand | ✅ | ❌ Missing 🚀 | ✅ Good match | ⚠️ Missing AB INDIA KAREGA GROWW, 200+ cities | ✅ | ⚠️ SUSPICIOUS |

### Educational Series:

| Email | Recipe exists? | Verdict |
|-------|---------------|---------|
| Edu-1: Basics of commodities | ❌ No | 🕳️ MISSING |
| Edu-2: Key things to know | ❌ No | 🕳️ MISSING |
| Edu-3: How to place first trade | ❌ No | 🕳️ MISSING |
| Edu-4: Focused on Crude Oil | ⚠️ Partially (existing commodity recipe is different email) | ⚠️ SUSPICIOUS |

### New Blocks:

| Block | Template quality | Data handling | Edge cases | Overall |
|-------|-----------------|---------------|------------|---------|
| app_screenshot_pair | ✅ Good | ✅ Optional fields handled | ✅ | ✅ VERIFIED |
| product_category_grid | ✅ Good (nesting fixed) | ✅ Odd count handled | ✅ | ✅ VERIFIED |
| social_showcase | ✅ Good (nesting fixed) | ✅ Empty channels handled | ✅ | ✅ VERIFIED |

### Analysis Document (OB_TO_FID_ANALYSIS.md):

| Section | Verdict |
|---------|---------|
| Email journey map | ⚠️ SUSPICIOUS — Day assignments mostly correct but content sections incomplete for Days 3, 5a, 7 |
| Push notification specs | ❌ WRONG — All emojis systematically stripped |
| Block sequences | ⚠️ SUSPICIOUS — Simplified vs PDF, missing sections |
| Design patterns | ✅ VERIFIED — Patterns correctly identified |
| Screenshots needed | ✅ VERIFIED — Comprehensive list |

---

## CRITICAL ISSUES SUMMARY (Action Required)

### P0 — Must Fix:

1. **All push notification emojis stripped** (9 of 9 recipes affected). PDF explicitly shows emojis in push titles. These are campaign metadata, not template output — the no-emoji rule should not apply here.

2. **Day 0 subject missing 👏 emoji**. PDF clearly shows "Congratulations on your account setup 👏".

3. **Educational emails 1-3 not built**. The analysis doc describes them but no recipes were created. The plan said "12 email types" but only 9 onboarding + 0 educational new = 9 built. 3 educational emails are completely missing.

4. **Day 3 recipe missing 3 of 7 content sections** from PDF (News, Events, Intraday, Limit orders not implemented).

### P1 — Should Fix:

5. **Day 0 missing `<Name>` personalization** in greeting. PDF shows "Congratulations \<Name\>," but recipe greeting has no personalization.

6. **Day 7 missing "AB INDIA KAREGA GROWW"** educational initiative section and "200+ cities" offline tour content.

7. **Day 5a missing Holdings/Positions/Orders** as first content section (recipe jumps directly to MTF).

8. **Day 4 missing SIP calculator** section from PDF.

9. **"Follow us yet?" section** appears in most PDF emails but only implemented in Day 7 recipe.

10. **All preheader text is invented** — not from PDFs. This may be intentional (preheaders aren't shown in design PDFs) but should be flagged.

### P2 — Nice to Fix:

11. **Day 2 CTA might be "START SIP"** not "EXPLORE MUTUAL FUNDS" — needs higher-res verification.

12. **Alternative subject lines and push notifications** exist in PDF but not captured as variants.

13. **Day 1 "Most brought" vs "Most bought"** — PDF literally says "brought" (typo), recipes silently corrected to "bought". Acceptable but undocumented.

---

**End of audit. No sugarcoating. 3 critical issues, 6 should-fix, 3 nice-to-fix.**
