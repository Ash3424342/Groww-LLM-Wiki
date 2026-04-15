# Growth Vertical — Concepts & Notes
### For an Engineering Major Getting into Growth

> This doc explains the *why* and *how* behind every term and process in Groww's Growth vertical. Not just definitions — the thinking behind them.

---

## 1. The Mental Model: Growth as a Pipeline

Imagine every user who downloads Groww as data entering a pipeline. At each stage of that pipeline, some users make it through to the next stage, and some drop off. Growth's entire job is to **maximize throughput** (get more users through each stage) and **minimize drop-off** (find where users are leaking out and plug those holes).

This is literally called a **funnel** — wide at the top (everyone who signed up), narrow at the bottom (only the users who became active investors). Every team in growth is responsible for one or more stages of this funnel.

The stages roughly are:

```
Downloaded app  →  Registered  →  KYC done  →  First Investment (FID)  →  Repeat Investor (RID)
```

At each arrow: some users make it through. The rest don't — at least not without a nudge. That's what the communication and engagement work is for.

---

## 2. The Funnel as a State Machine

If you think about it as a computer scientist would: every user has a **state**. They're either:

- `REGISTERED` — signed up but KYC not started
- `KYC_IN_PROGRESS` — started but didn't finish
- `KYC_DONE` — verified but no investment yet
- `FID_DONE` — made their first investment
- `ACTIVE_INVESTOR` — investing repeatedly (RID)
- `LAPSED` — was active, has gone quiet

Growth's job is to **trigger state transitions** — to get users from one state to the next. You do this by sending them the right message, at the right time, on the right channel.

Each transition between states has two numbers that matter:
- **Conversion rate**: % of users who successfully move to the next state
- **Dropoff rate**: % who get stuck or leave

Where you focus your effort = the transition with the worst conversion rate. That's your bottleneck, exactly like a slow function in a performance-critical pipeline.

---

## 3. Why KYC Creates Friction (And Why It Matters)

KYC stands for **Know Your Customer** — it's a regulatory requirement from SEBI (market regulator) and RBI. Before anyone can invest through Groww, they have to verify their identity. That means submitting PAN card, Aadhaar, bank account details, a selfie, and a signature — across multiple steps.

From a product/engineering perspective: this is a multi-step form that talks to multiple external APIs (UIDAI for Aadhaar, NSDL for PAN, etc.), each of which can fail or time out. From a user behavior perspective: every step is a potential dropout. The longer and more confusing the flow, the more people abandon halfway.

This is why the **activation funnel has 7-8 steps** — most of them are inside KYC. And why the Activation pod spends a lot of time figuring out *exactly which step* users are dropping off at, and what message or nudge would bring them back to complete it.

---

## 4. FID — Why the First Transaction is the "Aha Moment"

FID stands for **First Investment Done**. It's the most important milestone in a user's journey at Groww.

Here's why it matters so much: the moment someone invests ₹100, their behavior changes. They now have skin in the game. They'll open the app tomorrow to check how their investment is doing. They'll think about it. They'll come back. The first investment triggers a **habit loop**: invest → check → learn → invest again.

Before FID, a user has given Groww nothing — no revenue, no engagement, no relationship. After FID, the probability of them doing a second, third, tenth investment goes up dramatically. Think of it like a user completing their first successful build — once they've seen it work, they're hooked.

This is why FID is called the "aha moment" in growth. It's the point where the user realizes the value of the product firsthand.

---

## 5. RID — The Retention Problem

Getting someone to invest once is hard. Getting them to keep investing is harder — and more valuable.

RID stands for **Repeat Investment Done**. It's any transaction after the first. The reason this is tracked separately: the users who invest regularly (high RID frequency) are a small percentage of the user base but drive most of the revenue. This is the classic long-tail dynamic — power users matter enormously.

The challenge: life gets in the way. Users forget to invest, lose interest, or get distracted. The RID pod's job is to keep users engaged, remind them of their investment goals, and find reasons to bring them back to transact.

Engineering analogy: think of RID like **session count** in analytics. A user who installed your app once and never came back is a churned user. A user who opens it daily is your power user. The gap between them is retention.

---

## 6. NTU — Activation Has a Finish Line

NTU stands for **New Transacting User** — a user who has made their first transaction in a given time period. This is the official finish line of the Activation funnel.

Once a user becomes an NTU, they're no longer an "activation problem" — they graduate to the RID pod's responsibility. The Activation pod tracks users *until* they become NTU. After that, they're handed off.

**D7** is a related metric: what percentage of users who registered become NTU within 7 days? It's an early warning signal. If D7 drops, it means your activation machine is failing at the top of the funnel — something changed in the first week experience.

Think of D7 like a build's test pass rate in the first 7 minutes. If tests start failing faster, something broke upstream.

---

## 7. CrossSell FID — Expanding Wallet Share

Once a user has done FID in one product (say, Mutual Funds), they're still a new user to every other product (Stocks, Gold, FDs, US Stocks, etc.). Each of those is its own FID milestone — called **CrossSell FID**.

The strategy: take a user who already trusts Groww and has invested in one product, and get them to invest in a second one. Why? Because a user who invests across multiple products is far stickier than one who only uses a single product. More touchpoints, more engagement, higher LTV.

Engineering analogy: converting a free user to a paid plan is FID. Getting that paid user to buy add-ons or upgrade to enterprise is CrossSell FID. Each new product = a new line of revenue and a new reason to stay.

---

## 8. Cohorts — Segmentation is Just a SQL Query

A **cohort** is a group of users who share a characteristic. There are two types:

- **Time-based cohort**: "All users who registered in March 2025" — useful for tracking how a group behaves over time
- **Behavioral cohort**: "All users who completed KYC but made no investment in the last 14 days" — useful for targeting a specific problem state

The reason you segment instead of messaging everyone: **relevance is everything**. If you send a "Start your first SIP" message to someone who's already been investing for 2 years, they'll either ignore it or unsubscribe. Every unsubscribe permanently degrades your channel. Targeted = better conversion + healthier channels.

Engineering analogy: a cohort is literally a `SELECT * FROM users WHERE condition`. The Audience Manager tool at Groww is essentially a query builder for the user database.

---

## 9. TTU — Defining When a User Has "Gone Quiet"

Before the RID pod can do anything, it needs to know which users actually need re-engagement. That's where **TTU** (exact definition to confirm, but the logic is): a user crosses two thresholds —

- **Activity cut**: hasn't logged into the app in X days
- **Transaction cut**: hasn't made a transaction in Y days

If both thresholds are crossed, the user is considered **lapsed** and enters a re-engagement workflow.

Engineering analogy: a heartbeat / health check. In distributed systems, if a node hasn't sent a heartbeat in N seconds, you declare it dead and failover. TTU is the growth equivalent — if we haven't seen a user signal in N days, we treat them as "at risk" and send a rescue attempt.

---

## 10. What is a Campaign? (And Why You Don't Blast Everyone)

A **campaign** is a targeted message sent to a defined cohort, through a specific channel, at a planned time. The combination of *who*, *what*, *when*, and *how* is what makes a campaign.

Why not just message everyone every day? Because **opt-outs are permanent**. If you send irrelevant messages too often, users disable push notifications, unsubscribe from email, or block you on WhatsApp. Once they do that, you've permanently lost that channel for reaching them. The channel itself degrades.

This is why relevance is treated as infrastructure, not just a nice-to-have. Irrelevant comms at scale = gradual channel death.

Engineering analogy: a campaign is like a targeted API call to a specific user segment — not a broadcast to all subscribers. Spamming all subscribers constantly = DDoS-ing your own engagement channels.

---

## 11. Channels — Think of Them as Delivery Protocols

Different channels have wildly different characteristics. Choosing the right channel for the right message is part of the strategy.

| Channel | Latency | Engagement | Constraint |
|---------|---------|-----------|-----------|
| Push notification | Near-instant | ~3-5% CTR | Dismissed easily, OS permission needed |
| WhatsApp | Near-instant | ~60-70% open rate | Heavily regulated, template approval, can't spam |
| Email | Minutes | ~20% open rate | Best for rich, detailed content |
| RCS | Near-instant | Higher than SMS | Like SMS but with images and buttons |
| SMS | Near-instant | High delivery, low engagement | No visuals, plain text, expensive per message |
| In-app Story | Synchronous | Highest intent | User is already in the app |

Engineering analogy: these are like **delivery protocols** with different guarantees and tradeoffs:
- Push ≈ UDP: fast, fire-and-forget, no delivery guarantee
- Email ≈ async queue: reliable, latency doesn't matter, high payload
- WhatsApp ≈ TCP with rate limiting: reliable and engaging but throttled
- In-app ≈ synchronous function call: user is right there, highest signal

Picking the wrong channel for the context = sending a 10MB payload over a low-bandwidth connection. You can do it, but it's wasteful and the user experience suffers.

---

## 12. Communication Types — The Spectrum from Manual to Automated

Not all communications are equal in how they're generated and sent. Think of this as a spectrum:

```
← Manual                                              Automated →

BAU Comms → Adhoc Comms → Mid-Market → Personalized → Journeys
```

**BAU (Business As Usual):** Planned, regular campaigns. A person decides to run a "SIP reminder" push every Monday. Like a cron job someone has to consciously configure every week.

**Adhoc comms:** One-off reactions to things that just happened — a market crash, a hot IPO, a regulatory change. Like shipping an emergency hotfix.

**Mid-market action comms:** Real-time triggers during trading hours. Nifty drops 2% → send a "buying opportunity" push to relevant users. Like a webhook firing on an event.

**Personalized comms:** ML inference results delivered per user. Instead of one message to everyone, each user gets a message tailored to their behavior. Like a recommendation API call per user.

**Journeys:** Automated sequences that branch based on user behavior over time. Set it up once, and it runs autonomously. This is the most sophisticated form.

The further right on this spectrum, the more automation is involved, the more relevant the message, and the less manual effort per message sent.

---

## 13. What is a Journey? (Event-Driven Automation)

A **Journey** is an automated communication sequence triggered by a user event (or the absence of one). It's the most powerful tool in the engagement toolkit.

Here's a concrete example — the "KYC done, no FID" journey:

```
Trigger: User completes KYC but doesn't invest within 24 hours

Day 0  →  Push: "Your account is ready. Make your first investment."
           ↓ (Did user invest?)
           YES → Exit journey, hand off to RID pod
           NO ↓
Day 2  →  Email: "Not sure where to start? Here are 3 funds for beginners."
           ↓ (Did user invest?)
           YES → Exit
           NO ↓
Day 5  →  WhatsApp: "Investing even ₹100 today can make a difference."
           ↓ (Did user invest?)
           YES → Exit
           NO ↓
Day 7  →  Flag user for deeper analysis / different strategy
```

This runs automatically for every user who hits the trigger condition. No manual work per user.

Engineering analogy: a Journey is an **event-driven state machine** — like AWS Step Functions or a DAG execution engine. Each node is a communication action. Each edge is a condition (did the user act?). The whole thing runs asynchronously for millions of users simultaneously.

The absence of an event is as meaningful as the presence of one. "User did NOT invest in 2 days" is a trigger just as much as "user invested."

---

## 14. Personalization — The ML Recommendation Pipeline

The core problem: you have 10 million users and one message. Sending that one message to everyone is the lowest-common-denominator approach — most people find it irrelevant, CTR is low, opt-outs rise.

The solution: compute a **different message for every user**, every day.

Here's how Groww's personalization engine works:

**Input:** Every user's app activity — what they browse, what's on their watchlist, what they hold, when they open the app, what they click on.

**Three ML models run daily:**

1. **Product affinity model:** Given this user's activity, what are the 2 products they're most likely to transact in tomorrow? Output: `["Mutual Funds", "US Stocks"]`

2. **Instrument affinity model:** Within those products, which specific instrument are they most likely to act on? Output: `"Mirae Asset Emerging Bluechip Fund"`

3. **Time activity model:** When is this user most active on the app? Output: `"8:45 AM"`

**Combined output:** Send this user a push notification at 8:45 AM saying "Mirae Asset Emerging Bluechip Fund is up 2% this week. Start a SIP today."

Instead of a generic "Invest in Mutual Funds", every user gets something that feels personally relevant — because it is.

Engineering analogy: this is exactly a **recommendation engine**, like Netflix or YouTube's "recommended for you" — except instead of "what to watch", it's "what to invest in, and when to tell you."

---

## 15. The Campaign Workflow — End to End

Here's what actually happens, step by step, when a campaign goes from idea to sent:

```
1. DEFINE COHORT
   → "Who are we targeting?"
   → Example: users who completed KYC more than 7 days ago, made no investment,
     and were active on the app in the last 3 days
   → This is literally a query: WHERE kyc_done=true AND fid=false
     AND last_active <= 3 days AND kyc_date >= 7 days ago

2. CREATE CONTENT (Content banao)
   → Write the message: push body, email subject, WhatsApp text
   → Add personalization variables: {first_name}, {product_browsed}, {fund_name}
   → This happens BEFORE audience finalization — you write the message,
     then pull the exact audience

3. AUDIENCE MANAGER
   → Run the segment query against the user database
   → Get back a list of matching user IDs
   → Check reach: is the segment big enough? Any overlap with other campaigns today?

4. LOAD & CONFIGURE IN NARAD / WEBENGAGE
   → Upload user list
   → Set: send time, channel, frequency cap (max 1 push per user per day, etc.)
   → QA: test send to internal users, verify copy and links

5. SEND
   → Platform delivers messages via the chosen channel
   → Push goes through FCM/APNs, WhatsApp through Meta's API, etc.

6. MEASURE
   → Track: delivery rate, open rate, CTR, and crucially — did the user FID/RID after?
   → Report in Comms 360 and WBR
   → Feed learnings back: what worked? What didn't? Refine next campaign.
```

---

## 16. Why Metrics Are a Feedback Loop, Not Just Numbers

Every metric is a signal about a specific part of the pipeline. When a metric drops, it tells you *where* something broke. When it rises, it tells you something worked. This is identical to how observability works in engineering.

| Metric | What it tells you |
|--------|-----------------|
| **D7** | Is your activation working in the first week? Drop → something broke at the top of the funnel |
| **Convert rate (per step)** | Exactly which funnel step is the bottleneck right now |
| **FID rate** | Is your overall activation machine working? |
| **RID rate** | Is your retention machine working? Are users coming back? |
| **Push CTR** | Is your message relevant to the cohort you chose? Low CTR → wrong audience or wrong message |
| **Opt-out rate** | Are you over-messaging or under-targeting? High opt-outs → channel degradation |
| **CrossSell FID rate** | Are you successfully expanding users into new products? |

Engineering analogy: these metrics are your **SLIs (Service Level Indicators)**. Latency, error rate, and throughput for a web service. Conversion rate, dropoff rate, and FID rate for a growth funnel. Both tell you if your system is healthy or broken — and where.

The key mindset shift: a metric without an owner is useless. Every metric in the Growth vertical is owned by a person or a pod. When it moves, there's someone responsible for understanding why.

---

## 17. The Tools Stack — What Each One Actually Does

**NARAD** — Groww's internally built CRM. Think of it as a campaign management system the engineering team built themselves: create a campaign, define the audience, write the message, schedule it, track delivery and clicks. Custom-built to handle Groww-specific logic and scale.

**WebEngage** — A commercial off-the-shelf CRM (like Salesforce for engagement). Used alongside NARAD for certain channels or use cases. Similar capabilities but with more out-of-box integrations.

**Audience Manager** — The segmentation layer. You give it criteria ("KYC done, no FID, active last 3 days"), it runs the query against the user database and hands back a list. Like a query builder UI on top of the user data warehouse.

**Superset** — Apache Superset, an open-source BI tool. Think Grafana — but instead of CPU usage and error rates, it shows business metrics: daily FID numbers, funnel conversion rates, campaign performance over time. Used by everyone in the vertical for data analysis.

**Comms 360** — A dashboard specifically for communication performance. Cross-channel view: how did today's push campaign do? How does WhatsApp compare to email for a given cohort? Optimized for the "did this message work?" question.

**User Engagement Dashboard** — Top-level view of the vertical's KPIs: MAI, FID count, D7 rates, active user counts. The "homepage" metric view for the Growth team.

---

## 18. Why WhatsApp is Both Powerful and Dangerous

WhatsApp is the highest-engagement channel in the toolkit — but it's also the most dangerous to misuse. Here's why the team thinks carefully before scaling it:

**Why it's powerful:**
- Unlike push notifications (which require the app to be installed and opt-in), WhatsApp reaches users through a personal channel they check multiple times a day
- ~50% of non-investor app-keep users are NOT reachable via push. WhatsApp fills this gap.
- Industry benchmarks: 60-70%+ open rates vs 3-5% for push CTR
- Cost advantage for reactivation: WhatsApp FID CAC is 1/5th to 1/10th of paid remarketing (Facebook/Google ads)

**Why it's dangerous to overuse:**
- Meta is tightening rules — price for Business Initiated Conversations went from 51p to 73p (anti-spam measure). User Initiated Conversations stay at 33p (Meta is pushing companies toward conversational, not broadcast)
- Industry norm: 1 WA per week for most brands, 1 per 14D for fintech. Exceeding this → user blocks → Meta may permanently block the business number
- Once a user blocks on WhatsApp, you lose the channel for them permanently — much harder to recover than a push opt-out

**The strategic rule:** Use WhatsApp for high-intent moments (user is close to completing an action) or for users unreachable by other channels. Don't broadcast; be contextual.

**Proven high-ROI WhatsApp use cases at Groww:**
1. Esign drop-off nudge (user is at last step of KYC): 30% conversion uplift
2. Inactive user reactivation (no push token): 1/10th the CAC of paid ads
3. Push-unreachable active users: incremental reach with better engagement

Engineering analogy: WhatsApp is a **privileged resource** — like a production database you can query directly instead of going through the API layer. Fast and powerful, but hitting it too hard crashes the system. Rate limit it carefully.

---

## 19. The Cold Start Problem

When a brand new user signs up to Groww, they have zero behavioral history. The ML models (product affinity, instrument affinity) have nothing to work with. This is the **cold start problem** — how do you personalize for someone who just arrived?

Several approaches are being explored:
1. **Ad-group-level messaging:** If you know which ad the user clicked to download the app, you can infer what product interested them ("started SIP" ad → probably interested in MF). Mirror the acquisition messaging in the onboarding flow.
2. **Feed-based discovery:** Curate a generic but high-quality discovery feed for new users until behavioral signals emerge
3. **Curiosity-based comms:** Instead of product-specific messages (which require knowing user preferences), send curiosity hooks ("Check how the market is doing today") to drive app opens → behavioral data → personalization possible

The cold start problem is fundamentally a **chicken-and-egg problem**: you need behavior to personalize, but you need personalization to get behavior. The solution is to get any behavior first (app opens, PP visits, watchlist activity), then let the models kick in.

Engineering analogy: cold start in ML recommendations is exactly like cache warming in distributed systems. You can't serve personalized content from an empty cache — so you either serve defaults (generic feed) or use side-channel signals (ad click = implicit preference) until the cache warms up.

---

## 21. GCG — How You Know Your Campaign Actually Worked

This is the core measurement problem in growth: you run a campaign and your metric goes up. But did it go up *because* of your campaign, or would it have gone up anyway?

**GCG = Global Control Group.** Here's how it works:

- 5% of your total user base is permanently held out from all promotional communications. They still receive transactional messages (payment confirmations, order receipts), but no marketing nudges.
- The other 95% is your **treatment group** — they receive campaigns.
- Both groups are tracked with a **30-day holdout window** — meaning you compare them over a 30-day period.

At any given time:
- Treatment: 95% of users → receive your campaigns
- Control: 5% of users → baseline behavior (no influence from campaigns)

The **incremental uplift** = `(Treatment group metric) / (Control group metric) - 1`

If the treatment group has 20% more NTUs than the GCG, your campaigns are driving 20% incremental NTUs.

**Why is this hard without GCG?** Because user behavior is seasonal, market-driven, and confounded. When markets are bullish, FIDs go up for everyone — not because of your campaign. GCG separates natural behavior from campaign-driven behavior.

Engineering analogy: GCG is a **permanent A/B test holdout group**, but instead of testing a feature, you're testing whether *doing anything at all* moves the needle. It's the null hypothesis you're always comparing against.

**Benchmark from Groww's data:**
- Non-TTU campaigns: +55-60% DAU uplift, +75% NTU uplift at Day 15 vs GCG
- Personalised TTU comms: Peak DAU +11% vs GCG

---

## 20. Reachability — Why You Can't Just "Send a Push"

One of the most surprising things to learn: you can't reach most of your users through a single channel. Here's the reachability breakdown for non-investor (pre-FID) users:

- **~50% of non-investor app-keep users** don't have push notifications enabled → push unreachable
- **L150D+ inactive users** (last active 150+ days ago): push reachability drops to **~1.5%** — almost nobody
- **Email**: better reachability but lower engagement
- **WhatsApp**: requires explicit opt-in to receive business messages, but broader reach than push among inactive users

This is why the channel strategy is multi-layer. If a user can't be reached via push:
- Try email first
- Then SMS as fallback
- WhatsApp for higher-intent moments (requires opt-in but better ROI)
- Paid remarketing (Facebook/Google) for completely unreachable users — but very expensive (FID CAC 6,000+ for L150D+ base)

The cost of reaching unreachable users escalates dramatically:
```
Push → Free (already opted in)
Email → Minimal cost
SMS → Small variable cost
WhatsApp → 73p/message (BIC)
Remarketing → Rs.6,000+ per FID conversion (for deeply inactive users)
```

Engineering analogy: reachability is like **endpoint health in a service mesh**. You have multiple ways to reach a service (HTTP, gRPC, queue), and some endpoints are down (user opted out of push). Your retry logic needs to fall back through the stack gracefully — but calling the most expensive endpoint first is wasteful.

---

## 22. MAB — The ML Engine Behind Campaign Selection

Imagine you're trying to decide which of 10 campaigns to show each user. The naive approach: send all users Campaign A for a week, measure, then try Campaign B next week. This is a standard A/B test. It has a massive flaw: you're wasting weeks getting to the right answer, and you're showing suboptimal campaigns to users while you figure it out.

**Multi-Armed Bandit (MAB)** solves this with a smarter algorithm:

- You start by showing each campaign to a small random sample of users.
- You measure which campaigns get the best CTR per user segment.
- You **gradually shift traffic** to the winning campaigns — more users see the winners, fewer see the losers.
- You keep a small exploration rate: even campaigns that look weaker keep getting some traffic, because they might work for a specific sub-segment.

At Groww this is called **Campaign Affinity / MAB**:

- ~50% of TTU (active investors) have at least 1 campaign affinity score
- The model computes for each user: "Which of the available campaigns are they most likely to engage with?"
- The MAB algorithm then balances **exploit** (show the winning campaign) vs **explore** (test alternatives)

**Result:** Instead of sending the same push to all users, each user gets the campaign most likely to work for them. CTR goes up. Opt-outs go down.

Engineering analogy: MAB is like **adaptive load balancing with feedback**. Instead of round-robin (A/B test), you weight traffic based on real-time performance data — like an A/B test that continuously self-optimizes. The 5% holdout for exploration = the randomness needed to avoid getting stuck in a local optimum.

---

## 23. The Business Layer — CLTV × Capacity

Here's a core strategic problem: you have 10 million users and can only send each one a limited number of messages per month (due to channel fatigue, regulatory limits, etc.). Who do you contact? With what message? About what product?

**The Business Layer** is Groww's framework for answering this:

> **For each user, send 1 RID message (for their existing product) + 1 CrossSell message (for a new product). That's it for the month.**

This is the **CLTV × Capacity model**:

```
CLTV = Customer Lifetime Value — how valuable is this user long-term?
Capacity = How many messages can we send without degrading the channel?
```

The two-layer cohort model:
1. **Layer 1 (Business Layer):** Rank users by CLTV. High-CLTV users get priority for communication slots.
2. **Layer 2 (Campaign Layer):** Within the allowed capacity, pick the best campaign for each user (using ML affinity models).

**Why the constraint matters:**
- If you message users too often, they opt out → channel degrades permanently
- Low-CLTV users getting too many messages = wasted capacity
- High-LTV users who lapse = the most expensive users to lose → prioritize retention over acquisition for them

**What this means in practice:**
- Each user gets at most: 1 RID nudge + 1 CrossSell nudge per month (from the business layer)
- On top of that: adhoc campaigns, BAU comms — but the business layer is the core structure
- The ML models (Product Affinity, Instrument Affinity, Campaign Affinity) decide *what* each nudge says

Engineering analogy: CLTV × Capacity is a **rate limiter + priority queue**. You have a fixed number of "slots" per user per month. You fill those slots in priority order (CLTV-ranked). The ML models decide the payload for each slot.

---

## 24. The Three-Part Engagement Strategy

Groww's engagement approach is organized in three layers — think of it as a progressive rollout plan:

**Part 1 — Off-app communications (live today):**
All the channels we've discussed: push, WhatsApp, email, RCS, SMS. Messages that reach users when they're not in the app.

**Part 2 — On-app personalization (in progress):**
When the user *is* in the app, what do they see? The feed, stories, in-app banners, navigation recommendations. This is personalization at the product layer — not just "send them a push" but "when they open the app, show them exactly the right content."

**Part 3 — Combined (future):**
The full picture: off-app messaging *coordinates with* on-app experience. If a push brought a user in, the app already knows why they're there and shows them a relevant landing state.

**Why this progression?** Off-app is easier — you control the message. On-app requires product integration — you're changing what millions of users see in the live product. More complex, but much higher impact because the user's intent is already there (they opened the app).

Engineering analogy: Part 1 is **outbound notifications** (server-pushed). Part 2 is **personalized API responses** (request-response, but the response depends on the user profile). Part 3 is **context propagation** — the notification and the app experience share state.

---

## 31. Discovery vs Conversion — The Two Different Cross-sell Problems

When you're trying to get an MF investor to also invest in Stocks, there are two completely different problems you might be solving:

**Problem 1: They don't know the product exists.** They've never been to the Stocks page. They don't know Groww does equity investing. You need to **discover** them to the product.

**Problem 2: They've visited Stocks, maybe even added stocks to a watchlist, but haven't transacted.** They know about it. They're just not converting. You need to improve **conversion**.

Groww's cross-sell analysis found that **the discovery problem is largely solved** for most products:
- Bottom navigation products (MF, Stocks): ~100% ever discovered by TTU users
- Ever discovered Products/user = 2.4/3 (excludes Loans/Pay)
- Pay improved from 33% to 50% discovery in a single month once prioritized

What this means: **you can't materially improve cross-sell by just making users aware of more products.** They already know. The gap is converting the already-aware users.

**The conversion strategy:** The Next Best Product ML model identifies which product each user is most likely to transact in *next*, based on their historical behavior. The experiment (Dec, 3.1M users each side) added one extra cross-sell PN/day (n+1 frequency):

- Overall cross-sell conversion: +4%
- Pay specifically: **+23%** (Pay model was most impactful despite lower accuracy ranking)
- The extra PN didn't kill DAU — users redirected their sessions to cross-sell products instead of just adding net-new sessions

**The PPI=1 warning:** Users with only 1 product (single-product investors) are the most tempting target for cross-sell — they have the most room to grow. But the data shows: PPI=1 users show huge DND (push opt-out) spikes when targeted aggressively with cross-sell. PPI>1 users cross-sell smoothly with no DND increase. **The conclusion:** don't burn your channel health trying to force-cross-sell single-product investors. Let them warm up first.

**NTU recency pattern:** Cross-sell uplift is highest for 12M+ NTUs (established, comfortable with Groww) and 1M NTUs (honeymoon period — high intent). It's lowest for 2-3M NTUs (the settling period — past the honeymoon, not yet habitual). Design cross-sell targeting with this in mind.

Engineering analogy: Discovery vs conversion is the same as **cache miss vs cache hit latency**. Discovery = cache miss (user never loaded the product). Conversion = cache hit that doesn't translate to a transaction (data is in cache but not being used). The optimization strategy is completely different for each case.

---

## 30. The Responsibility Charter — Why F&O Marketing is Constrained

F&O (Futures & Options) are leveraged derivatives. You can lose more than you invest. SEBI is acutely aware of this and has been pushing brokers to take a more cautious approach to marketing high-risk products. Groww's internal response to this is the **Responsibility Charter**.

**What it means in practice (confirmed from Batch 9 docs):**

- **Before Dec-23:** F&O cross-sell was broad — any TTU (active investor) could be targeted with F&O promotional comms, regardless of whether they'd shown F&O interest.
- **Jan-24:** F&O cross-sell paused entirely. Internal discussions happening.
- **Mar-24 onwards:** Restarted, but with a hard constraint: **only target users who have either (a) already completed F&O onboarding, or (b) been identified as F&O affinity users by the ML model**. No more cold-targeting CNC/MF investors for F&O.

**Why this matters for growth metrics:**
- F&O NTU share declined post the targeting change — fewer people exposed = fewer conversions.
- BUT: the decline was NOT proportional to the reduction in targeting. Organic F&O discovery continues even without active promotion — some users find F&O on their own through app exploration or market conditions (volatile markets naturally drive F&O interest).
- This tells you something important: a large fraction of F&O NTU was already driven by organic intent, not campaign influence.

**MTF (Margin Trade Funding) has the same framing.** MTF lets you buy stocks with borrowed money. GTM strategy explicitly calls out "educate the user as a responsible broker" — you explain the risks before pushing the product.

**Engineering analogy:** The Responsibility Charter is like **rate limiting + access control on a sensitive API endpoint**. Before: anyone could call the endpoint. After: only users with appropriate permissions (F&O onboarded OR F&O affinity signal) can be targeted. The change reduces throughput but improves precision — and aligns with the platform's long-term regulatory standing.

**Why this matters for your work:** Any time you're designing a campaign or experiment that involves F&O, MTF, or other leveraged products — check against the Responsibility Charter. The constraint isn't just legal CYA; it's a real business decision to prioritize LTV over short-term conversion.

---

## 29. The Personalization Ladder — From Generic to Intent-Based Technical Triggers

One of the clearest illustrations of Groww's personalization evolution is in CNC (stocks trading). The team ran a series of experiments that form a visible progression ladder: each rung is more personalized than the last, and each rung has higher CTR and session conversion.

**The ladder (ranked by performance):**

```
Generic "Stocks in Spotlight" (BAU)
    → Same message to all CNC users, afternoon send
    → CTR: ~3%
    ↓
Stock News (automated, holdings-based)
    → "HDFC Bank news: XYZ" for users who hold HDFC
    → CTR: 4-7%, Session conversion: 10-35%
    ↓
Price Alert (±5% movement)
    → "Your stock moved 5%" for holdings/watchlist
    → CTR: 3.5-8%, Session conversion: 17-40%
    ↓
52W High / Low Alert
    → "Stock X just hit 52-week high" for high-intent users
    → Intent = Holdings OR PP visit > 4 in L7D
    → CTR: 11-13%, Session conversion: 33-37%
    ↓
200 DMA Breakout Alert (best performer)
    → "Stock X crossed 200-day moving average" for high-intent users
    → CTR: 14-19%, Session conversion: 40-51%
```

**Why does this ladder work?** Each rung is more specific and more relevant to the user's actual investing state:
- Generic: relevant to nobody in particular
- Stock news: relevant because it's about a stock you own
- Price alert: urgent because it affects your portfolio value
- 52W High/Low: rare, extreme event — very high signal value
- DMA breakout: sophisticated technical signal — tells a serious investor something actionable about long-term trend

**The session attribution window is 12 minutes.** If a user clicks a PN and opens the app within 12 minutes, that session is attributed to the campaign. This is the standard measurement window for CNC PN session conversion.

**What is a DMA (Daily Moving Average)?** The N-day moving average is the average closing price of a stock over the last N trading days. The **200 DMA** is the most watched long-term trend indicator by traders. When a stock crosses above its 200 DMA, it's called a positive breakout — traditionally a bullish signal. When it crosses below, that's a negative/bearish breakout. Groww tested 50, 150, and 200 DMA alerts. 200 DMA won.

**Feature Discovery rung (separate lever):** Alongside content alerts, there's a different personalization approach: getting users to adopt app features. For CNC Low/Mid Active users, the team sent personalized nudges to set a Custom Alert or add a stock to their Watchlist — using the user's existing interest in that stock (>avg clicks on a specific ISIN). Result: Sessions/WAU +6%, MTU +6%. This is a "habit formation" play rather than a trading signal play.

Engineering analogy: The personalization ladder is like **HTTP response caching tiers**. Generic campaign = cache miss (same response for all). Holdings-based = user-level cache (different response per user profile). 52W High = event-driven invalidation (only responds when a real event occurs for that user). The more specific and event-driven the message, the higher the signal-to-noise ratio for the receiver.

---

## 27. The Stories Scoring Model — Using ML to Rate Content Quality

The growth team creates dozens of in-app Stories (Instagram-style swipeable cards). How do you know which ones are good? You can look at total views, but a viral story could have lots of views and high skip rates — meaning people opened it and immediately left. You need a quality metric.

**Rf score** = Random Forest content score predicting **Day-1 retention** (does the user come back the next day after seeing this story?). That's the real proxy for content quality: not just "did they watch it" but "did it make them want to come back."

**The formula:**
```
RF_Score ≈ 0.24 × Skip_Rate
          + 0.23 × Normalized_Completion
          + 0.18 × Unified_Action_Rate
          + 0.16 × Weighted_Time
          + 0.13 × Screenshot_Rate
          + 0.06 × Slide_Count
```

Each coefficient is the feature importance weight from the Random Forest. **Skip Rate is the most powerful predictor** — users who skip the story are telling you the content isn't relevant. If skip rate is high, your D1 retention will suffer.

**Why Normalized Completion instead of raw completion?** A 5-slide story and a 15-slide story shouldn't be held to the same completion standard. A 70% completion rate on a 15-slide story might actually be great. Normalized completion adjusts for slide count: the model regressed slide_count → completion_rate (slope = -0.034), giving `expected_completion = 0.9297 - 0.0344 × slide_count`. If actual > expected, the story is performing above expectation.

**Why Weighted Time instead of mean time?** Mean time is noisy — a few users who left the app with the story open inflate it. `(0.1×P50) + (0.2×P75) + (0.3×P90) + (0.4×P95)` weights toward the *engaged* users (P90, P95), giving a better signal of voluntary engagement.

**Scoring tiers and what they mean:**
- Tier A (≥ 0.325): High-performing — replicate these
- Tier B (0.262–0.324): Acceptable — watch for patterns
- Tier C (< 0.262): Low-performing — redesign or drop

**Key operational insight:** Shorter stories win. 3-6 slides = optimal. Beyond 7-10 slides, completion drops noticeably. If users are fatiguing by slide 8, you're adding slides that hurt your score.

**Model caveats:** R² = 0.254 — the model explains 25.4% of D1 retention variance. That's not bad for content prediction (content quality is hard to model), but it means 75% of D1 retention variance comes from things the model doesn't capture — like the user's mood, what they had for breakfast, or market conditions. **This model is a content quality guide, not a retention prediction system.**

Engineering analogy: Rf score is like a **code quality linter** — it catches obvious problems (high skip rate = messy code that fails the first check) and rewards good patterns (high completion = tests passing). But it can't guarantee production reliability — it's a signal, not a guarantee.

---

## 28. The Notification Center / Feed — Content Strategy by User Type

"Feed" and "Notification Center (NC)" mean the same thing at Groww. It's the in-app content hub — a browseable, swipeable stream of market insights, alerts, educational content, and portfolio updates. Think Bloomberg Terminal lite, inside a mobile app.

**Current usage pattern (eye-opening stats):**
- WAU: 243K, DAU: 104K — relatively small vs total MAU (~10 crore+ registered users)
- Weekly visit retention: 33% — 1 in 3 weekly visitors returns the following week
- 93% of visitors are TTU (existing investors), only 7% are non-investors
- F&O users visit the most (28% of F&O MAU visit NC), CNC at 14%, MF at 7%

The team's own assessment: Feed is "running at half potential." The personalized content layer is barely live — only 18% of impressions are personalized (mostly News). 45% are generic market updates that any user would see.

**Content strategy by user type (how the team breaks it down):**

| User type | Daily content | Weekly content |
|-----------|--------------|----------------|
| **Stocks TTU** | Stocks in News (morning), Portfolio news feed, Sectoral movement | Popular Stock YT video, Market Wrap, Feature education |
| **F&O TTU** | Traders Corner (support/resistance), FII/DII numbers | Popular FnO YT video, Feature education |
| **MF TTU** | Ideation needed ("very static") | Popular MF YT video, Fund analysis |
| **Non-investors** | Stocks in News, Traders Corner, Sectoral movement | Investment Weekly roundup (gainers/losers, most-bought) |

**Why does F&O visit NC so much more?** F&O traders need real-time information. Support/resistance levels, OI changes, FII/DII flows — these are actual trading decision inputs. An MF investor can check once a month. An intraday trader needs data every 30 minutes.

**The FII/DII numbers:** Every day, after market close, institutional investor net buy/sell data is published. This is a key signal the trading community watches — it tells you whether "smart money" (large institutions) was buying or selling on a given day. Groww delivers this as a daily NC property for F&O users.

**Traders Corner:** A daily property showing technical support and resistance levels for NIFTY50, NIFTYBANK, and FINNIFTY. For options and futures traders, these levels define the range they're trading around. Publishing this every morning is a direct value-add for their trading day.

Engineering analogy: Feed strategy is like designing **API endpoints for different client types**. The F&O user is a heavy consumer (high poll rate, real-time data needs). The MF user is a batch client (monthly data refresh is fine). The non-investor is a new user with no client-specific config — they get defaults. You design different response payloads for each client, but they all hit the same service.

---

## 25. NARAD as a Data Pipeline — The Self-Serve Campaign Model

Most people think of a CRM as a "campaign sending tool" — you write a message, pick an audience, press send. That's true for NARAD's front-end. But what makes NARAD architecturally interesting is what happens underneath.

**The problem it solves:** F&O campaigns require real-time market data. "Send an alert when Nifty OI drops 10% in 30 minutes" requires monitoring every contract every minute. Before the self-serve pipeline was built, 90% of F&O campaigns were done manually — someone checked the data, wrote the message, and sent it. That doesn't scale.

**How NARAD's self-serve pipeline works:**

```
Invest Pod Data Sources
(fo_feed, indices_v3, derived_contract_master, ...)
        ↓
    [Kafka]
    Real-time event streams ingested
        ↓
    [Spark Stateful Structured Streaming]
    Joins multiple streams (refreshing at different intervals)
    Maintains state for each contract
    Handles both event-triggered and time-based (every minute) refreshes
        ↓
    [master_tables schema]
    Base attributes + derived attributes + historical (30min, 60min, 120min, 1D)
    Feature tables: Contract master, Index master, ATM master
        ↓
    [NARAD Campaign Rules Engine]
    Business team defines trigger logic (without DP team):
    e.g., WHEN curr_oi < oi_30min_before * 0.90 AND curr_price > price_30min_before * 1.05
        ↓
    [Push / WA / PN to user]
```

The key insight: **derived attributes are pre-computed and standardized**. When the business team wants a new campaign rule, they just write a SQL-like condition against existing attributes. The DP (Data Platform) team only gets involved if a fundamentally new data source is needed (e.g., Greeks data).

**Result:** 20+ F&O campaigns now run automatically. Campaign manager bandwidth freed up. New derived attribute logic takes <1 day to add.

Engineering analogy: NARAD's self-serve pipeline is like a **feature store + rules engine**. The Kafka/Spark layer is the feature computation layer (like Feast or Tecton). The master_tables are the feature store. NARAD's campaign rules are the downstream consumers — but instead of ML inference, it's threshold-based triggers. Any team member who knows the business logic can write a new rule without touching the data infrastructure.

---

## 26. Feed as a Pull Product — Why It's Different from Push

Every channel we've discussed so far is **push**: you send something to the user. The user receives it passively (push notification pops up; email arrives; WhatsApp message delivered). The user didn't ask for it.

**Feed is a pull product.** The user actively opens the app and looks at the feed. They're seeking information — not receiving an interruption. This changes everything:

| Dimension | Push Channel | Feed (Pull) |
|-----------|-------------|-------------|
| User intent | Low — they weren't looking | High — they came looking |
| Tolerance for irrelevance | Low — irrelevant → opt-out | High — they'll scroll past |
| Personalization value | Moderate — wrong content = ignored | Extremely high — right content = time spent |
| Frequency limits | Hard (regulatory + fatigue) | Soft (user controls how often they visit) |
| Revenue mechanism | Drives transaction events | Drives session depth + retention |

**The business case for Feed personalization:** If a user opens the feed and sees something irrelevant, they leave. If they see something tailored — their portfolio performance vs peers, a 52W high alert on a stock they own, a brokerage report on their watchlist — they stay. Time spent → habit formation → higher retention → higher LTV.

Groww's assessment: Feed is "running at half potential" because it's not yet fully personalized.

**NARAD's role:** Feed content properties (alerts, newsletters, analysis) are being moved into NARAD for automated delivery. NARAD's CDP currently supports **text-only personalization** — so personalized images are not yet possible at scale. Initial 5 properties are text-based (portfolio analysis, alerts, benchmarking, newsletter, brokerage outlook).

**Phase 1 properties (launching first):**
1. **Detailed Portfolio Analysis** — personalized insights on the user's holdings
2. **Alert Based Properties** — 52W high/low and movement alerts for held/watched stocks
3. **Portfolio vs Index Benchmarking** — how is the user's portfolio doing vs NIFTY/SENSEX?
4. **Interested Stocks Newsletter** — movement since last visit + sector/peer comparison for watchlisted stocks
5. **Brokerage Outlook** — aggregated broker research reports for stocks in portfolio/watchlist

**Phase 2 properties (after Fundamental Attribute Creation):**
1. **Interested Stocks Fundamentals** — P/E vs peers/industry, QoQ profit trends
2. **Portfolio Health Report** — flags danger markers (extreme Debt/Equity ratio, concentration risk, etc.)

Engineering analogy: Feed personalization is like **server-side rendering with user context**. The feed is a template — but the data that fills it is personalized per user. Push is fire-and-forget (UDP). Feed is request-response (HTTP GET) where the response is tailored to the user state.

---

## How It All Fits Together

```
User downloads Groww
        ↓
[ACTIVATION POD]
Funnel: Sign-up → KYC → FID
Comms: Push, Email, in-app nudges at each step
Goal: Get to FID as fast as possible
Metric: FID rate, D7, Onboarding %
        ↓
User does FID → becomes NTU
        ↓
[RID POD]
Goal: Repeat transactions across products
Tools: Cohorts based on TTU, hyper-personalized comms
Metric: RID rate, CrossSell FID, active SIPs
        ↑
[PERSONALIZATION]
Runs across both pods: product affinity + instrument affinity + time model
Makes every message more relevant for every user

[TRADING POD] — parallel track
Same FID → RID logic, but for trading products
Extra dimension: 9:15 AM market open as a daily trigger event

[ALL PODS]
Channels: Push, WhatsApp, Email, RCS, SMS, Stories
Tools: NARAD, WebEngage, Audience Manager, Superset
Reporting: WBR, MBR, Comms 360, UE Dashboard
```

The whole vertical is one large feedback loop: send message → user acts (or doesn't) → measure the result → improve the next message → repeat.

---

*This doc will grow as you learn more. Drop in new context and the Master Reference will get updated.*
