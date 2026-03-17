# KPI Dashboard Mockup — Similan Digital Agency
**Brands:** The Vegan Table | Really Good Deli | Lucky 13 Sandwich  
**Platform:** Google Looker Studio (recommended)  
**Update Frequency:** Daily (automated via API connectors)  
**Owner:** Panda / Analytics Bot  
**Audience:** Dan (weekly digest) + Brand managers (real-time access)

---

## DASHBOARD ARCHITECTURE

### Overview: 3-Page Structure

```
Page 1: EXECUTIVE SUMMARY (Dan's view — 1 page, all 3 brands)
Page 2: BRAND DEEP-DIVES (per-brand detailed metrics)
Page 3: AD PERFORMANCE (Meta + LinkedIn campaign breakdown)
```

---

## PAGE 1: EXECUTIVE SUMMARY

### Layout (Top to Bottom)

#### Header Bar
- Date range selector (default: Last 7 days | MTD | Last 30 days | Custom)
- Last updated timestamp
- Brand filter toggle: [All] [Vegan Table] [RGD] [Lucky 13]

---

#### Section 1: Brand Health Scorecards (3 cards, side by side)

**Card: The Vegan Table**
```
┌─────────────────────────────┐
│ 🌿 THE VEGAN TABLE          │
│─────────────────────────────│
│ Followers: 850 (+50 ▲)     │
│ Engagement Rate: 3.8% ▲    │
│ Email Open Rate: 28% ▲     │
│ Website Traffic: +32% ▲    │
│ Ad ROAS: 1.8:1 ▲           │
│─────────────────────────────│
│ HEALTH: 🟢 ON TRACK         │
└─────────────────────────────┘
```

**Card: Really Good Deli**
```
┌─────────────────────────────┐
│ 🥩 REALLY GOOD DELI         │
│─────────────────────────────│
│ LinkedIn Followers: 130 ▲  │
│ B2B Lead Inquiries: 4 ▲    │
│ Email Open Rate (B2B): 32% ▲│
│ Online Orders: 7 ▲         │
│ Ad ROAS: 1.6:1 ▲           │
│─────────────────────────────│
│ HEALTH: 🟢 ON TRACK         │
└─────────────────────────────┘
```

**Card: Lucky 13**
```
┌─────────────────────────────┐
│ 🥪 LUCKY 13 SANDWICH        │
│─────────────────────────────│
│ Followers: 680 (+80 ▲)     │
│ Engagement Rate: 2.5% ▲    │
│ Email Open Rate: 22% ▲     │
│ Footfall Index: +22% ▲     │
│ Ad ROAS: 2.1:1 ▲           │
│─────────────────────────────│
│ HEALTH: 🟢 ON TRACK         │
└─────────────────────────────┘
```

---

#### Section 2: Combined Traffic Trend (Line Chart)
- X-axis: Date (last 30 days)
- Y-axis: Combined website sessions (all 3 brands)
- 3 colored lines (one per brand)
- Annotations: Launch dates, email sends, ad launches

---

#### Section 3: Top Content Performers (Table)
| Brand | Platform | Post Type | Reach | Engagements | Engagement Rate |
|-------|----------|-----------|-------|-------------|-----------------|
| Vegan Table | Instagram | Reel | 2,100 | 84 | 4.0% |
| Lucky 13 | TikTok | Trending | 5,400 | 216 | 4.0% |
| RGD | LinkedIn | Article | 890 | 67 | 7.5% |
| Lucky 13 | Instagram | Carousel | 1,200 | 48 | 4.0% |
| Vegan Table | Facebook | Feed | 940 | 35 | 3.7% |

---

#### Section 4: Alerts & Anomalies (Red/Amber flags)
```
🔴 URGENT: Lucky 13 Location 3 — No posts in 5 days
🟡 WARNING: Vegan Table email bounce rate 3.2% (threshold: 2%)
🟡 WARNING: RGD LinkedIn engagement dropped 40% vs last week
✅ INFO: Vegan Table Reel hit 2,000+ reach (milestone)
```

---

## PAGE 2: BRAND DEEP-DIVES

### Layout: Tab per brand

---

### TAB: THE VEGAN TABLE

#### Row 1: Social Media Metrics (4 scorecards)

| Metric | This Week | Last Week | Target | Status |
|--------|-----------|-----------|--------|--------|
| Instagram Followers | 850 | 800 | 850 | 🟢 |
| Facebook Followers | 2,240 | 2,200 | 2,240 | 🟢 |
| Avg Engagement Rate | 3.8% | 3.2% | 3–4% | 🟢 |
| Story Views (avg) | 120 | 98 | 100+ | 🟢 |

#### Row 2: Email Performance

| Metric | This Week | Benchmark | Status |
|--------|-----------|-----------|--------|
| Emails Sent | 2 | 2/week | 🟢 |
| Open Rate | 28% | 25%+ | 🟢 |
| Click Rate | 4.2% | 3%+ | 🟢 |
| Unsubscribes | 1 | <5/week | 🟢 |
| Bounce Rate | 1.1% | <2% | 🟢 |
| List Size | 320 | +20 from base | 🟢 |

#### Row 3: Paid Ads

| Metric | This Week | Target | Status |
|--------|-----------|--------|--------|
| Impressions | 1,340 | 1,000–1,500 | 🟢 |
| Reach | 980 | 800+ | 🟢 |
| CPC | USD 0.18 | <USD 0.30 | 🟢 |
| CTR | 2.1% | 1.5%+ | 🟢 |
| Conversions (Grab clicks) | 28 | 20+ | 🟢 |
| ROAS | 1.8:1 | 1.5:1+ | 🟢 |
| Spend | USD 25 | USD 25/week | 🟢 |

#### Row 4: Content Calendar Compliance
- **Posts planned this week:** 5
- **Posts published:** 5 ✅
- **Posts on-time:** 4 (1 delayed by 2h)
- **Avg time from brief to publish:** 18h

#### Row 5: Top Performing Content (Bar Chart)
- X-axis: Post type (Reel, Feed, Carousel, Story, TikTok)
- Y-axis: Average engagement rate
- Color: by week

---

### TAB: REALLY GOOD DELI

#### Row 1: LinkedIn Metrics

| Metric | This Week | Last Week | Target | Status |
|--------|-----------|-----------|--------|--------|
| LinkedIn Followers | 130 | 100 | 130 | 🟢 |
| Impressions (articles) | 920 | 650 | 800+ | 🟢 |
| Reactions/Likes | 42 | 28 | 50+ | 🟡 |
| Comments | 8 | 5 | 10+ | 🟡 |
| Profile Views | 65 | 40 | 50+ | 🟢 |
| Connection Requests | 12 | 7 | 10+ | 🟢 |

#### Row 2: B2B Pipeline

| Metric | This Week | Month to Date | Target | Status |
|--------|-----------|---------------|--------|--------|
| Lead Inquiries | 2 | 4 | 3–5/month | 🟢 |
| Calls Scheduled | 1 | 2 | 2+/month | 🟢 |
| New Partners | 0 | 0 | 1/quarter | 🔵 |
| Email Responses (B2B) | 3 | 8 | — | — |

#### Row 3: B2C (Online Orders)

| Metric | This Week | Target | Status |
|--------|-----------|--------|--------|
| Website Visitors | 120 | 100+ | 🟢 |
| Online Orders | 4 | 5–10/month | 🟢 |
| Avg Order Value | THB 680 | THB 500+ | 🟢 |
| Cart Abandonment | 40% | <50% | 🟢 |
| New vs Returning | 70/30 | TBD | — |

#### Row 4: Email (B2B + B2C split)

| Segment | Open Rate | CTR | List Size | Status |
|---------|-----------|-----|-----------|--------|
| B2B contacts | 34% | 6.1% | 85 | 🟢 |
| B2C subscribers | 22% | 3.2% | 95 | 🟢 |

#### Row 5: Paid Ads (Meta + LinkedIn)

| Channel | Spend | Impressions | CPC | ROAS | Status |
|---------|-------|-------------|-----|------|--------|
| Meta B2B | USD 25 | 520 | USD 0.22 | — | 🟢 |
| Meta B2C | USD 25 | 840 | USD 0.19 | 1.6:1 | 🟢 |
| LinkedIn Ads | USD 50 | 680 | USD 0.85 | — | 🟡 |

---

### TAB: LUCKY 13 SANDWICH

#### Row 1: Social Media Metrics

| Metric | This Week | Target | Status |
|--------|-----------|--------|--------|
| Instagram Followers | 680 | 680 | 🟢 |
| Facebook Followers | 260 | 260 | 🟢 |
| TikTok Views (total) | 8,400 | 5,000+ | 🟢 |
| Avg Engagement Rate | 2.5% | 2–3% | 🟢 |

#### Row 2: Dine-In Footfall Proxy Metrics

> Note: Actual footfall from in-store counts. Until POS data is connected, proxies used.

| Metric | This Week | Baseline | Change | Status |
|--------|-----------|----------|--------|--------|
| Google Maps "Directions" clicks | 145 | 112 | +29% ▲ | 🟢 |
| "Call" clicks (GMB) | 38 | 28 | +36% ▲ | 🟢 |
| "Website" clicks (GMB) | 62 | 48 | +29% ▲ | 🟢 |
| Grab orders (maintained?) | 280 | 290 | -3.4% ▼ | 🟡 |

#### Row 3: Location-by-Location Breakdown (Table)

| Location | Impressions | Post Count | Engagement | Footfall Proxy | Status |
|----------|-------------|------------|------------|----------------|--------|
| Location 1 | 1,200 | 2 | 3.1% | +20% | 🟢 |
| Location 2 | 980 | 2 | 2.8% | +18% | 🟢 |
| Location 3 | 440 | 0 | 0% | +2% | 🔴 |
| Location 4 | 760 | 1 | 2.5% | +15% | 🟡 |
| Location 5 | 890 | 2 | 2.9% | +22% | 🟢 |

> 🔴 Location 3 needs immediate attention — no content posted

#### Row 4: Email Performance

| Metric | This Week | Target | Status |
|--------|-----------|--------|--------|
| Emails Sent | 2 | 2/week | 🟢 |
| Open Rate | 22% | 20%+ | 🟢 |
| Click Rate | 3.1% | 2.5%+ | 🟢 |
| List Size | 530 | 530 | 🟢 |

#### Row 5: Paid Ads (Higher Budget)

| Ad Type | Spend | Impressions | CPC | CTR | ROAS | Status |
|---------|-------|-------------|-----|-----|------|--------|
| Brand Awareness | USD 50 | 3,200 | USD 0.14 | 2.8% | — | 🟢 |
| Dine-in Footfall | USD 80 | 2,800 | USD 0.16 | 3.1% | 2.1:1 | 🟢 |
| Promo/Offer | USD 50 | 1,900 | USD 0.18 | 2.4% | 1.9:1 | 🟢 |
| Retargeting | USD 30 | 1,100 | USD 0.12 | 4.2% | 3.0:1 | 🟢 |
| Location-specific | USD 40 | 1,600 | USD 0.15 | 2.9% | 2.3:1 | 🟢 |
| **Total** | **USD 250** | **10,600** | **USD 0.15** | — | **2.1:1** | 🟢 |

---

## PAGE 3: AD PERFORMANCE

### Layout: Cross-brand ad comparison

#### Section 1: Total Ad Spend vs Return (Stacked bar chart)
- X-axis: Brand
- Y-axis: USD spend + attributed revenue
- Color: Spend (red) vs Revenue (green)

#### Section 2: Campaign Performance Table

| Brand | Campaign | Platform | Spend | Impressions | Reach | CPC | CTR | Conv. | ROAS |
|-------|----------|----------|-------|-------------|-------|-----|-----|-------|------|
| VT | Launch Awareness | Meta | USD 40 | 1,340 | 980 | 0.18 | 2.1% | 28 | 1.8:1 |
| RGD | B2B Lead Gen | LinkedIn | USD 50 | 680 | 520 | 0.85 | 1.2% | 3 | — |
| RGD | B2C Retail | Meta | USD 25 | 840 | 620 | 0.19 | 1.8% | 4 | 1.6:1 |
| L13 | Dine-in Drive | Meta | USD 80 | 2,800 | 2,100 | 0.16 | 3.1% | 62 | 2.1:1 |
| L13 | Brand Awareness | Meta | USD 50 | 3,200 | 2,400 | 0.14 | 2.8% | 45 | — |

#### Section 3: A/B Test Tracker

| Brand | Test | Variant A | Variant B | Winner | Confidence | Action |
|-------|------|-----------|-----------|--------|------------|--------|
| VT | Subject line | "We're Back 🌿" | "10 Years. New Energy." | A | 72% | Use A |
| L13 | Ad creative | Food photo | Reel video | Video | 85% | Scale video |
| RGD | CTA | "Schedule a Call" | "Learn More" | A | 68% | Keep testing |

---

## SETUP INSTRUCTIONS

### Looker Studio Data Sources
1. **Meta Ads Manager** → Connect via Meta API connector
2. **Google Analytics 4** → Connect via GA4 connector (one property per brand)
3. **Google Business Profile** → Connect via GBP connector (Lucky 13 locations)
4. **LinkedIn Analytics** → Manual CSV import (weekly) until API available
5. **Email Platform** → Mailchimp/Klaviyo connector
6. **Grab** → Manual data entry (no API available)

### Access Levels
| Person | Access Level | Can Edit? |
|--------|-------------|-----------|
| Dan | Editor | Yes |
| Panda (Analytics Bot) | Editor | Yes |
| Brand managers | Viewer | No |
| Clients | Viewer (report link) | No |

### Refresh Schedule
- Meta, GA4, GBP: Daily at 6 AM Bangkok time
- Email: After each send + daily refresh
- LinkedIn: Weekly (Monday 8 AM)
- Grab: Manual entry by PM Bot (weekly)

---

## WEEKLY DIGEST FORMAT (Automated)

Sent every **Monday 8 AM** to Dan via Telegram:

```
📊 SIMILAN WEEKLY DIGEST — Week of [Date]

THE VEGAN TABLE 🌿
✅ Followers: 850 (+50)
✅ Engagement: 3.8%
✅ ROAS: 1.8:1
⚠️ Email bounce rate slightly elevated (monitor)

REALLY GOOD DELI 🥩
✅ LinkedIn Impressions: 920 (+270)
✅ B2B Leads: 4 this month
🔴 LinkedIn engagement dipped — review content for week

LUCKY 13 🥪
✅ TikTok Views: 8,400 (above target)
✅ ROAS: 2.1:1
🔴 Location 3 — 0 posts this week (immediate action needed)
✅ Dine-in proxy +22% ▲

ACTION ITEMS:
1. RGD — Review LinkedIn content strategy
2. L13 — Content for Location 3 urgently needed
3. VT — Monitor email bounce rate

Full dashboard: [Looker Studio link]
```

---

## KPIs BY PHASE

### Phase 1 (Months 1–2): Establishment
| Brand | Primary KPI | Target |
|-------|-------------|--------|
| Vegan Table | Engagement rate | 3–4% |
| RGD | B2B lead inquiries | 3–5/month |
| Lucky 13 | Dine-in footfall proxy | +20% |

### Phase 2 (Month 3): Optimization
| Brand | Primary KPI | Target |
|-------|-------------|--------|
| Vegan Table | Email list growth | +50 subscribers |
| RGD | Online orders | 15+ orders/month |
| Lucky 13 | ROAS | 2.5:1+ |

### Phase 3 (Months 4–6): Scale
| Brand | Primary KPI | Target |
|-------|-------------|--------|
| Vegan Table | Footfall | +35% vs baseline |
| RGD | B2B partnerships closed | 2 new hotels |
| Lucky 13 | Dine-in % of sales | 40%+ (from 10–30%) |

---

## ESCALATION RULES (Auto-alerts to Dan)

| Trigger | Alert Level | Action |
|---------|-------------|--------|
| ROAS drops below 1.0:1 for 3 days | 🔴 URGENT | Pause ads, notify Dan |
| Engagement rate drops >40% WoW | 🟡 WARNING | Review content, report |
| Negative review (1–2 stars) | 🔴 URGENT | Notify Dan within 1h |
| Account security anomaly | 🔴 URGENT | Lock account, notify immediately |
| Email bounce rate >3% | 🟡 WARNING | Review list health |
| Ad spend 20% over budget | 🟡 WARNING | Pause + notify Dan |
| No posts published for 48h | 🟡 WARNING | Check content pipeline |

---

*Dashboard last updated: March 14, 2026*  
*Built by: Panda / Similan Digital*
