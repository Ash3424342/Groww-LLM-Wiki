# OB-to-FID Email Journey Analysis

> **Source**: `OB to FID_Feb_v3.pdf` (Groww onboarding design map, Feb 2026)
> **Analyzed**: 2026-04-06
> **Purpose**: Complete reference for building onboarding + educational email recipes

---

## Overview

Two email programs mapped:
1. **Educational Series** — 4 commodity-focused emails (standalone, not day-sequenced)
2. **Onboarding Journey (OB-to-FID)** — 8 emails across Day 0–7 post account setup

Combined: **12 email types** to be built as recipes.

---

## Part 1: Educational Email Series

### Email Edu-1: Basics of Commodities Trading
- **Open rate**: ~24.8%
- **Subject**: (not specified in design)
- **Hero**: "Commodities trading, simplified"
- **Content**: Intro to what commodities are, why trade them, basics of MCX
- **CTA**: Green — "EXPLORE COMMODITIES"
- **Blocks**: header_logo → hero_text → article_section (intro) → chart_image (app screenshots) → article_section (basics) → cta_button → social_proof_banner → footer_standard
- **Notes**: Uses app screenshots showing the commodities section. No factor cards.

### Email Edu-2: Key Things to Know Before Trading
- **Open rate**: 21.1%
- **Subject**: (not specified)
- **Hero**: "Your guide to trading Commodities"
- **Content**: Global & macro news, Weekly inventory reports, Monthly contract expiries
- **App screenshots**: News section, Natural Gas chart, contract expiry table
- **CTA**: Green — "EXPLORE COMMODITIES"
- **Blocks**: header_logo → hero_text → hero_image (illustration) → article_section (intro) → app_screenshot_pair (news section) → article_section (inventory reports) → app_screenshot_pair (chart) → article_section (contract expiries) → app_screenshot_pair (expiry table) → cta_button → social_proof_banner → footer_standard
- **Notes**: Heavy use of left-text/right-screenshot alternating layout. Video link: "Watch this video"

### Email Edu-3: How to Place Your First Trade
- **Open rate**: 25.4% (highest in series)
- **Subject**: (not specified)
- **Hero**: "Your first Commodities trade, made simple"
- **Content**: Step-by-step — Hit Option Chain → Found your strike? Basket order → Set quantity & margin → Place order
- **App screenshots**: Option Chain screen, Basket order toggle, Quantity/margin screen, Order confirmation
- **CTA**: Green — "EXPLORE COMMODITIES"
- **Blocks**: header_logo → hero_text → article_section (intro) → step_instruction (4 steps with screenshots) → cta_button → social_proof_banner → footer_standard
- **Notes**: Perfect match for `step_instruction` block. 4 steps with alternating screenshots.

### Email Edu-4: Focused on Crude Oil
- **Open rate**: 15.3% (lowest — deep-dive content)
- **Subject**: (not specified)
- **Hero**: (not visible, likely "What moved Crude Oil?")
- **Content**: Two ways to trade Crude Oil — Crude Oil vs Crude Oil Mini contracts
- **App screenshots**: Listing card with All Commodities filter, Crude Oil + Mini contracts
- **CTA**: Green — "EXPLORE NOW"
- **Blocks**: header_logo → article_section (intro) → chart_image (listing card) → article_section (closing) → cta_button → social_proof_banner → footer_standard
- **Notes**: This is essentially the existing `groww_educational_commodity` recipe pattern (already built).

---

## Part 2: Onboarding Journey (OB-to-FID)

### Day 0: Welcome Email
- **Subject**: "Congratulations on your account setup"
- **Push notification**: Title: "Congrats! Your account setup is complete", Body: "Tap to start investing in Stocks, Mutual Funds & more on Groww.", CTA: "EXPLORE NOW"
- **Hero**: "Welcome to the world of investing"
- **Content**: "Congratulations <Name>," personalized greeting → Product category overview (Stocks, MF, F&O, IPO) → App screenshots of each section → "How about we take you on a quick tour of Groww?"
- **Key UI elements**: Search bar, Nifty/Sensex tickers, product category grid (Stocks, Mutual Funds, F&O, IPO)
- **CTA**: Green — "EXPLORE GROWW"
- **Blocks**: header_logo → hero_text → article_section (congratulations) → product_category_grid (4 categories) → article_section (tour intro) → chart_image (app home screenshot) → cta_button → social_proof_banner → footer_standard
- **New block needed**: `product_category_grid`

### Day 1: First Stock Purchase
- **Subject**: "Your first stock is just a few taps away"
- **Push notification**: Title: "Ready to buy your first stock?", Body: "View trending stocks, today's top movers & popular ETFs — all on Stocks explore. Start investing today.", CTA: "GET STARTED"
- **Hero**: "Buying your first stock? We'll guide you"
- **Content**: "Hello <Name>," → Pick your stock (search or trending) → Look at price → Click buy → Enter quantity → Confirm order
- **App screenshots**: Search bar, trending stocks, stock detail page, buy form, order confirmation
- **CTA**: Green — "EXPLORE STOCKS"
- **Blocks**: header_logo → hero_text → article_section (greeting + pick stock) → app_screenshot_pair (search) → article_section (trending) → app_screenshot_pair (stock detail) → step_instruction (buy flow: 3-4 steps) → cta_button → social_proof_banner → footer_standard
- **New block needed**: `app_screenshot_pair`

### Day 2: First SIP
- **Subject**: "Investing in SIPs - The Easy Way"
- **Push notification**: Title: "Ready to start your SIP?", Body: "Explore popular funds, high returns & best SIP funds collections — all on Mutual fund explore. Start investing today.", CTA: "GET STARTED"
- **Hero**: "First SIP made simple, here's how"
- **Content**: Pick a mutual fund (search or popular) → Check past performance → Set SIP amount → Confirm order
- **App screenshots**: MF search, popular funds, fund detail with chart, SIP setup form
- **CTA**: Green — "EXPLORE MUTUAL FUNDS"
- **Blocks**: header_logo → hero_text → article_section (greeting + pick fund) → app_screenshot_pair (search) → app_screenshot_pair (popular funds) → step_instruction (SIP flow: 3-4 steps) → cta_button → social_proof_banner → footer_standard

### Day 3: Stocks Tools & Analysis
- **Subject**: "Track, analyse & invest with confidence"
- **Push notification**: Title: "Catch the latest market trends", Body: "Track trending stocks & top movers. Analyse, add to your watchlist & set alerts.", CTA: "EXPLORE NOW"
- **Hero**: "Making investing in stocks delightful"
- **Content**: "Hello <Name>," → Products and tools → Screener (sort/filter stocks) → Market trends (gainers/losers) → News & Events → Watchlists → "Or better, set the price you want to buy the stock at"
- **App screenshots**: Screener, Market trends, News section, Events, Watchlist, Limit order
- **CTA**: Green — "EXPLORE STOCKS"
- **Blocks**: header_logo → hero_text → article_section (greeting + intro) → app_screenshot_pair (screener) → app_screenshot_pair (market trends) → app_screenshot_pair (news) → app_screenshot_pair (watchlist) → article_section (limit orders) → app_screenshot_pair (limit order) → cta_button → social_proof_banner → footer_standard

### Day 4: Mutual Fund Discovery
- **Subject**: "Discover mutual funds made for you"
- **Push notification**: Title: "Not sure where to start?", Body: "Explore mutual funds with highest returns over the past 3 years. Start investing today.", CTA: "START TODAY"
- **Hero**: "Making investing in mutual funds delightful"
- **Content**: "Hello <Name>," → Sort and find top performing funds → Collections (SIP with 500, Tax saving, Large cap...) → Compare funds → SIP calculator → Import external funds
- **App screenshots**: Fund sort/filter, Collections grid, Fund comparison, SIP calculator, Import screen
- **CTA**: Green — "EXPLORE MUTUAL FUNDS"
- **Blocks**: header_logo → hero_text → article_section (greeting) → app_screenshot_pair (sort/filter) → app_screenshot_pair (collections) → app_screenshot_pair (compare) → app_screenshot_pair (calculator) → article_section (import) → app_screenshot_pair (import) → cta_button → social_proof_banner → footer_standard

### Day 5a: Stocks Features Deep-Dive
- **Subject**: "Making investing in stocks delightful"
- **Push notification**: Title: "More than just stocks", Body: "Invest in ETFs, apply for IPOs & trade with MTF — all in one place.", CTA: "Explore stocks"
- **Content**: Holdings, Positions, Orders → MTF (margin trading) → ETFs → Intraday → IPO → Product & Tools
- **App screenshots**: Holdings screen, MTF, ETF explorer, Intraday screener, IPO section
- **CTA**: Green — "EXPLORE STOCKS"
- **Blocks**: header_logo → hero_text → article_section (intro) → app_screenshot_pair (holdings) → app_screenshot_pair (MTF) → app_screenshot_pair (ETFs) → app_screenshot_pair (intraday) → app_screenshot_pair (IPO) → cta_button → social_proof_banner → footer_standard

### Day 5b: MF Features Deep-Dive
- **Subject**: "Making investing in mutual funds delightful"
- **Push notification**: Title: "Calculate fund returns, in seconds", Body: "Use the SIP calculator to calculate how much your investment could grow over time.", CTA: "CHECK OUT NOW"
- **Content**: See trending funds → Fund details (NAV, returns, ratings) → Check past performance → "Check out the crowd favourite of all time" → Popular funds
- **App screenshots**: Trending funds, fund detail page, performance chart, popular list
- **CTA**: Green — "EXPLORE POPULAR FUNDS"
- **Blocks**: header_logo → hero_text → article_section (intro) → app_screenshot_pair (trending) → app_screenshot_pair (fund detail) → app_screenshot_pair (performance) → app_screenshot_pair (popular) → cta_button → social_proof_banner → footer_standard

### Day 6: F&O Trading
- **Subject**: "Get Started with F&O in Minutes" / "F&O Trading Made Effortless"
- **Push notification**: Title: "Looking for ultra-fast F&O trading?", Body: "Experience faster trades, advanced charts, smarter tools & pro-level features — all on Groww F&O.", CTA: "GET STARTED"
- **Hero**: "Making trading in F&O delightful" / "Trade F&O in just a few steps"
- **Content**: Choose Index → Select contract → Quick trades → Advanced Charts → Positions management
- **App screenshots**: Index selection (NIFTY/BANKNIFTY/FINNIFTY), Option chain, Trade form, Charts, Positions
- **CTA**: Blue — "TRY IT NOW" / "EXPLORE F&O"
- **Blocks**: header_logo → hero_text → article_section (intro) → step_instruction (select index → option chain → quick trade → confirm) → app_screenshot_pair (charts) → app_screenshot_pair (positions) → cta_button (blue) → social_proof_banner → footer_standard
- **Notes**: Uses blue CTA (feature/product focus)

### Day 7: Brand Story & Beyond the App
- **Subject**: "More than just an investment app"
- **Push notification**: Title: "12+ Cr investors are on Groww", Body: "Don't wait — start your investing journey on Groww today.", CTA: "START TODAY"
- **Hero**: "Our world beyond the app"
- **Content**: "Some say, we are an investment app. We say, we're here to change how India thinks about finance and investing." → Brand story (started 2016) → Educational initiatives ("AB INDIA KAREGA GROWW") → GROWW DIGEST (weekly market guide) → YouTube channel → Social media ("Follow us yet?") → "Our social is a treasure box of finance content"
- **App screenshots**: None (brand-focused, not product)
- **CTA**: Green — "EXPLORE GROWW" + "READ NOW" + "WATCH NOW"
- **Blocks**: header_logo → hero_text → article_section (brand story) → divider → article_section (educational initiatives) → chart_image (event photo) → divider → article_section (digest intro) → chart_image (digest preview) → social_showcase (YouTube + social channels) → cta_button → social_proof_banner → footer_standard
- **New block needed**: `social_showcase`

---

## Part 3: New Blocks Required

### 1. `app_screenshot_pair` (HIGH PRIORITY)
The dominant pattern in onboarding emails — text on one side, app screenshot on the other.

**Data structure**:
```json
{
  "caption": "Pick your stock — search or browse trending",
  "caption_heading": "Pick your stock",
  "image_url": "https://...",
  "image_alt": "Groww app stocks screen",
  "layout": "left-text" | "right-text",
  "image_width": 240
}
```

### 2. `product_category_grid` (Day 0 only)
2-column grid of product categories with icons.

**Data structure**:
```json
{
  "categories": [
    {"icon_url": "https://...", "title": "Stocks", "subtitle": "1500+ stocks to invest in", "url": "https://groww.in/stocks"},
    {"icon_url": "https://...", "title": "Mutual Funds", "subtitle": "5000+ funds, SIP from ₹500", "url": "https://groww.in/mutual-funds"}
  ]
}
```

### 3. `social_showcase` (Day 7, potentially others)
"Follow us yet?" section with social channel showcase.

**Data structure**:
```json
{
  "heading": "Follow us yet?",
  "description": "Our social is a treasure box of finance content.",
  "channels": [
    {"name": "YOUTUBE", "label": "Daily videos. Real talk. Zero jargon.", "url": "https://youtube.com/...", "cta": "WATCH NOW"},
    {"name": "READ NOW", "label": "Your weekly guide to the markets, simplified.", "url": "https://groww.in/digest", "cta": "READ NOW"}
  ]
}
```

---

## Part 4: Push Notification Specs

| Day | Title | Body | CTA |
|-----|-------|------|-----|
| 0 | Congrats! Your account setup is complete | Tap to start investing in Stocks, Mutual Funds & more on Groww. | EXPLORE NOW |
| 1 | Ready to buy your first stock? | View trending stocks, today's top movers & popular ETFs — all on Stocks explore. Start investing today. | GET STARTED |
| 2 | Ready to start your SIP? | Explore popular funds, high returns & best SIP funds collections — all on Mutual fund explore. Start investing today. | GET STARTED |
| 3 | Catch the latest market trends | Track trending stocks & top movers. Analyse, add to your watchlist & set alerts. | EXPLORE NOW |
| 4 | Not sure where to start? | Explore mutual funds with highest returns over the past 3 years. Start investing today. | START TODAY |
| 5a | More than just stocks | Invest in ETFs, apply for IPOs & trade with MTF — all in one place. | Explore stocks |
| 5b | Calculate fund returns, in seconds | Use the SIP calculator to calculate how much your investment could grow over time. | CHECK OUT NOW |
| 6 | Looking for ultra-fast F&O trading? | Experience faster trades, advanced charts, smarter tools & pro-level features — all on Groww F&O. | GET STARTED |
| 7 | 12+ Cr investors are on Groww | Don't wait — start your investing journey on Groww today. | START TODAY |

Alternative push notifications mentioned:
- "Stocks, Mutual Funds & more" — Invest your way. Start your journey with Groww today. → EXPLORE NOW
- "Trade F&O in milliseconds" — Faster execution, advanced charts & option chain — all on Groww. → EXPLORE F&O

---

## Part 5: Design Patterns Observed

1. **Personalization**: All onboarding emails start with "Hello <Name>," or "Congratulations <Name>,"
2. **Alternating screenshot layout**: Text left / screenshot right, then text right / screenshot left
3. **Step-by-step flows**: Day 1 (buy stock), Day 2 (start SIP), Day 6 (trade F&O) use numbered steps
4. **CTA colors**: Green for explore/invest, Blue for features/trading
5. **Social proof**: "INDIA'S NO.1 STOCK BROKER" + "Loved and trusted by 1 Crore+ active investors"
6. **Footer consistency**: All emails use identical SEBI disclaimer + unsubscribe footer
7. **No fear/hype language**: All copy is neutral, informational, action-oriented
8. **App screenshots are the hero**: In onboarding, screenshots ARE the content — minimal text

---

## Part 6: App Screenshots Needed

Each email requires specific app screenshots. These must come from the design team or be captured from the app:

| Email | Screenshots needed |
|-------|-------------------|
| Day 0 | Home screen, product categories |
| Day 1 | Search bar, trending stocks, stock detail, buy form, order confirmation |
| Day 2 | MF search, popular funds, fund detail, SIP setup, SIP confirmation |
| Day 3 | Screener, market trends, news, events, watchlist, limit order |
| Day 4 | Fund sort/filter, collections, compare, SIP calculator, import |
| Day 5a | Holdings, MTF, ETFs, intraday, IPO |
| Day 5b | Trending funds, fund detail, performance chart, popular list |
| Day 6 | Index selection, option chain, trade form, charts, positions |
| Day 7 | Event photos, Groww Digest preview |
| Edu 1-3 | Commodities section, option chain, basket order, order screens |

**Total**: ~50+ unique app screenshots. Use placeholder URLs until real assets are available.

---

## Part 7: Recipe Priority

| Priority | Recipe | Depends on | Notes |
|----------|--------|-----------|-------|
| P0 | groww_onboarding_welcome (Day 0) | product_category_grid block | First email in funnel |
| P0 | groww_onboarding_stocks (Day 1) | app_screenshot_pair block | Highest conversion potential |
| P0 | groww_onboarding_sip (Day 2) | app_screenshot_pair block | MF acquisition |
| P1 | groww_onboarding_stocks_tools (Day 3) | app_screenshot_pair block | |
| P1 | groww_onboarding_mf_explore (Day 4) | app_screenshot_pair block | |
| P1 | groww_onboarding_stocks_features (Day 5a) | app_screenshot_pair block | |
| P1 | groww_onboarding_mf_features (Day 5b) | app_screenshot_pair block | |
| P2 | groww_onboarding_fno (Day 6) | step_instruction block (exists) | |
| P2 | groww_onboarding_brand (Day 7) | social_showcase block | Brand, not conversion |
