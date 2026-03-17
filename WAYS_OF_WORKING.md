# Similan Digital: Ways of Working

## How We Operate

This document consolidates all tools, APIs, processes, and best practices that power Similan Digital. It's the agency's operating manual.

---

## 1. TOOLS & PLATFORMS INVENTORY

### 1.1 Core Marketing Platforms

#### **Meta Business Suite + Ads Manager**
**What:** Facebook Page management, Instagram Business account management, Meta Ads creation/optimization

**Used for:**
- Posting to Lucky 13, Vegan Table, Really Good Deli (FB & Instagram)
- Creating & managing paid ad campaigns (Meta/Instagram ads)
- Community management (comments, DMs, moderation)
- Analytics (impressions, reach, engagement)

**Access:**
- Dan's Meta account (owner)
- Business Account ID: [To be filled by Dan]
- Pages: 3 (Lucky 13, Vegan Table, RGD)
- Credentials: Stored in .env (never hardcoded)

**APIs:**
- Business Account API (read followers, audience, metrics)
- Graph API (publish posts, read/manage comments)
- Ads Manager API (create campaigns, set budgets, optimize)

**Rate limits:**
- Business tier: 200 API calls/day
- Implement batch requests to stay under limit
- Exponential backoff on 429 errors (too many requests)

**Workflows:**
1. **Daily:** Analytics Bot pulls metrics (followers, engagement, reach)
2. **3x/week:** Community Manager Bot monitors comments, flags escalations
3. **Weekly:** Paid Ads Bot optimizes campaigns (budget reallocation, audience refinement)
4. **As needed:** Dan posts approved content (or delegates to team member)

**Troubleshooting:**
- Token expired? → Re-authenticate via Meta's OAuth flow
- Ad campaign rejected? → Check for policy violations (alcohol, health claims, misleading)
- Engagement dropped? → Check for algorithm changes, audience fatigue, content quality

---

#### **Google Analytics 4 (GA4)**
**What:** Website traffic tracking, user behavior, conversion metrics

**Used for:**
- Track Lucky 13 website traffic (landing page + delivery links)
- Track Vegan Table website traffic (if online ordering added)
- Track Really Good Deli website traffic (e-commerce, B2B inquiry forms)
- Measure content impact (clicks from social → website)

**Access:**
- Dan's Google account (owner)
- Properties: 3 (one per brand website)
- Credentials: Service account (JSON key) stored in .env

**APIs:**
- Google Analytics Data API v1
- Used by Analytics Bot to pull daily metrics

**Events to track:**
- Page views
- Scroll depth (how far users scroll)
- Button clicks (e.g., "Order on Grab", "Contact for wholesale")
- Form submissions (email signup, inquiry form)
- Outbound clicks (to delivery platforms, WhatsApp, phone)

**Rate limits:**
- 10,000 requests/day
- Batch up to 5 queries per API call

**Workflows:**
1. **Daily:** Analytics Bot pulls GA4 data, updates KPI dashboard
2. **Weekly:** Dan reviews website traffic in digest
3. **Monthly:** Analytics Bot identifies traffic trends, proposes content changes

**Troubleshooting:**
- No data showing? → Check that tracking code is installed on website
- Data delay? → GA4 can have 24–48h processing lag (expected)
- Spikes in traffic? → Check for viral post, paid ad campaign, or bot traffic (filter bots in GA4 settings)

---

#### **Google Ads**
**What:** Search ads, display ads, YouTube ads (if used)

**Status:** Currently NOT SET UP (see Phase 1 setup checklist)

**Plan:** Set up when/if needed (currently Meta ads are sufficient for F&B/local)

**When to activate:**
- If Lucky 13 needs search visibility for keywords ("sandwich near me", "dine-in Phuket")
- If Really Good Deli needs B2B search ads ("wholesale deli", "food supplier Bangkok")

**Credentials:** TBD

**APIs:** Google Ads API

**Rate limits:** TBD

---

#### **Email Platform (TBD — Review April 1)**
**Status:** Decision deferred to April after first month of data

**Options under consideration:**
- Mailchimp (free tier, simple UI, good for startups)
- Klaviyo (more powerful segmentation, better analytics)

**Will be used for:**
- Lucky 13: Weekly newsletter (specials, location updates, new items)
- Vegan Table: Bi-weekly newsletter (menu updates, events, wellness tips)
- Really Good Deli: Monthly B2B newsletter (new products, partnerships, industry insights)

**Access:**
- Dan's Mailchimp account (owner)
- 3 audiences (one per brand)

**Current subscribers:**
- Lucky 13: ~500
- Vegan Table: ~300
- Really Good Deli: ~200 (B2B)

**APIs:**
- Marketing API (send campaigns, manage lists, track opens/clicks)
- Subscriber Sync (bulk import/export)

**Rate limits:**
- 10 requests per second
- Batch operations for bulk actions

**Workflows:**
1. **Weekly:** Copywriter Bot drafts newsletter template
2. **Dan approval:** Reviews content, approves send
3. **Mailchimp:** Campaign scheduled (usually Tuesday 9 AM local time for best open rates)
4. **Post-send:** Analytics tracked (open rate, click rate, unsubscribe rate)

**Best practices:**
- Keep subject lines <50 characters
- Use brand-specific templates (consistent look)
- Segment lists by customer type (dine-in vs delivery for Lucky 13)
- Clean lists monthly (remove inactive subscribers)

**Troubleshooting:**
- Emails going to spam? → Check sender authentication (SPF, DKIM, DMARC records)
- Low open rates? → Test different subject lines, send times
- Unsubscribe rate high? → Review frequency (not too many emails), content relevance

---

#### **Asana (Project Management)**
**What:** Task tracking, content calendar, workflow automation, team coordination

**Used for:**
- 30-day content calendar per brand
- Task assignments (bot tasks, human tasks)
- Deadline tracking
- Status updates
- Automations (trigger notifications, log completions)

**Access:**
- Dan's Asana account (owner)
- 4 projects: Lucky 13, Vegan Table, Really Good Deli, Cross-client

**Structure:**
```
Each project contains:
├── Content Calendar (board view, sorted by week/channel)
├── Campaigns (board view, one card per campaign)
├── Tasks (list view, includes bot tasks, human approvals)
├── Reports (custom views, summaries by bot)
└── Timeline (Gantt view for campaign timelines)
```

**APIs:**
- REST API (read/write tasks, manage projects, update status)
- Webhooks (trigger actions on task changes)

**Rate limits:**
- 150 requests/minute

**Workflows:**
1. **Friday EOD:** Content Manager Bot creates task cards for next week's content
2. **Monday 9 AM:** Dan reviews week's tasks in Asana, approves calendar
3. **Tue–Fri:** Bots update task status as they work (drafting, designing, copywriting)
4. **Task completion:** Bot marks done, Project Manager Bot triggers archive workflow
5. **Weekly:** Dan views Asana summary in digest

**Automations:**
- Task status = "Needs Approval" → Send Telegram message to Dan
- Task due date = today → Notify assigned bot
- Task completed → Archive to previous week's folder

**Troubleshooting:**
- Tasks not syncing? → Check webhook configuration
- Automations not firing? → Verify rule conditions, timing
- Performance slow? → Too many tasks per project (archive old ones)

---

#### **Telegram (Communication)**
**What:** Real-time alerts, daily digests, content approvals, crisis escalation

**Used for:**
- **@SimilanSecurityAlerts** — Security threats, credential leaks, customer complaints (HIGH PRIORITY)
- **@SimilanDailyDigest** — Morning summary (LOW PRIORITY, informational)
- **@SimilanApprovals** — Posts awaiting Dan review (MEDIUM PRIORITY, actionable)

**Bot setup:**
- Bot name: Similan Digital Bot
- Bot token: Stored in .env (NEVER share)
- Channels: 3 (security, digest, approvals)

**APIs:**
- Telegram Bot API (send messages, handle reactions)

**Rate limits:**
- 30 messages/second per bot
- Batch non-urgent updates (combine into one message)

**Workflows:**
1. **Real-time (24/7):**
   - Security Bot detects threat → Sends alert to @SimilanSecurityAlerts
   - Community Manager Bot flags customer complaint → Sends to @SimilanSecurityAlerts
   - Project Manager Bot detects missed deadline → Sends to @SimilanApprovals

2. **Daily (9 AM Bangkok time):**
   - Analytics Bot compiles overnight metrics → Sends to @SimilanDailyDigest
   - Includes: follower changes, engagement summary, pending approvals, security status

3. **On-demand:**
   - Copywriter Bot drafts ad copy → Sends to @SimilanApprovals
   - Dan reacts: ✅ (approve), 📝 (revise), ❌ (reject)

**Message format (example):**
```
🔐 SECURITY ALERT — Credential Detected
Platform: Meta Business API
Risk: CRITICAL
Found in: Facebook post draft (Really Good Deli campaign)
Action taken: Auto-quarantine, removed from system
Details: Instagram access token partially exposed in image alt text
Recommended: Rotate Instagram token ASAP

Dan, please confirm once you've rotated credentials.
```

**Troubleshooting:**
- Bot not sending messages? → Check token validity, network connectivity
- Messages delayed? → Check Telegram's rate limiting, reduce batch size
- Dan not seeing alerts? → Verify Dan is member of channel, notifications enabled

---

### 1.2 Design & Content Tools

#### **Canva (or Alternative: Adobe Express)**
**What:** Graphic design templates, quick visual creation

**Used for:**
- Creating Instagram posts (templates + customization)
- Designing email headers, banners
- Building carousel graphics (5–10 slides)
- Ad creative (Meta ads, social ads)

**Access:**
- Dan's Canva account or Visual Designer Bot's workspace
- Team account recommended (easier sharing)

**How Visual Designer Bot uses it:**
1. Start with brand template (colors, fonts loaded)
2. Input text/copy from Content Manager Bot
3. Select photos from BRAND_ASSETS/photos/ or photographer library
4. Generate 3 variations
5. Export as PNG (1080×1080 for Instagram)
6. Save to APPROVED_POSTS folder
7. Notify Project Manager Bot when ready

**Troubleshooting:**
- Bot can't access Canva? → Use API if available, or manual design workflow
- Design inconsistency? → Ensure bot is using correct brand template
- Performance issues? → Pre-design templates offline, use Canva only for copy swaps

---

#### **Adobe Premiere Pro / DaVinci Resolve (Video Editing)**
**What:** Edit Reels, TikToks, short-form video content

**Used for:**
- Trim/edit raw footage from photographer
- Add captions, transitions, music
- Create 15–30s clips for social
- Optimize aspect ratios per platform

**Access:**
- Dan's Adobe Creative Cloud or DaVinci Resolve (free version)
- Video Editor Bot workflows (likely manual or semi-automated)

**Workflows:**
1. **Monthly:** Photographer delivers raw video clips
2. **Video Editor Bot:** Reviews, categorizes by brand
3. **Project Manager Bot:** Schedules editing tasks
4. **Editing process:** 3–5 day turnaround per clip
5. **Output:** Export as MP4, optimized for platform
6. **Archive:** Store in BRAND_ASSETS/videos/

**Troubleshooting:**
- Long render times? → Use lower resolution proxies during editing
- Format issues? → Export as H.264 MP4, 1080p, 30fps
- Audio sync problems? → Ensure photographer provides synced files

---

### 1.3 Analytics & Reporting

#### **Looker Studio (Google's Free BI Tool)**
**What:** Custom dashboards, real-time reporting, data visualization

**Used for:**
- KPI dashboard (followers, engagement, website traffic, email metrics)
- Executive summary (Dan views anytime, no login needed)
- Trend analysis (30-day, 90-day, 12-month)
- Competitor benchmarking

**Access:**
- Dan's Google account (owner)
- Public link (embeddable, no credentials needed for Dan)

**Data sources:**
- Google Analytics 4 (website traffic)
- Meta Business API (followers, engagement)
- Mailchimp API (email open/click rates)
- Custom JSON (pulled by Analytics Bot, stored in Google Drive)

**Dashboards:**
1. **Lucky 13 Sandwich Dashboard**
   - Metric 1: Instagram followers (trend + daily delta)
   - Metric 2: Instagram engagement rate (% of followers engaging)
   - Metric 3: Top posts (this week, last week, all-time)
   - Metric 4: Website traffic (landing page visits, Grab order clicks)
   - Metric 5: Email subscriber growth + open/click rates
   - Metric 6: Footfall proxy (website traffic as proxy for foot traffic)

2. **The Vegan Table Dashboard** (same metrics)

3. **Really Good Deli Dashboard**
   - Metric 1: LinkedIn followers + engagement
   - Metric 2: Facebook followers + engagement
   - Metric 3: Website leads (inquiry form submissions)
   - Metric 4: Email metrics (B2B newsletter)
   - Metric 5: Sales pipeline (custom metric, requires CRM integration)

4. **Agency Dashboard (Similan Digital)**
   - Combined metrics across 3 brands
   - Competitor benchmarking (Prime Burger vs Lucky 13, etc.)
   - Team performance (bots' output volume, quality metrics)

**Refresh rate:** Hourly (Analytics Bot pushes updates to Google Drive, Looker Studio pulls)

**Workflows:**
1. **Daily:** Analytics Bot updates Google Drive CSV with latest metrics
2. **Looker Studio:** Auto-refreshes (hourly)
3. **Dan:** Views dashboard anytime, spots trends
4. **Weekly:** Analytics Bot writes digest summary (highlights, trends)
5. **Monthly:** Analytics Bot creates detailed report (30-day analysis)

**Troubleshooting:**
- Dashboard shows no data? → Check data source connections (GA4, Meta API)
- Refresh delayed? → Check Analytics Bot's scheduled task, network connectivity
- Chart looks wrong? → Verify data aggregation (sum vs average vs count)

---

### 1.4 Collaboration & Documentation

#### **Google Drive + Docs/Sheets**
**What:** Shared file storage, collaborative documents, real-time editing

**Used for:**
- Storing SIMILAN_AGENCY_SETUP/ directory (this entire structure)
- Collaborative docs (CONTENT_CALENDAR, CAMPAIGN_BRIEFS, REPORTS)
- Sharing brand guidelines (Dan uploads PDFs)
- Sharing competitor research (screenshots, analysis)
- Version history (track changes over time)

**Folder structure:** Mirrors SIMILAN_FILE_STRUCTURE.md

**Access:**
- Dan's Google account (owner)
- Bots have read access (via service account)
- Real-time sync (files updated in Drive appear in local workspace)

**Security:**
- No sensitive credentials in Drive (use .env instead)
- Brand guidelines: Share only with team (not public)
- API keys: NEVER store in Drive

**Workflows:**
1. **Content Calendar:** Dan + bots collaboratively edit (Dan writes feedback, Content Manager Bot updates)
2. **Competitive Research:** Analyst bot adds findings, Dan reviews
3. **Weekly Reports:** Analytics Bot writes in Google Doc, Dan reads/exports to PDF

---

## 2. API CREDENTIALS & SECURE STORAGE

### 2.1 Where Credentials Live

**NEVER hardcoded in code. ALWAYS in `.env` file.**

```
# .env (local, git-ignored, never committed)
META_ACCESS_TOKEN=eaa123456789abcdef...
META_BUSINESS_ACCOUNT_ID=12345678...
GOOGLE_ANALYTICS_KEY=/path/to/ga4-key.json
MAILCHIMP_API_KEY=abc123def456...
ASANA_AUTH_TOKEN=1/123456789...
TELEGRAM_BOT_TOKEN=123456789:ABCdef...
GOOGLE_APPLICATION_CREDENTIALS=/path/to/key.json
OPENAI_API_KEY=sk-...  (for Security Bot content moderation)
```

**Security practices:**
- ✅ Rotate credentials every 3 months
- ✅ Use service accounts (not personal accounts) where possible
- ✅ Use OAuth tokens instead of passwords
- ✅ Store .env in secure location (encrypted if possible)
- ✅ Never share .env file via email or Slack
- ✅ Audit credential usage (check API access logs monthly)

**If credential is exposed:**
1. Immediately rotate (generate new token/key)
2. Revoke old credential in platform (Meta, Google, Mailchimp, etc.)
3. Alert Dan via Telegram (Security Alert)
4. Document incident (date, what was exposed, action taken)
5. Review logs to see if exposed credential was misused

---

### 2.2 Credential Rotation Schedule

| Platform | Credential | Rotation | Owner |
|----------|-----------|----------|-------|
| Meta Business | Access token | Every 3 months | Dan |
| Google Analytics | Service key | Every 6 months | Dan |
| Mailchimp | API key | Every 6 months | Dan |
| Asana | OAuth token | Every 3 months | Dan |
| Telegram | Bot token | Every 6 months | Dan |

---

## 3. BOT WORKFLOWS & INTERACTIONS

### 3.1 Content Creation Pipeline

**Day 1 (Monday):** Content Manager Bot drafts 5 posts for the week

```
Input:
- Brand guidelines + past top posts
- Content calendar (from Asana)
- Trending topics (hashtags, seasonal)

Output:
- 5 post drafts (copy + hashtag suggestions)
- Sent to Visual Designer Bot + Copywriter Bot

Time: 2–3 hours (bot processing)
```

**Day 1–2 (Mon–Tue):** Visual Designer Bot creates graphics

```
Input:
- Post copy from Content Manager Bot
- Brand assets (colors, fonts, templates)
- Photo library (from photographer)

Output:
- 5 designs (PNG, 1080×1080)
- 3 variations per post (A/B test options)
- Sent to Security Bot

Time: 2–4 hours
```

**Day 2 (Tue AM):** Security Bot reviews all content

```
Input:
- Post copy + graphics
- Brand guidelines
- Compliance checklist (Thai law, PDPA, OWASP)

Output:
- ✅ PASS: Queued for Dan approval
- ❌ FAIL: Auto-quarantine + Telegram alert to Dan
  - Example failures: Credential exposed, malware, health claim, political content

Time: 30 min – 1 hour
```

**Day 2 (Tue afternoon):** Dan reviews & approves

```
Input:
- 5 approved posts (copy + graphics)
- Via Telegram @SimilanApprovals channel

Dan's actions:
- ✅ Approve (post goes to queue)
- 📝 Revise (return to bot with feedback)
- ❌ Reject (pull and start over)

Timeline: <24h turnaround (ideally same day)
Output: Approved posts scheduled in Asana
```

**Day 3–4 (Wed–Thu):** Project Manager Bot schedules posting

```
Input:
- Approved posts from Asana
- Content calendar (timing, channel, platform)

Output:
- Posts scheduled in project management tool
- Dan/human gets reminder to post to live channel
- Notification sent to Dan via Telegram

Time: 1 hour (scheduling + notification)
```

**Day 5–7 (Fri–Sun):** Dan posts to live channels

```
Input:
- Scheduled post from Project Manager Bot
- Via Meta Business Suite (Dan or team member)

Output:
- Post goes live on Facebook, Instagram, TikTok (depending on brand)
- Monitoring begins (Community Manager Bot watches comments)
```

**Monitoring (ongoing):** Community Manager Bot monitors engagement

```
Input:
- Live posts on all channels
- Comments, DMs, mentions

Output:
- Routine comments: Auto-respond (friendly, helpful)
- Escalations: Flag to Dan via Telegram (@SimilanSecurityAlerts)
  - Customer complaint
  - Brand-sensitive question
  - Legal/PR issue

Time: 24/7 monitoring
```

**Weekly archive:** Dan reviews performance

```
Input:
- Post metrics (likes, comments, shares, reach)
- Engagement rate
- Community sentiment

Output:
- APPROVED_POSTS/2026-03-week1.md (lessons learned)
- Feedback to Content Manager Bot (what worked, what didn't)

Time: Friday EOD review
```

---

### 3.2 Bot Interaction Matrix

```
Who talks to whom?

CONTENT MANAGER BOT
├─→ Visual Designer Bot (send copy for design)
├─→ Copywriter Bot (request longer-form versions)
├─→ Project Manager Bot (notify drafts ready)
└─→ Security Bot (request review)

VISUAL DESIGNER BOT
├─→ Content Manager Bot (request copy/captions)
├─→ Project Manager Bot (notify designs ready)
└─→ Security Bot (request review)

COPYWRITER BOT
├─→ Content Manager Bot (receive brief, send longer content)
├─→ Visual Designer Bot (if text overlay needed)
├─→ Project Manager Bot (notify copy ready)
└─→ Security Bot (request review)

PAID ADS BOT
├─→ Content Manager Bot (get content for ad creative)
├─→ Visual Designer Bot (get ad graphics)
├─→ Analytics Bot (get performance data to optimize)
└─→ Dan (notify of budget changes >±20%)

COMMUNITY MANAGER BOT
├─→ Escalation Bot (flag customer issues)
└─→ Dan (via Telegram alerts)

ANALYTICS BOT
├─→ All bots (provide performance feedback)
├─→ Dan (via daily digest + monthly report)
└─→ Looker Studio (push data to dashboard)

PROJECT MANAGER BOT
├─→ All bots (receive task updates, send reminders)
├─→ Asana (update task status, manage timelines)
└─→ Dan (notify of milestones, blockers)

SECURITY BOT
├─→ All bots (scan outputs before release)
├─→ Dan (via @SimilanSecurityAlerts for threats)
└─→ Code review (YARA, Semgrep, bandit scans)

INFLUENCER OUTREACH BOT (Phase 3 only)
├─→ Community Manager Bot (coordinate brand partnerships)
└─→ Dan (approve partnerships, agreements)

Internal comms: Asana + Telegram (ops channel)
External comms: Telegram (Dan's channels) + email (if needed)
```

---

### 3.3 Approval Gates

**Every piece of content goes through gates in this order:**

```
GATE 1: Security Bot
- Scans for: malware, credentials, compliance violations
- Output: PASS or FAIL (auto-quarantine if fail)

GATE 2: Dan's Review (Telegram)
- Scans for: brand fit, quality, tone
- Output: APPROVE, REVISE, REJECT

GATE 3: Project Manager Bot
- Checks: Scheduling, channel appropriateness, audience
- Output: Schedule for posting

GATE 4: Posting (Dan or team member)
- Action: Post to live channel (FB, Instagram, TikTok, etc.)

Post-posting monitoring (24/7)
- Community Manager Bot watches for issues
- Escalates to Dan if needed
```

**No content bypasses Security Bot.** All posts queued, all posts checked.

---

## 4. COMMUNICATION PROTOCOLS

### 4.1 Telegram Channels

**@SimilanSecurityAlerts** (HIGH PRIORITY)
- Message source: Security Bot, Community Manager Bot
- Frequency: As needed (immediate escalation)
- Who reads: Dan
- Action required: YES (resolve issue ASAP)
- Example messages:
  ```
  🔐 MALWARE DETECTED in post draft
  Payload: XSS attack in Facebook post caption
  Status: Quarantined, removed from system
  Action: None required (auto-handled)
  ```

  ```
  ⚠️ CUSTOMER COMPLAINT — Google My Business
  Branch: Lucky 13 (Phuket Town)
  Issue: "Food poisoning symptoms after eating here"
  Severity: CRITICAL
  Recommended: Contact manager, offer resolution, monitor for more complaints
  Dan should: Respond publicly within 1 hour
  ```

**@SimilanDailyDigest** (LOW PRIORITY)
- Message source: Analytics Bot
- Frequency: Daily (9 AM Bangkok time)
- Who reads: Dan
- Action required: NO (informational)
- Example message:
  ```
  📊 DAILY DIGEST — March 14, 2026

  Lucky 13 Sandwich:
  - Instagram: +12 new followers (1,240 total)
  - Engagement rate: 3.8% (↑ 0.2% from yesterday)
  - Top post: Italian Sub launch (47 likes, 8 comments)
  
  The Vegan Table:
  - Facebook: +8 new followers (2,200 total)
  - Email subscribers: +3 (303 total)
  
  Really Good Deli:
  - Website leads: 5 form submissions
  - LinkedIn engagement: 2.1% (avg)
  
  Pending approvals: 2 posts awaiting your review
  Security status: ✅ All clear (0 threats detected)
  
  Full dashboard: [Looker Studio link]
  ```

**@SimilanApprovals** (MEDIUM PRIORITY)
- Message source: Content Manager Bot, Copywriter Bot, Visual Designer Bot
- Frequency: 3–5 posts per day (Tue–Fri)
- Who reads: Dan
- Action required: YES (approve/revise/reject within 24h)
- Example message:
  ```
  📸 INSTAGRAM POST — Lucky 13 Sandwich (Tue, Mar 18 @ 9 AM)
  
  Copy:
  "Ever tried a sandwich so good it changed your mind? 🥪
  Lucky 13's new Italian Sub is here, made fresh daily.
  Grab yours today at [location] or order on Grab! 🚚"
  
  Visual: [Embedded image preview]
  Hashtags: #lucky13phuket #sandwich #fresh #phuket #foodie
  
  Respond with: ✅ approve | 📝 revise | ❌ reject
  ```

---

### 4.2 Response Time Expectations

| Message Type | Channel | Dan's SLA | Notes |
|--------------|---------|-----------|-------|
| Security alert | @Alerts | <1 hour | Critical issues (malware, creds leaked) |
| Customer complaint | @Alerts | <2 hours | Negative reviews, complaints |
| Content approval | @Approvals | <24 hours | Can be async (Dan reviews daily) |
| Daily digest | @Digest | N/A | FYI only, no response needed |

---

### 4.3 How to Escalate

**Customer issue (complaint, negative review):**
1. Community Manager Bot flags in @SimilanSecurityAlerts
2. Dan reviews, determines severity (LOW/MEDIUM/HIGH)
3. Dan responds publicly (acknowledge, apologize, offer solution)
4. Follow-up: Document in ESCALATIONS folder, prevent future

**Security threat (malware, credential leak):**
1. Security Bot auto-quarantines content
2. Alerts Dan in @SimilanSecurityAlerts
3. Dan rotates credentials if exposed
4. Follow-up: Review what happened, tighten rules

**Budget alert (ad spend overage):**
1. Paid Ads Bot detects spend > ±20% threshold
2. Alerts Dan in @SimilanApprovals
3. Dan approves or rejects budget increase
4. Bot pauses/resumes campaigns based on response

---

## 5. OPERATIONAL PROCESSES

### 5.1 Weekly Cadence

```
MONDAY (9 AM):
├─ Analytics Bot sends @SimilanDailyDigest (overnight metrics)
├─ Content Manager Bot reviews last week's performance (APPROVED_POSTS)
├─ Dan reviews content calendar for week (Asana board)
├─ Dan approves weekly themes + messaging direction
└─ Project Manager Bot assigns tasks to bots

TUESDAY (9 AM):
├─ Content Manager Bot drafts 5 posts (Mon posts)
├─ Visual Designer Bot creates graphics (Mon posts)
├─ Security Bot reviews all outputs
├─ Dan approves posts via @SimilanApprovals
└─ Project Manager Bot schedules approved posts

WEDNESDAY (9 AM):
├─ Content Manager Bot drafts 5 posts (Wed posts)
├─ [Same review/approval process]
├─ Community Manager Bot monitors Mon posts (comments, engagement)
└─ Paid Ads Bot optimizes running campaigns

THURSDAY (9 AM):
├─ Content Manager Bot drafts 5 posts (Thu posts)
├─ [Same review/approval process]
├─ Paid Ads Bot reports on ad performance
└─ Analytics Bot flags any anomalies (engagement drop, etc.)

FRIDAY (9 AM):
├─ Content Manager Bot drafts 5 posts (Fri posts)
├─ [Same review/approval process]
├─ Dan reviews week's performance (all posts, engagement, followers)
├─ Analytics Bot prepares WEEK_N_DIGEST
└─ End of week archive (APPROVED_POSTS/2026-03-week-N.md)

WEEKEND (Saturday/Sunday):
├─ Community Manager Bot monitors weekend engagement
├─ Security Bot continues 24/7 threat monitoring
├─ No posting (unless special event/crisis)
└─ Bots on standby (no new tasks)
```

---

### 5.2 Monthly Cadence

```
LAST FRIDAY OF MONTH:
├─ Content Manager Bot reviews month's performance (top posts, themes)
├─ Analytics Bot prepares MONTHLY_REPORT
│   ├─ 30-day metrics (followers, engagement, traffic)
│   ├─ Trend analysis (what changed, why)
│   ├─ Competitor benchmarking
│   └─ Recommendations for next month
├─ Dan reviews & provides feedback
└─ Archive old campaigns to /ARCHIVES

FIRST MONDAY OF NEW MONTH:
├─ Dan + Content Manager Bot create next month's content calendar
├─ Monthly planning meeting (if needed)
├─ Photographer provides next month's photo/video library
├─ New theme/campaign briefs written (if applicable)
└─ Asana projects reset with new tasks

MID-MONTH (around 15th):
├─ Analytics Bot checks 15-day metrics vs goals
├─ Paid Ads Bot optimizes budgets based on performance
├─ Copywriter Bot analyzes email engagement (open/click rates)
└─ Any adjustments made to strategy/messaging
```

---

### 5.3 Quarterly Review

```
EVERY 3 MONTHS (end of Q1, Q2, Q3, Q4):
├─ Comprehensive analysis of all 3 brands
├─ KPI progress vs 6-month goals (set in Phase 1)
├─ Competitor benchmarking update
├─ Team retrospective (bots performing well, any issues)
├─ Budget optimization (reallocate between brands if needed)
├─ Credential rotation (Dan rotates Meta, Google, other tokens)
├─ Security audit (Security Bot reviews for vulnerabilities)
└─ Plan for next quarter
```

---

## 6. DATA RETENTION & ARCHIVAL

### 6.1 What to Keep

**Keep indefinitely:**
- Client briefs (CLIENTS/*/CLIENT_BRIEF.md)
- Brand assets (CLIENTS/*/BRAND_ASSETS/)
- Successful campaigns (CLIENTS/*/CAMPAIGN_BRIEFS/)
- Competitor research (COMPETITOR_RESEARCH/)
- Bot system prompts (BOTS/*/SYSTEM_PROMPT.md)

**Keep for 6 months:**
- Weekly digests (REPORTS/*)
- Performance data (CLIENTS/*/PERFORMANCE_DATA/)
- Approved posts (CLIENTS/*/APPROVED_POSTS/)

**Keep for 12 months:**
- Monthly reports (REPORTS/*/MONTHLY_REPORT.md)
- Escalations (CLIENTS/*/ESCALATIONS/)
- Security reports (REPORTS/*/SECURITY_REPORT.md)

**After 6 months:** Archive old APPROVED_POSTS to /ARCHIVES
**After 12 months:** Archive old performance data & reports to /ARCHIVES

### 6.2 Backup Schedule

- **Daily:** Automatic Google Drive sync
- **Weekly:** Manual snapshot (date-stamped folder)
- **Monthly:** Download full /SIMILAN_AGENCY_SETUP to external drive

---

## 7. TROUBLESHOOTING & ESCALATION

### 7.1 Common Issues

**Problem: Post approval is delayed (>24h)**
- Cause: Dan busy, approval queue backlogged
- Solution: Priority queue (mark urgent posts), batch approvals, async workflow
- Prevention: Clear expectations on SLA, break into smaller batches

**Problem: Engagement rate dropped 20%+**
- Cause: Algorithm change, content fatigue, audience shift
- Solution: Analytics Bot flags immediately, Dan investigates, Content Manager Bot diversifies content
- Prevention: Regular audience analysis, A/B test creative, refresh hashtags

**Problem: API rate limit exceeded**
- Cause: Too many bot requests at once
- Solution: Implement exponential backoff, batch requests, stagger timing
- Prevention: Monitor API usage, optimize request patterns, upgrade tier if needed

**Problem: Security threat detected (malware in post)**
- Cause: Bot generated malicious content (unlikely but possible)
- Solution: Security Bot quarantines, Dan reviews, bot is retrained
- Prevention: Regular Security Bot testing, code reviews, input validation

**Problem: Credential leaked (token exposed in post)**
- Cause: Bot copy included sensitive data
- Solution: Rotate token immediately, review logs for misuse, retrain bot
- Prevention: Security Bot checks all outputs, no secrets in templates

**Problem: Dan didn't respond to approval request (72h+)**
- Cause: Dan traveling, busy, forgot
- Solution: Escalate via Telegram (mention @dan), move to backup approval (human team member)
- Prevention: Set up deputy approver for when Dan unavailable

---

### 7.2 Escalation Path

```
ISSUE DETECTED
    ↓
Level 1: Bot tries to handle
├─ If fixable: Resolve autonomously (log action)
└─ If not fixable: → Level 2

Level 2: Dan notified via Telegram
├─ Security issues (@SimilanSecurityAlerts) — ASAP
├─ Customer complaints (@SimilanSecurityAlerts) — <2h
├─ Content approval (@SimilanApprovals) — <24h
├─ Metrics anomalies (@SimilanDailyDigest) — no urgency
└─ If Dan doesn't respond in SLA → Level 3

Level 3: Escalation to backup person (TBD)
├─ Backup approver (if Dan unavailable)
├─ Operations manager (if business impact)
└─ Client contact (if client-specific issue)
```

---

## 8. SECURITY BEST PRACTICES

### 8.1 Credential Management

**Never:**
- ❌ Hardcode API keys in Python, JavaScript, or any code
- ❌ Commit .env to git/GitHub
- ❌ Share credentials via email, Slack, or unencrypted chat
- ❌ Use personal accounts for API credentials (use service accounts)
- ❌ Reuse credentials across multiple services

**Always:**
- ✅ Store credentials in .env file (git-ignored)
- ✅ Use OAuth tokens where possible (instead of passwords)
- ✅ Rotate tokens every 3–6 months
- ✅ Use service accounts with minimal permissions
- ✅ Log all API access (audit trail)
- ✅ Alert Dan if credential is exposed

### 8.2 Code & File Security

**For .md & skill files:**
- ✅ No hardcoded secrets
- ✅ Safe functions (no arbitrary exec, proper input validation)
- ✅ Follow OpenClaw spec
- ✅ PDPA compliance (no personal data exposure)
- ✅ Thai advertising regulations (no alcohol, royal refs, health claims)

**Security Bot checks:**
- YARA rules (malware signatures)
- truffleHog (credential patterns)
- Semgrep (code patterns, vulnerabilities)
- Custom checks (brand guidelines, compliance)

### 8.3 Incident Response

**If credential is exposed:**
1. Rotate immediately (generate new token)
2. Revoke old credential in platform
3. Alert Dan via Telegram (🔐 SECURITY ALERT)
4. Review API access logs (check for unauthorized use)
5. Document incident (what, when, action taken)
6. Update security rules to prevent reoccurrence

**If malware is detected:**
1. Quarantine content (remove from system)
2. Alert Dan via Telegram (⚠️ THREAT DETECTED)
3. Review Security Bot rules (why did it slip through?)
4. Retrain bot (update system prompt, examples)
5. Document incident

**If customer data is at risk:**
1. Stop all operations immediately
2. Alert Dan (🚨 CRITICAL ALERT)
3. Review what data was accessed
4. Notify affected customers (if required by law)
5. Comply with Thai PDPA requirements

---

## 9. TOOLS MATRIX (Quick Reference)

| Tool | Purpose | Used by | Access | Frequency |
|------|---------|---------|--------|-----------|
| Meta Business | Social posting, ads, analytics | Content Manager, Paid Ads, Community Manager bots + Dan | API | Daily |
| Google Analytics 4 | Website traffic | Analytics Bot | API | Daily |
| Mailchimp | Email campaigns | Copywriter Bot + Dan | API | Weekly |
| Asana | Project management | Project Manager Bot + Dan | API + Web | Daily |
| Telegram | Alerts, approvals | All bots + Dan | API | 24/7 |
| Looker Studio | KPI dashboard | Dan | Web (public link) | Hourly |
| Google Drive | File storage, docs | All bots + Dan | API + Web | Daily |
| Canva | Graphic design | Visual Designer Bot | API (if available) or manual | Daily |
| DaVinci Resolve | Video editing | Video Editor Bot | Desktop app | Weekly |
| OpenAI API | Content moderation, threat detection | Security Bot | API | 24/7 |

---

## 10. NEXT STEPS FOR DAN

1. **Confirm tools:** Review list, approve or suggest alternatives
2. **Set up credentials:** Provide Meta Business, Google Analytics, Mailchimp access
3. **Configure Telegram:** Create bot, share token with Panda (for integration)
4. **Populate brand assets:** Upload logos, colors, fonts, photos, videos to Google Drive
5. **Review bot prompts:** Panda will draft, Dan approves tone/rules
6. **Approve security checklist:** Review SECURITY_CHECKLIST.md, add custom rules
7. **Plan Week 1 kickoff:** Schedule infrastructure setup, credential verification

---

**Ready to lock this in?**
