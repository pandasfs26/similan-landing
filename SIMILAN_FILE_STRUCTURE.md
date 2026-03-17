# Similan Digital: File Structure & Organization

## Root Directory Structure

```
/Users/pandamac/.openclaw/workspace/
├── SIMILAN_AGENCY_SETUP/              # Agency operations hub
│   ├── AGENCY_BRIEF.md                # Copy of final discovery questionnaire
│   ├── BOT_ARCHITECTURE.md            # 10-bot system design (THIS FILE'S SOURCE)
│   ├── WAYS_OF_WORKING.md             # Operational procedures, tools, APIs
│   ├── TOOLS_INVENTORY.md             # Every tool, API key location, access pattern
│   │
│   ├── CLIENTS/                       # Per-client operational data
│   │   ├── lucky-13-sandwich/
│   │   │   ├── CLIENT_BRIEF.md        # Client overview, goals, KPIs
│   │   │   ├── BRAND_ASSETS/
│   │   │   │   ├── logos/
│   │   │   │   ├── colors_fonts.md    # Brand colors, hex codes, fonts
│   │   │   │   ├── photos/            # Monthly photo library from photographer
│   │   │   │   ├── videos/            # Monthly video library
│   │   │   │   └── guidelines.pdf     # Brand guidelines (when Dan provides)
│   │   │   ├── CONTENT_CALENDAR.md    # Living doc: month's content plan
│   │   │   ├── CAMPAIGN_BRIEFS/       # Individual campaign docs
│   │   │   │   ├── summer_campaign.md
│   │   │   │   └── grand_opening_l14.md
│   │   │   ├── APPROVED_POSTS/        # Archive of live posts (post-mortem analysis)
│   │   │   │   ├── 2026-03-week1.md
│   │   │   │   └── 2026-03-week2.md
│   │   │   ├── PERFORMANCE_DATA/      # Weekly snapshots for analytics
│   │   │   │   ├── 2026-03-14.json    # Engagement, followers, reach
│   │   │   │   └── 2026-03-21.json
│   │   │   └── ESCALATIONS/           # Customer complaints, brand issues
│   │   │       ├── 2026-03-14_negative_review.md
│   │   │       └── resolved.md
│   │   │
│   │   ├── the-vegan-table/           # (Same structure as above)
│   │   │   ├── CLIENT_BRIEF.md
│   │   │   ├── BRAND_ASSETS/
│   │   │   ├── CONTENT_CALENDAR.md
│   │   │   └── ... (same as Lucky 13)
│   │   │
│   │   └── really-good-deli/          # (Same structure as above)
│   │       ├── CLIENT_BRIEF.md
│   │       ├── BRAND_ASSETS/
│   │       ├── CONTENT_CALENDAR.md
│   │       └── ... (same as Lucky 13)
│   │
│   ├── SIMILAN_DIGITAL/               # Agency's own brand
│   │   ├── BRAND_ASSETS/
│   │   │   ├── logos/
│   │   │   ├── colors_fonts.md
│   │   │   └── guidelines.pdf
│   │   ├── CONTENT_CALENDAR.md        # Blog posts, case studies, agency content
│   │   ├── WEBSITE/
│   │   │   ├── index.html
│   │   │   ├── services.html
│   │   │   ├── case_studies.html
│   │   │   └── assets/
│   │   └── SOCIAL/
│   │       ├── instagram_content.md
│   │       ├── linkedin_content.md
│   │       └── tiktok_content.md
│   │
│   ├── BOTS/                          # Bot configurations & prompts
│   │   ├── content-manager/
│   │   │   ├── SYSTEM_PROMPT.md       # Bot's role, tone, guidelines
│   │   │   ├── TEMPLATES.md           # Post templates, format examples
│   │   │   └── RULES.md               # What to write, what not to write
│   │   ├── visual-designer/
│   │   ├── paid-ads-bot/
│   │   ├── community-manager/
│   │   ├── analytics-bot/
│   │   ├── copywriter/
│   │   ├── video-editor/
│   │   ├── influencer-outreach/
│   │   ├── project-manager/
│   │   └── security-compliance/
│   │       ├── SYSTEM_PROMPT.md
│   │       ├── SECURITY_CHECKLIST.md  # 12-point review
│   │       ├── THREAT_RULES.md        # YARA patterns, malware signatures
│   │       └── COMPLIANCE_RULES.md    # Thai PDPA, alcohol, royal refs, etc.
│   │
│   ├── PROCESSES/                     # Standard operating procedures
│   │   ├── APPROVAL_WORKFLOW.md       # Step-by-step approval process
│   │   ├── CONTENT_CALENDAR_PROCESS.md # How to build/update calendar
│   │   ├── CRISIS_MANAGEMENT.md       # How to respond to customer issues
│   │   ├── AD_SPEND_PROCESS.md        # Budget allocation, optimization
│   │   └── REPORTING_PROCESS.md       # How to generate weekly/monthly reports
│   │
│   ├── INTEGRATIONS/                  # API keys, credentials, webhooks
│   │   ├── META_BUSINESS.md           # Meta Ads Manager API, Business Suite
│   │   ├── GOOGLE_ADS.md              # Google Ads API (if set up)
│   │   ├── MAILCHIMP.md               # Email API, list management
│   │   ├── ASANA.md                   # Project management API
│   │   ├── GOOGLE_ANALYTICS.md        # GA4 API, event tracking
│   │   ├── TELEGRAM.md                # Bot notifications, message flow
│   │   └── LOOKER_STUDIO.md           # Dashboard creation, data sources
│   │
│   ├── TEMPLATES/                     # Reusable templates
│   │   ├── INSTAGRAM_POST.md          # Template: Instagram feed post
│   │   ├── FACEBOOK_POST.md           # Template: FB post (longer form)
│   │   ├── TIKTOK_POST.md             # Template: TikTok captions
│   │   ├── EMAIL_NEWSLETTER.md        # Template: Email campaign
│   │   ├── AD_COPY.md                 # Template: Meta ad copy (short form)
│   │   ├── BLOG_POST.md               # Template: Website blog post
│   │   └── LINKEDIN_POST.md           # Template: LinkedIn (B2B)
│   │
│   ├── COMPETITOR_RESEARCH/           # Ongoing competitive analysis
│   │   ├── LUCKY_13_COMPETITORS.md    # Prime Burger, Bartels competitive position
│   │   ├── VEGAN_TABLE_COMPETITORS.md # (No direct competitors)
│   │   ├── RGD_COMPETITORS.md         # Manston, Sloanes, Smokey Mountain analysis
│   │   └── SOCIAL_AUDIT.md            # Competitor social benchmarking (weekly update)
│   │
│   ├── REPORTS/                       # Archive of reports
│   │   ├── 2026-03/
│   │   │   ├── WEEK_1_DIGEST.md       # Week 1 performance
│   │   │   ├── WEEK_2_DIGEST.md
│   │   │   ├── MONTHLY_REPORT.md      # Month-end deep-dive
│   │   │   └── SECURITY_REPORT.md     # Monthly security audit
│   │   └── 2026-04/
│   │       └── ...
│   │
│   ├── SKILLS/                        # OpenClaw skills for specialized tasks
│   │   ├── similan-content-analyzer/
│   │   │   ├── SKILL.md               # Skill definition
│   │   │   ├── analyzer.js            # Analyze competitor content, trends
│   │   │   └── references/
│   │   ├── similan-email-marketer/
│   │   │   ├── SKILL.md
│   │   │   ├── emailer.py
│   │   │   └── references/
│   │   └── similan-security-auditor/
│   │       ├── SKILL.md
│   │       ├── auditor.py             # YARA, truffleHog, Semgrep runner
│   │       └── rules/
│   │
│   ├── MEMORY/                        # Session memory files (daily + long-term)
│   │   ├── 2026-03-14.md              # Today's log (what happened, decisions)
│   │   ├── 2026-03-13.md
│   │   └── ... (daily files)
│   │
│   └── ARCHIVES/                      # Old, completed campaigns
│       ├── 2026-02/                   # If launching partway through
│       └── historical/
│
└── BOOTSTRAP_DOCS/                    # (Keep for reference, can delete later)
    ├── AGENCY_DISCOVERY.md
    ├── BOT_ARCHITECTURE.md
    └── This SIMILAN_FILE_STRUCTURE.md
```

---

## Key Directories Explained

### `/CLIENTS/` — Per-Brand Operations

Each brand has identical structure:

```
lucky-13-sandwich/
├── CLIENT_BRIEF.md
│   Owner: Dan
│   Updated: Monthly or when goals change
│   Content: Summary of brand, KPIs, target audience, pain points
│
├── BRAND_ASSETS/
│   Owner: Dan (populates), Visual Designer Bot (references)
│   ├── logos/
│   │   ├── l13_logo_horizontal.png
│   │   ├── l13_logo_square.png
│   │   └── usage_guide.md
│   ├── colors_fonts.md
│   │   Primary: #FF6B35 (orange), #2C3E50 (dark)
│   │   Fonts: Open Sans (headings), Lato (body)
│   ├── photos/                        # From photographer, monthly
│   │   ├── 2026-03/
│   │   │   ├── sandwich_hero_01.jpg
│   │   │   ├── location_branch1.jpg
│   │   │   └── ...
│   │   └── 2026-04/
│   ├── videos/
│   │   ├── 2026-03/
│   │   │   ├── branch1_timelapse.mp4
│   │   │   └── customer_testimonial.mp4
│   │   └── 2026-04/
│   └── guidelines.pdf
│       (When Dan provides formal brand guide)
│
├── CONTENT_CALENDAR.md                # LIVING DOCUMENT
│   Owner: Content Manager Bot + Project Manager Bot
│   Updated: Weekly
│   Format: 30-day calendar, channel breakdown, post copy, visual assignments
│   Example:
│     # Lucky 13 Sandwich — March 2026 Content Calendar
│     
│     ## Week 1 (Mar 14–20)
│     ### Monday, Mar 14 (POSTED)
│     - Platform: Instagram
│     - Type: Carousel (5 slides)
│     - Copy: "Introducing our new Italian Sub—made with..." [X chars]
│     - Visual: 5 product photos from Feb library
│     - Hashtags: #lucky13phuket #sandwich #local
│     - Posted by: Dan
│     - Status: ✅ LIVE
│     - Engagement: 47 likes, 8 comments, 2 shares
│
├── CAMPAIGN_BRIEFS/
│   Owner: Copywriter Bot, Content Manager Bot
│   Example: summer_campaign.md
│     # Lucky 13 Summer Campaign (May–Aug)
│     ## Goal: Drive dine-in traffic during low season
│     ## Messaging: "Beat the heat with our fresh, cold sandwiches"
│     ## Timeline: 16 weeks
│     ## Budget: THB 50,000 + USD 200/month ads
│     ## Creative assets needed: 12 hero images, 4 videos
│     ## KPI: +25% dine-in traffic vs baseline
│
├── APPROVED_POSTS/
│   Owner: Dan (creates by archiving), Content Manager Bot (references)
│   Purpose: Post-mortem analysis (what worked, why)
│   Updated: Weekly
│   Example: 2026-03-week1.md
│     # Lucky 13 — Week 1 Posts (Mar 14–20)
│     
│     ## Post 1: Italian Sub Launch
│     - Platform: Instagram
│     - Copy: [Full copy used]
│     - Visuals: [Asset list]
│     - Performance: 47 likes, 8 comments, 2 shares, 340 impressions
│     - Lessons: Product-focused posts get 3x engagement vs lifestyle
│     - Feedback from Dan: "Love the close-up shot. Use more macro photography."
│
├── PERFORMANCE_DATA/
│   Owner: Analytics Bot
│   Updated: Daily (auto-exported from Meta/GA4)
│   Format: JSON snapshot
│   Example: 2026-03-14.json
│     {
│       "date": "2026-03-14",
│       "platform": "instagram",
│       "followers": 1240,
│       "new_followers": 12,
│       "engagement_rate": 0.038,
│       "reach": 340,
│       "website_clicks": 14,
│       "top_post": {
│         "caption": "Italian Sub Launch",
│         "likes": 47,
│         "comments": 8,
│         "shares": 2
│       }
│     }
│
└── ESCALATIONS/
    Owner: Community Manager Bot (flags), Dan (handles)
    Purpose: Record of issues, resolution, prevention
    Example: 2026-03-14_negative_review.md
      # Escalation: Negative Google Review
      Date: 2026-03-14 14:22 UTC+7
      Platform: Google My Business (Branch 2)
      Issue: "Waited 30 mins, sandwich was cold"
      Severity: MEDIUM (1 review, no viral trend)
      Response sent by: Dan
      Resolution: Offered replacement + 20% discount voucher
      Status: ✅ RESOLVED (customer replied: "Thank you, appreciate it")
      Prevention: Reminder sent to Branch 2 manager re: quality checks
```

### `/SIMILAN_DIGITAL/` — Agency's Own Brand

Same structure as client brands, but Similan-focused:

```
SIMILAN_DIGITAL/
├── BRAND_ASSETS/
│   ├── logos/ (Similan logo, approved by Dan)
│   ├── colors_fonts.md
│   └── guidelines.pdf
├── CONTENT_CALENDAR.md (Agency's own posts, case studies, thought leadership)
├── WEBSITE/
│   ├── index.html (Landing page)
│   ├── services.html (What Similan offers)
│   ├── case_studies.html (Client wins, benchmarked)
│   └── assets/ (CSS, JS, images)
└── SOCIAL/
    ├── instagram_content.md (Behind-the-scenes, team, process)
    ├── linkedin_content.md (Thought leadership, industry insights)
    └── tiktok_content.md (Trends, quick tips, viral opportunities)
```

### `/BOTS/` — Bot Configurations

Each bot has a working directory with system prompt, templates, rules:

```
content-manager/
├── SYSTEM_PROMPT.md
│   You are the Content Manager for Similan Digital.
│   Your job: Create engaging, on-brand social media posts.
│   Tone: [Brand-specific: fun, casual, authentic, etc.]
│   Constraints:
│   - No politics
│   - No crude language
│   - Max 280 chars for Twitter-style, adapt for Instagram/TikTok
│   - Always include 3–5 relevant hashtags
│   - Reference brand assets before creating
│
├── TEMPLATES.md
│   ## Instagram Post (Feed)
│   ---
│   Copy (150–300 chars):
│   [Hook] [Benefit] [CTA]
│   
│   Example:
│   "Ever tried a sandwich so good it changed your mind? 🥪
│   Lucky 13's new Italian Sub is here, made fresh daily.
│   Grab yours today at [location] or order on Grab! 🚚"
│   
│   Visual: 1 high-quality product photo (1080×1080px)
│   Hashtags: 5–10 relevant (brand, location, category)
│   
│   ## Instagram Reel (Video)
│   ---
│   Duration: 15–30s
│   Format: Hook (0–3s) + Payoff (3–20s) + CTA (20–30s)
│   [Similar detailed template]
│
└── RULES.md
    DO:
    - Tag location handles when relevant
    - Respond to trending sounds/challenges on TikTok
    - Use local influencer partnerships when available
    - Post 5–7 times per week (per content calendar)
    
    DON'T:
    - Post alcohol content for Lucky 13 (Thai law)
    - Promote unsustainable claims for Vegan Table
    - Tag competitors negatively
    - Post unvetted user-generated content
```

### `/PROCESSES/` — Standard Operating Procedures

```
APPROVAL_WORKFLOW.md
├── Step 1: Content Manager Bot drafts 5 posts for upcoming week
├── Step 2: Visual Designer Bot creates graphics/assigns photo library assets
├── Step 3: Security Bot scans all outputs (malware, creds, compliance)
├── Step 4: [If flagged] Auto-quarantine + Telegram alert to Dan
├── Step 5: [If pass] Send to Dan via Telegram approval channel
├── Step 6: Dan reviews (target: <24h) → approve/revise/reject
├── Step 7: Project Manager Bot schedules approved content
├── Step 8: Dan/human posts to live channel
├── Step 9: Monitoring begins (Community Manager Bot, Analytics Bot)
├── Step 10: Weekly archive (Approved Posts, performance data logged)

CONTENT_CALENDAR_PROCESS.md
├── When: Build on last Friday of previous month
├── Owner: Content Manager Bot + Dan
├── Steps:
│   1. Review previous month's top 5 posts (what worked)
│   2. Check brand calendar (seasonality, events, launches)
│   3. Identify themes for upcoming month
│   4. Draft 30-day calendar (4 weeks, channel-specific)
│   5. Get Dan's feedback (Friday EOD)
│   6. Finalize Monday (ready for Week 1 posting)
└── Output: CONTENT_CALENDAR.md, shared with all bots

CRISIS_MANAGEMENT.md
├── Trigger: Negative review, viral complaint, brand-damaging comment
├── Response time: <1 hour (Community Manager Bot flags, Dan handles)
├── Steps:
│   1. Acknowledge publicly (empathetic, brief)
│   2. Take offline (DM, email, phone if needed)
│   3. Solve root cause (refund, replacement, apology)
│   4. Follow up (close loop publicly)
│   5. Document (Escalations folder)
│   6. Prevent (share lesson with team, adjust processes)

AD_SPEND_PROCESS.md
├── Budget: THB 60,000/month for all services + separate USD ad spend
├── Allocation:
│   - Lucky 13: USD 500/month (or as optimized)
│   - Vegan Table: USD 100/month
│   - Really Good Deli: USD 100/month
│   - Testing budget: 20% for new channels/tactics
├── Optimization cycle: Weekly (Paid Ads Bot analyzes, proposes adjustments)
├── Guardrails:
│   - No more than ±20% weekly adjustment without Dan approval
│   - ROAS must be positive (no wasteful spend)
│   - A/B test new audiences/creative (measure impact)
└── Reporting: Real-time dashboard + weekly digest

REPORTING_PROCESS.md
├── Real-time: Analytics Bot updates dashboard hourly
├── Weekly digest: Every Monday 9 AM Bangkok time
│   - Top 3 posts per brand (engagement, reach)
│   - Community highlights (questions, brand mentions)
│   - Ad spend summary (ROI, CPA, ROAS)
│   - Security report (threats detected, compliance)
│   - Pending approvals
├── Monthly deep-dive: First Monday of month
│   - 30-day performance summary
│   - Trend analysis (follower growth, engagement rate trajectory)
│   - Competitor benchmarking
│   - Recommendations for next month
└── Dashboard: Real-time access (Looker Studio), no login required for Dan
```

### `/INTEGRATIONS/` — API & Credential Tracking

```
META_BUSINESS.md
├── Account: Similan Digital (Dan's account)
├── Clients configured:
│   - Lucky 13 Sandwich (FB page, Instagram biz account)
│   - The Vegan Table (FB page, Instagram biz account)
│   - Really Good Deli (FB page, Instagram biz account)
├── APIs used:
│   - Business Account API (read followers, engagement, audience)
│   - Ads Manager API (create/manage campaigns, optimize budgets)
│   - Graph API (post content, manage comments)
├── Credentials: Stored in .env file (NEVER in code)
│   META_ACCESS_TOKEN=eaa123456...
│   META_BUSINESS_ACCOUNT_ID=12345...
├── Rate limits:
│   - 200 API calls per day (Business tier)
│   - Batch requests to avoid throttling
│   - Exponential backoff on 429 errors
├── Integration: Ads Bot connects daily, Analytics Bot pulls metrics
└── Security: Token rotated quarterly, IP whitelisting enabled

GOOGLE_ADS.md
├── Status: NOT YET SET UP (see E3 of discovery brief)
├── Plan: Set up when/if Google Ads needed (search ads, display ads)
├── Credentials: TBD
├── Rate limits: TBD
└── Integration point: Ads Bot (when enabled)

MAILCHIMP.md
├── Account: Similan Digital (Dan's account)
├── Audiences:
│   - Lucky 13 Sandwich (mailing list, ~500 subscribers)
│   - The Vegan Table (mailing list, ~300 subscribers)
│   - Really Good Deli (mailing list, ~200 subscribers, B2B)
├── APIs used:
│   - Marketing API (send campaigns, manage lists, track engagement)
│   - Subscriber Sync (import/export via CSV)
├── Credentials: API key in .env
│   MAILCHIMP_API_KEY=abc123...
│   MAILCHIMP_SERVER_PREFIX=us1
├── Rate limits:
│   - 10 requests per second
│   - Batch operations for bulk actions
├── Integration: Copywriter Bot drafts, Project Manager Bot schedules
└── Security: API key rotated every 6 months

ASANA.md
├── Account: Similan Digital (Dan is owner)
├── Projects:
│   - Lucky 13 Sandwich (content calendar, campaigns, tasks)
│   - The Vegan Table (same)
│   - Really Good Deli (same)
│   - Cross-client (strategy, competitor research, reports)
├── APIs used:
│   - REST API (create tasks, manage timelines, update status)
│   - Webhooks (trigger automations on task change)
├── Credentials: OAuth token in .env
│   ASANA_AUTH_TOKEN=1/xyz...
├── Automation:
│   - Task created → Notify bots via Telegram
│   - Task completed → Log in APPROVED_POSTS
│   - Due date passed → Escalate to Dan
├── Integration: Project Manager Bot syncs daily
└── Security: OAuth token auto-refreshes

GOOGLE_ANALYTICS.md
├── Property: Similan Digital (main domain)
├── Sub-properties: One per client (if they have websites)
│   - lucky13sandwich.com
│   - thevegantablephuket.com
│   - reallygoodfoodgroup.com
├── APIs used:
│   - Google Analytics Data API v1 (query events, sessions, conversions)
├── Credentials: Service account (JSON key) in .env
│   GOOGLE_APPLICATION_CREDENTIALS=/path/to/key.json
├── Events tracked:
│   - Page views
│   - Scroll depth
│   - Button clicks (e.g., "Order on Grab")
│   - Email signups
│   - Form submissions
├── Integration: Analytics Bot pulls daily, builds Looker Studio dashboard
└── Security: Service account restricted to read-only access

TELEGRAM.md
├── Bot: Similan Digital Bot (created by Dan)
├── Bot token: In .env (NEVER share)
│   TELEGRAM_BOT_TOKEN=123456789:ABCdef...
├── Channels:
│   - @SimilanSecurityAlerts (high-priority security/customer issues)
│   - @SimilanDailyDigest (morning summary)
│   - @SimilanApprovals (content awaiting Dan review)
├── Workflow:
│   - Security Bot → Alerts channel (malware, creds leaked)
│   - Community Manager Bot → Alerts channel (customer complaint)
│   - Analytics Bot → Digest channel (morning stats)
│   - Content Manager Bot → Approvals channel (post awaiting Dan)
├── Integration: All bots send Telegram messages via API
├── Rate limits:
│   - 30 messages per second per bot
│   - Batch non-urgent updates (combine into one message)
└── Security: Token rotated if ever exposed, no logging of sensitive messages

LOOKER_STUDIO.md
├── Dashboard: Similan Digital — KPI Dashboard (public link, no login)
├── Data sources:
│   - Google Analytics (website traffic)
│   - Meta Business API (followers, engagement)
│   - Mailchimp (email metrics)
│   - Custom JSON (pulled by Analytics Bot, stored in Google Drive)
├── Visualizations:
│   - Lucky 13: Followers trend, engagement rate, top posts, website traffic
│   - Vegan Table: Same
│   - Really Good Deli: Followers, email engagement, B2B pipeline (custom)
├── Refresh rate: Hourly (Analytics Bot pushes updates)
├── Access: Dan gets a public link, can view anytime, no credentials needed
└── Customization: Analytics Bot updates based on weekly KPI changes
```

### `/TEMPLATES/` — Reusable Content Templates

```
INSTAGRAM_POST.md
├── Headline: [Hook or question, 3–10 words]
├── Body: [Main message, 100–200 words, conversational]
├── Call to action: [What you want them to do: visit, order, tag a friend]
├── Hashtags: [5–10 relevant, researched for reach]
├── Visual requirements:
│   - Size: 1080×1080px (or vertical 1080×1350px for feed)
│   - Format: JPEG or PNG
│   - Color palette: Brand colors (from guidelines)
│   - Text overlay: Optional (max 20% of image)
├── Example:
│   ---
│   Heading: "Craving something fresh?"
│   Body: "Our Italian Sub is made daily with imported ingredients and love.
│   Come by any of our 5 locations or order on Grab. Fresh, fast, delicious."
│   CTA: "Tap the link in bio to order now! 🥪"
│   Hashtags: #lucky13phuket #sandwich #fresh #phuket #foodie
│   Visual: High-quality product photo of Italian Sub, top-down, good lighting
└── Variations: Carousel (5 slides), Reel (video), Story (vertical)

EMAIL_NEWSLETTER.md
├── Subject line: [Curiosity or benefit, <50 chars]
├── From: [Brand name, consistent]
├── Preheader: [Preview text, <100 chars]
├── Header: [Logo + brand image]
├── Body:
│   - Section 1: Feature (new product, event, update)
│   - Section 2: Secondary content (tips, behind-the-scenes, customer story)
│   - Section 3: CTA (shop, visit, learn more)
│   - Footer: Address, unsubscribe, social links
├── Design:
│   - Single column (mobile-friendly)
│   - Brand colors & fonts
│   - 1–2 hero images max
│   - Clear button CTAs
├── Example:
│   ---
│   Subject: "New! Try our Italian Sub today 🇮🇹"
│   Preheader: "Fresh, made daily, only at Lucky 13"
│   [Header with Lucky 13 logo]
│   "Hi [Name],
│   We just launched something special.
│   Our new Italian Sub features imported salami, fresh mozzarella, and a secret sauce.
│   Come try it at any location or order on Grab.
│   [CTA Button: Order Now]
│   [Testimonial: "Hands down the best sub in Phuket!" — Alex K.]
│   [Footer with address, unsubscribe, Instagram/Facebook links]"
└── Frequency: Weekly for Lucky 13 & Vegan Table, bi-weekly for RGD (B2B)
```

---

## File Naming Conventions

```
Content Calendar: CONTENT_CALENDAR_YYYY-MM.md (e.g., CONTENT_CALENDAR_2026-03.md)
Weekly Digest: WEEK_N_DIGEST_YYYY-MM-DD.md (e.g., WEEK_1_DIGEST_2026-03-14.md)
Performance Data: YYYY-MM-DD.json (e.g., 2026-03-14.json)
Campaigns: campaign_name_YYYY-MM.md (e.g., summer_campaign_2026-05.md)
Posts Archive: YYYY-MM-week-N.md (e.g., 2026-03-week-1.md)
Skills: skill-name/SKILL.md (e.g., similan-content-analyzer/SKILL.md)
```

---

## Permissions & Access

```
┌─────────────────────┬──────────────────┬─────────────────┬──────────────┐
│ File/Folder         │ Dan (Owner)      │ Bots (Read)     │ Bots (Write) │
├─────────────────────┼──────────────────┼─────────────────┼──────────────┤
│ BRAND_ASSETS        │ Update monthly   │ Reference only  │ ❌           │
│ CONTENT_CALENDAR    │ Review & approve │ ✅ Read         │ ✅ Append    │
│ APPROVED_POSTS      │ Archive posts    │ Reference       │ ❌           │
│ PERFORMANCE_DATA    │ Review/analyze   │ ✅ Read         │ ✅ Write     │
│ ESCALATIONS         │ Handle           │ ✅ Read/flag    │ ✅ Write     │
│ BOTS/prompts        │ Tune & refine    │ ✅ Read         │ ❌           │
│ INTEGRATIONS        │ Secure storage   │ ✅ Read (env)   │ ❌           │
│ PROCESSES           │ Update as needed │ ✅ Read         │ ❌           │
│ MEMORY              │ Daily log        │ Context only    │ Update own   │
└─────────────────────┴──────────────────┴─────────────────┴──────────────┘
```

---

## Backup & Security

- **Credentials:** Stored in `.env` file (never in git, never in markdown)
- **Sensitive files:** Encrypted at rest (OS-level if possible)
- **Version control:** Use git with `.gitignore` (exclude .env, API keys)
- **Weekly backup:** Automated snapshot (date-stamped)
- **Archive:** Old campaigns moved to /ARCHIVES after 3 months

---

## Next Steps for Dan

1. **Create initial directory structure** (Panda will provide script)
2. **Populate BRAND_ASSETS/ for each client:**
   - Logos (PNG, transparent bg)
   - Color palette (hex codes)
   - Fonts (links or files)
   - Initial photo/video library
   - Brand guidelines (PDF if available)
3. **Populate SIMILAN_DIGITAL/ brand assets**
4. **Review bot system prompts** (Panda drafts, Dan approves tone/rules)
5. **Approve credential storage & .env setup** (security checklist)

---

**Structure ready to use?**
