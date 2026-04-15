# PDF Processing Log

Track of all 62 PDFs — what was read, what was extracted, which files were updated.

**Legend:** ✅ Done | 🔄 In Progress | ⬜ Pending

**STATUS: ALL 62 PDFs COMPLETE ✅ — Completed 2026-03-27**

Files updated: `Growth Vertical - Master Reference.md` · `Growth Vertical - Concepts & Notes.md` · `groww-context.md` (skill context store)

Notes on image-heavy docs (limited extraction): #38 NARAD Roadmap, #52 MTF GTM, #60 Rakhi Exp results, #62 Competitor Screenshots — content was screenshots/diagrams; extracted all available text from headings and surrounding context.

---

## BATCH 1 — Strategy & Foundations
| # | PDF | Status | Key Extractions |
|---|-----|--------|----------------|
| 1 | Engagement - Long term strategy Doc | ✅ | 3-part strategy (off-app→on-app→combined); Business Layer (1 RID + 1 CrossSell/user/month); CLTV×Capacity model; Campaign Affinity/MAB (~50% TTU); Low/Mid active users = higher incremental lift |
| 2 | Retention Deepdive | ✅ | TTU-MAU% ~73%, App-Keep TTU MAU% ~87% (ATH Jan 2024); Resurrection gap at Day 5; M3/M6/M12 retention on uptrend; App Affinity = DAU/MAU |
| 3 | Growth-Cross Sell Metric finalization | ✅ | PPU deprecated → Active PPU recommended; Active PPU product scope (Stocks, F&O, MF, Credit, UPI, BBPS, Insurance); CNTU = Cross-sell NTU |
| 4 | Campaign impact measurement & attribution | ✅ | GCG = 5% holdout, 30-day window; MTA for long-window conversions; Incremental uplift calculation |
| 5 | Incrementality Measurement- Engagement | ✅ | Non-TTU uplift: +55-60% DAU, +75% NTU at Day 15 vs GCG; Personalized TTU: +11% peak DAU vs GCG; 52W H/L CTR 12% = 4X generic |
| 6 | NARAD vs other Mar-tech CLM platforms | ✅ | NARAD = in-house CRM; WebEngage = push throughput at scale; image-heavy doc (table comparisons were screenshots, not extractable text) |

## BATCH 2 — Activation Funnel
| # | PDF | Status | Key Extractions |
|---|-----|--------|----------------|
| 7 | Install to NTU- User Activation journey | ✅ | JFM-24 focus areas; push for 7D post-install; FB+RCS as add. channels; affinity models post/pre-OB; M1 retention levers (uninstall, M0 NTU, M1 MAU); cold start problem; PP visits as milestone |
| 8 | Sign-up to OB Funnel Experiments | ✅ | Two WA experiments on onboarding: Esign (30% uplift → live), IFSC→BV (4% → reverted); Account opening cost Rs.44/user; WA funnels doc table |
| 9 | User Reactivation & NTU | ✅ | WA vs Remarketing experiment (3 weeks); ~17% inactive non-investors have app; WA FID CAC = 1/5th (Non-OB), 1/10th (OB) of remarketing; scaled to 300K users |
| 10 | Increase NTU from Inactive base | ✅ | L30D/L150D+ cohort definitions; push reachability drops to ~1.5% for L150D+; 30% MAU from L150D+ via Google ads; old CAC 6000+; PPvisit≥2/5 as targeting signal |
| 11 | NTU -_CNTU conversion | ✅ | ~70% NTU→CNTU by 3M; ~80% by 24M; First 30D = awareness/discovery; Post 30D = CNTU milestone targets (MF: SIP mandate; CNC/F&O/MIS: Buy>X); guardrails needed |
| 12 | Whatsapp Strategy for Signup__NTU funnel | ✅ | Why WA: 50% non-investors not push-reachable; PN CTR 1-2%; WA pricing BIC 73p, UIC 33p; industry frequency benchmarks; non-happy OB flows deployed; COSMOS mentioned |
| 13 | WhatsApp Experiment for Onboarding Drop off flows | ✅ | Exact funnel drop rates confirmed; 26% Signup→Esign in 7D; ~200 incremental Esigns/day; ₹145 cost/conversion; WA live 100% in COSMOS; D7<D1 uplift (WA prepones) |

## BATCH 3 — TTU & Retention
| # | PDF | Status | Key Extractions |
|---|-----|--------|----------------|
| 14 | TTU Retention- Next steps | ✅ | Retention Propensity Model (deciles 1-10); High Risk (Jan MAU D1,2,3) vs High Potential (Jan Inactive D8,9,10); email reachability high across all deciles; push low for inactive; WA/RCS for low-PN-reach base; WA brings app opens not transactions; WA PU cost Rs.75 |
| 15 | TTU- Ressurection | ✅ | Early diagnostic doc; brainstorm questions (app install, churn type, reachability, AUM, product mix, PPI, losses, NPS); potential levers: portfolio WA, Digest, GrowwFlix, loans, rewards, Pay push, new features |
| 16 | User Reactivation for Non-TTU (WhatsApp + Remarketing) | ✅ | Scale-up experiment (D30+ inactive); TG split: Engagement + Remarketing (Invest+Pay); WA freq 3/month (1/week); 1-month duration; NTU uplift NOT statistically significant yet (experiment maturing) |
| 17 | Product Level Affinity experiment_ Improve DTU from TTU | ✅ | ML affinity vs BAU (50/50 split); same content & freq, only targeting changed; PN CTR +6%, DTU +1.3%, Sessions +7%; mid/low-active uplift; high-active TTU: NO uplift; BQ→AM→WebEngage pipeline; FC at segment level |
| 18 | Next best product experiment for TTU | ✅ | Cross-sell ML model (PPU=1 users); F&O, MF, CNC, MIS; 2-week experiment; mixed results (CTR/DAU down, cross-sell product DAU up in some cohorts); 14D window too short → 30D needed; Pay & Credit to be added |
| 19 | Revive_ Portfolio updates over WA for TTU resurrection | ✅ | 3.2M TTU become inactive/month; WA portfolio update to inactive>30D & AUM>Rs.100; Tue (MF) + Wed (CNC) weekly cron; Jan experiment → Apr full rollout → May-Jun 2nd rollout |
| 20 | IPO & SGB Comms. for TTU - SOP | ✅ | SGB=Sovereign Gold Bond (confirmed); IPO targeting via PA calendar; intent segmentation (applied L3M, PPvisit>3 L7D, Apply clicked); IPO CTR 4% TTU; SGB CTR 3-4.5%; IPO Corner property; Pre-apply NOT allowed in comms |

## BATCH 4 — Personalization & ML
| # | PDF | Status | Key Extractions |
|---|-----|--------|----------------|
| 21 | _WIP_User Personalisation- Category level for Invest TTU | ✅ | 4 lifecycle stages; 2 models/product (RID + CrossSell); 12 total models; daily/fortnightly refresh; Analytics rule layer on top of ML |
| 22 | Product Affinity - Segment personalisation- OB__NTU activation | ✅ | @Preksha Vyas; D7+ non-TTU; CTR↑ Sessions↑ but NO FID uplift; F&O best (73% accuracy), MF negative (55% accuracy); Pay to be added |
| 23 | Instrument Level Affinity- For NTU activation | ✅ | @Amit Kumar; 362K users; Top 10 stocks: 3% DAU uplift (minimal NTU); Top 11-50: 23% CTR but NO DAU → paused; Top 10 → automating into in-house CM |
| 24 | F&O TTU-User Personalisation - Instrument level affinity | ✅ | @Himanshu; affinity = max trades in given index; PN CTR +6-10%, User CTR +6-9%; DAU/Session minimal; mid/low intent users benefit most |
| 25 | MF TTU- User personalisation- Purchase abandonment funnel | ✅ | @Ritvik Pandey; buy intent ≥2 clicks L30D; SIP 260K (60%) + Lumpsum 160K (40%); curiosity content (no perf data); CTR↑ all cohorts, MF DAU↑ 3/4, PP Visits↑ 4/4; +7,800 lumpsum orders at scale (+5%) |
| 26 | Contextual Multi-Arm Bandits_ Smart Push Notifications | ✅ | Thompson Sampling; V0: 1→6 campaigns, 34% CTR uplift after warmup; V1: 40% CTR + 3% DTU; 5 C-MABs live for TTU; 3 Non-TTU coming; 2D lag in affinity data (EMS to fix) |
| 27 | Contextual Multi-Arm Bandits_ Personalisation on App- Part 2 | ✅ | Widget Ranker Engine; BFF dependency; V0: 4 slots (from 9); 13 widgets; daily refresh; 70-75% Stocks NTU from Most Traded + Search; CNC Explore = 48% Groww NTU |
| 28 | Campaign Affinity- Smart Push notification | ✅ | V0 Classical ML: 10-15% CTR; V1 Thompson Sampling: 20% CTR (early reads); Template Fatigue Penalty + Eligibility Filtering; NARAD auto-triggers from AM segments; Aampe evaluated but rejected |
| 29 | Aampe | ✅ | External AI-agentic push tool; keyword tokenization + tonality per user; Sep-24 evaluation; rejected (10.2L POC cost for 8M MAU); integration complexity too high |
| 30 | Match-making_ Discussion doc | ✅ | ML model status summary; RID PA: next-day prediction; Cross-sell: 14D prediction; coverage 70-90%; high confidence = 80-90% of daily DTUs; Cross-sell FID uplift +3.2%; source splits for NTU/RID by product |
| 31 | Personalised properties testing_ JFM | ✅ | F&O personalisation ideas: expiry date, tracking behavior, carryforward; Properties backlog: golden/death crossover, price breakout, block deals, high P/E; intermediate users ~80% of platform; user calling done (7 users) |

## BATCH 5 — Channel Strategies
| # | PDF | Status | Key Extractions |
|---|-----|--------|----------------|
| 32 | Email Strategy Doc | ✅ | Email benefits: 99% delivery, 18-20% open, cheapest; Digest > 90% of volume; Digest readership declining (13M→8M); new strategy: pillars = Awareness, Activation, Reactivation, RID, Transactional |
| 33 | Email Throughput Ramp-up Project | ✅ | @Himanshu; Nov-22 project; bottlenecks: WE→Netcore 1.8M/hr, Netcore→user 2.2M/hr; solution: WE paid 10M/hr + new subdomains + 30D warmup; throughput 2.2M/hr→10M/hr; open rate +2-2.5% |
| 34 | Email Optimisations- Weekly Digest | ✅ | @Himanshu; 27M targeted, 20-22M not opening; cost 7-8L/month wasted; new seg: opened ≥1 in L90D → 11M users; same 2.1M opens; spam rate spike 68% = inboxing failure |
| 35 | Improve MAU by improving Email interaction_ GrowwFlix | ✅ | @Yash Yadav; GrowwFlix = YT video email; 3 versions (MF/Stocks/Trading); TTU +100K MAU (1.7%); Non-TTU +26K (0.71%); YT: Trading +27%, MF +15%, Main +6% subscribers; scaled to 7M, 30% open rate |
| 36 | Improving PN engagement with Banners | ✅ | @Juie Shah + @Aishwarya; 40+ PNs/day per user; image PNs = 60% higher CTR (industry claim); Groww result: NO major CTR uplift; F&O banners stopped; non-TTU marginal only |
| 37 | Push Throughput Experiment- Webengage | ✅ | @Himanshu; Apr-23; WE throughput 75K→250K/min (paid); WE→FCM latency -50%; FCM→user latency +120% (unexpected); net CTR marginal; DAU attribution +0.5-0.6%; peak time shifted earlier |

## BATCH 6 — NARAD & Tools
| # | PDF | Status | Key Extractions |
|---|-----|--------|----------------|
| 38 | Mar-tech NARAD Roadmap | ✅ | Image-only doc (all schema diagrams = screenshots, not extractable); section headers: "NARAD Schema" + "Mar-tech platforms reference"; no new text content beyond Batch 1 #6 |
| 39 | Self-serve flow for NARAD campaigns | ✅ | F&O campaigns 90% manual → automated via Kafka+Spark pipeline; master_tables schema; 20+ campaigns live (PCR alert, OI alert, ATM straddle, Long/Short buildup, Covering/Unwinding, Put/Call OI); <1 day for new derived attributes; next: CNC & MF |
| 40 | Feed Personalisation Strategy with NARAD | ✅ | @Ritvik Pandey; Feed = pull product "running at half potential"; NARAD CDP = text-only (no personalized images); Phase 1: Portfolio Analysis, Alert Properties, Benchmarking, Interested Stocks Newsletter, Brokerage Outlook; Phase 2: Fundamentals + Portfolio Health Report |

## BATCH 7 — Feed & Stories
| # | PDF | Status | Key Extractions |
|---|-----|--------|----------------|
| 41 | Feed Content Framework and Strategy | ✅ | 4 pillars: Personalized (18% impressions), Macro/Market (45%), Opportunities/Screeners (25%), Personal Finance (12%); ML Earnings Call Summarisation live; Brokerage Reports pending; CMOTS data planned; personalized images blocked by NARAD CDP limitation |
| 42 | Feed-UE content strategy | ✅ | NC=Feed confirmed; WAU 243K, DAU 104K, retention 33%; TTU 93% (F&O 28%, CNC 14%, MF 7%); content plan per product: Stocks (News, Sectoral), F&O (Traders Corner, FII/DII), Non-investors (Investment Weekly); phase 2: PN/email to drive NC DAU |
| 43 | Stories-New scoring framework | ✅ | Rf score (Random Forest) predicts D1 retention; R²=0.254; features: Skip Rate (0.24), Normalized Completion (0.23), Action Rate (0.18), Weighted Time (0.16), Screenshot Rate (0.13), Slide Count (0.06); Tier A ≥ 0.325; optimal length: 3-6 slides |

## BATCH 8 — CNC Pod
| # | PDF | Status | Key Extractions |
|---|-----|--------|----------------|
| 44 | CNC Low and Mid Active users - Feature Discovery | ✅ | @Ritvik Pandey; ISIN-level targeting 470K users; nudged to set Custom Alert/Watchlist for interest stocks; Sessions/WAU +6%, MTU +6%, PN CTR +90%, Feature Adoption (Watchlist) +2.5%; DAU insignificant; next: automate via NARAD |
| 45 | CNC Personalised experiments- 52W alerts | ✅ | @Amit Kumar @Hritwik Sahay; 52W High/Low alerts for Holdings+Watchlist+PPvisit>4; CTR 11-13%, session conversion 33-37% (beats price alerts + news); Variation A wins; 450K daily → expand to Nifty 500 + 1M reach |
| 46 | DMA Alert_ CNC Personalisation expt. | ✅ | @Juie Shah @Yash Yadav; DMA = 200 Daily Moving Average (not Direct Market Access); 200 DMA positive/negative breakout alerts; CTR 14-19%, session conversion 40-51% (best ever); tested 50/150/200 DMA — 200 wins; scale via NARAD |

## BATCH 9 — Trading Pod
| # | PDF | Status | Key Extractions |
|---|-----|--------|----------------|
| 47 | F&O - TTU - Content Performance Insights | ✅ | @Himanshu Khandelwal @Yash Yadav; F&O TTU segments A-F + Churned + Beginners; S&R alerts + OI insights = top performers for High/Mid intent; instrument affinity = Low intent; automate S&R in in-house CM; next: VIX/DMA variations; F&O educational post D7 |
| 48 | F&O Cross-sell & NTU drop | ✅ | Responsibility Charter (Dec-23) → F&O cross-sell paused Jan-24; restarted Mar-24 for F&O affinity users only; F&O NTU declining but not proportionally to targeting reduction; organic intent continues |
| 49 | F&O OI repository table | ✅ | Python/KiteConnect code for live Nifty option chain table; ATM=round(LTP/100)*100; CE/PE OI, prices, bid-ask, straddle price, buildup signals; data source: invest_iceberg.live_data.stocks_data_live_nse_fo_feed |
| 50 | Stocks F&O | ✅ | PN content for "High Volume F&O Stocks"; SQL for Most Traded F&O via platform_pinot.default.fno_stocks_order; ranks by turnover (filled_qty × avg_fill_price); filters OPTSTK (not futures); minimal new conceptual content |
| 51 | Stocks Explore Customisation for non TTU | ✅ | Hypothesis: fewer widgets→higher NTU. FAILED: v0 (1 widget: -50% NTU, 4 widgets: -20%) paused; v1 (5 widgets, new signups): flat NTU; 51% explore before onboarding; next: C-MAB widget personalization |
| 52 | MTF Go-to-market strategy_ Apr' 24 | ✅ | Mostly image-based; 3-part GTM: (1) drop-off journey for MTF discovered users (responsible broker education), (2) nudged discovery focused cohort, (3) [image]; responsible broker framing same as F&O |

## BATCH 10 — Cross-sell
| # | PDF | Status | Key Extractions |
|---|-----|--------|----------------|
| 53 | Cross-sell_discovery- Current status | ✅ | Discovery NOT the problem: ever Product/user=2.4/3; Bottom Nav ~100% ever discovered; Pay 33%→50% Jul; ~10% scope only; real gap = conversion not awareness; OKR question open: monthly discovery vs ever transaction |
| 54 | Next Best Product Cross Sell Experiment | ✅ | n+1 PN frequency; TG/CG=3.1M each; 8-21 Dec; CS conversion +4%, CS product DAU +3%, Pay +23%, F&O +2%; PN CTR -10%, User CTR +8%; PPI=1: marginal uplift + huge DND spike; PPI>1: sharp CS uplift; NTU recency: 12M+>1M>3-12M>2-3M |

## BATCH 11 — Campaigns & Events
| # | PDF | Status | Key Extractions |
|---|-----|--------|----------------|
| 55 | Asia Cup Final_ 17 Sep | ✅ | WA experiment; Inactive TTU >180D PN-unreachable; Invest (Breakout Stocks) 2.5L vs Pay (Bill Rewards) 2.5L vs CG 8.3L; Invest content wins: higher resurrection uplift + higher Pay discovery; 1-day experiment |
| 56 | Tax harvesting- Engagement | ✅ | FY-end engagement hook; tax loss harvesting = sell unrealized losses to offset STCG (15%)/LTCG (10%); target: users with unrealized stock losses; channel plan: Email+Push (awareness) → Stories (personalized P&L); competitor reference: Zerodha Kite |
| 57 | PU Testing_ Aug 23 | ✅ | PU = Portfolio Update confirmed; Inactive TTU >60D AUM≥100; WA 2L vs Email 2L vs CG 72K; WA resurrection +23% vs Email +2%; WA 1x/month + Email 2x/month going forward; add 52W high/low + gainers/losers |

## BATCH 12 — Pay Pod
| # | PDF | Status | Key Extractions |
|---|-----|--------|----------------|
| 58 | Pay Exp Overall | ✅ | Ties together 3 experiments; Invest > Pay for TTU resurrection; Non-TTU: Pay CAC Rs.65 vs Invest Rs.270; PreLoad > Regular Cashback for WAU+Onboarding+FPD; Invest thematic stock collection = cheaper resurrection than Bill rewards |
| 59 | Pay Retention | ✅ | Planning framework; BBPS Non-Bill → category approach; Bill category → target bill generation date (not due date); UPI → MCC Code by merchant type; Unused Cashback → awareness; Pay Only users → cross-sell to Invest; link mobile to Groww UPI |
| 60 | Pay_ Rakhi Exp - 30 Aug | ✅ | Inactive TTU 30-180D; PN-reachable (PN) + PN-unreachable (WA 1.5L vs CG 1.25L); 1-day festive hook (Rakhi); results in image format — not extractable; UPI payment reward |
| 61 | Pay_ UPI Rewards Exp_ 10 Sep | ✅ | Inactive TTU 30-180D; WA 3L vs CG 5.7L; PN 2L vs CG 1.5L; statistically significant resurrection uplift; Pay Discovery only 1/3 of resurrected (default landing = Invest); UPI CAC = half of Bill rewards; BBPS FPD CAC >> UPI FPD |

## BATCH 13 — Competitor Intelligence
| # | PDF | Status | Key Extractions |
|---|-----|--------|----------------|
| 62 | Competitor Screenshots_ Invest, Credit, Insurance | ✅ | Mostly image-based; competitors observed: ET Money (P2P lending PN), StockEdge (ATH alerts), Paytm (credit card bill cashback), HDFC Sky (morning update), INDMoney (image banners), Share.market (midday updates); Credit + Insurance sections = image screenshots only |
