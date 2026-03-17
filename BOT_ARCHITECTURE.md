# Similan Digital Bot Architecture

## Bot Team Overview

10 bots working as a coordinated team. 3 content bots active immediately, others ramping Phase 1–3.

| Bot | Role | Phase 1 (Weeks 1–4) | Phase 2 (Weeks 5–8) | Phase 3 (Weeks 9–12) |
|-----|------|:---:|:---:|:---:|
| **Content Manager** | Social copy, captions, hashtags | ✅ | ✅ | ✅ |
| **Visual Designer** | Graphics, layouts, templates | ✅ | ✅ | ✅ |
| **Paid Ads Bot** | Meta/Google campaigns, budget optimization | ✅ | ✅ | ✅ |
| **Community Manager** | Comments, DMs, engagement | ❌ | ✅ | ✅ |
| **Analytics Bot** | Metrics, reporting, dashboards | ⚠️ Basic | ✅ | ✅ |
| **Copywriter Bot** | Longer-form content, email, ad copy | ❌ | ✅ | ✅ |
| **Video Editor Bot** | Reels, short-form edits, effects | ❌ | ⚠️ Basic | ✅ |
| **Influencer/Outreach Bot** | Partnerships, collaborations | ❌ | ❌ | ✅ |
| **Project Manager Bot** | Workflow orchestration, scheduling | ✅ Basic | ✅ | ✅ |
| **Security & Compliance Bot** | Threat monitoring, content review, audit | ✅ 24/7 | ✅ 24/7 | ✅ 24/7 |

---

## Phase 1: Setup & Credentialing (Weeks 1–4)

### Week 1: Infrastructure & Access
- [ ] Verify/set up FB, Instagram, TikTok business accounts
- [ ] Set up Meta Ads Manager & Google Ads
- [ ] Create brand asset directory structure
- [ ] Set up project management tool (Asana or Monday)
- [ ] Configure Telegram notifications channel
- [ ] Establish secure credential storage (no hardcoding)

### Week 2: Bot Setup & Onboarding
- [ ] Spin up all 10 bots (some in standby mode)
- [ ] Content Manager Bot: Ingest brand guides, past posts, competitor analysis
- [ ] Visual Designer Bot: Ingest brand colors, fonts, templates
- [ ] Paid Ads Bot: Connect to Meta & Google, load historical campaign data
- [ ] Security Bot: Configure threat detection rules, code review standards
- [ ] Project Manager Bot: Set up content calendar, workflow automation

### Week 3: Content Calendar & First Batch
- [ ] Dan + bots co-create 30-day content calendar (3 brands)
- [ ] Content Manager Bot drafts first week of posts
- [ ] Visual Designer Bot creates graphics/templates
- [ ] Copywriter Bot drafts ad copy + email templates
- [ ] Security Bot reviews all outputs
- [ ] Dan approves all content for posting

### Week 4: Launch & Tune
- [ ] Begin posting to live channels (human-posted, Dan approval)
- [ ] Monitor engagement, comments, performance
- [ ] Analytics Bot builds real-time dashboards
- [ ] Iterate based on first 2 weeks of data
- [ ] Refine content calendar for Month 2

---

## Phase 2: Workflow Optimization (Weeks 5–8)

### Week 5–6: Ramp Up Bot Capacity
- [ ] Community Manager Bot goes live (comment/DM monitoring)
- [ ] Copywriter Bot expands (blog, email campaigns, longer-form)
- [ ] Video Editor Bot begins basic short-form edits
- [ ] Influencer Bot starts researching partnerships
- [ ] Security Bot: Weekly threat/compliance digest added to reporting

### Week 7: Content at Scale
- [ ] All 3 brands posting on regular cadence (per content calendar)
- [ ] Community Manager Bot handling customer interactions (Dan monitors)
- [ ] Email marketing campaigns live (Mailchimp/Klaviyo)
- [ ] First paid ad optimization cycle (budget reallocation based on performance)

### Week 8: Decision Point
- [ ] Review first month of metrics
- [ ] Dan decides: Can bots handle more autonomy, or stay in review cycle longer?
- [ ] Prepare Phase 3 ramp-up plan

---

## Phase 3: Bot Autonomy & Scaling (Weeks 9–12)

### Week 9–10: Limited Autonomy Trial
- [ ] Content Manager Bot: Can draft content without Dan pre-approval (Dan reviews async within 24h)
- [ ] Visual Designer Bot: Can iterate on templates (Dan approves final designs)
- [ ] Paid Ads Bot: Can adjust budgets within guardrails (real-time alerts to Dan if threshold exceeded)
- [ ] Community Manager Bot: Can respond to routine comments (escalate brand-sensitive issues to Dan)

### Week 11–12: Review & Stabilize
- [ ] Measure error rate, response time, engagement lift
- [ ] Refine escalation rules (what auto-flags to Dan)
- [ ] Formalize post-12-week operating model
- [ ] Plan Month 4 (likely: full autonomy for some bots, continued review for others)

---

## Bot Interaction Diagram

```
CONTENT CREATION PIPELINE
========================

[Photographer] 
    ↓ (monthly: photos, videos)
[Brand Asset Library]
    ↓
[Content Manager Bot] ← [Copywriter Bot]
    ↓                       ↓
[Visual Designer Bot] ← [Copywriter Bot (ad copy)]
    ↓                       ↓
[SECURITY BOT] ← Review all outputs for malware, creds, compliance
    ↓ (pass/fail)
    ├→ PASS: Queued for approval
    └→ FAIL: Auto-quarantine + Telegram alert to Dan
    ↓
[Dan Approval] (Telegram) ← First 2 months: all posts
                            After Month 3: spot-check mode
    ↓ (approved)
[Project Manager Bot] ← Schedule posting + coordinate timing
    ↓
[Human Posts to FB/Insta/TikTok] (Dan or designated team member)
    ↓
[Community Manager Bot] ← Monitor comments, DMs, engagement
    ↓ (flags/responses)
[Analytics Bot] ← Aggregate metrics, build dashboards
    ↓
[Dan Review] (Weekly digest, Monthly deep-dive)

PAD SPEND MANAGEMENT
====================

[Paid Ads Bot] 
    ↓
[Historical data + KPI targets]
    ↓
[Campaign optimization] (bid strategy, audience, creative rotation)
    ↓
[SECURITY BOT] ← Verify no malicious links, proper tracking
    ↓ (if safe)
[Meta/Google Ads Manager]
    ↓
[Real-time performance monitoring]
    ↓
[Alerts to Dan] (if spend > threshold or engagement drops)

ESCALATION PATHS
================

CUSTOMER INTERACTION
Customer comment/DM on FB, Instagram, GMB
    ↓
[Community Manager Bot] ← Tag as routine or escalation-worthy
    ├→ ROUTINE: Auto-respond (friendly, helpful)
    │   ↓ (Dan reviews later in digest)
    └→ ESCALATION: Telegram alert to Dan immediately
        Examples: Complaint, brand-sensitive, legal question

SECURITY ALERT
Malware, creds, suspicious activity detected
    ↓
[Security Bot] ← 24/7 monitoring
    ├→ Auto-quarantine malicious content
    └→ Telegram alert to Dan (high priority)

METRIC ANOMALY
Engagement drops >20% or unexplained spike
    ↓
[Analytics Bot] ← Real-time monitoring
    ↓
[Telegram alert to Dan] ← Investigate trend
```

---

## Approval Workflow (Months 1–2)

**Every piece of content goes through this gate:**

```
[Bot generates content]
        ↓
[Security Bot reviews]
        ├→ FLAGGED: Quarantine + alert Dan
        └→ PASS: Send to Dan for approval
        ↓
[Dan reviews via Telegram]
(target: <24h turnaround)
        ├→ APPROVED: Queue for posting
        ├→ REVISE: Return to bot with feedback
        └→ REJECTED: Pull and rework
        ↓
[Project Manager Bot schedules posting]
        ↓
[Dan/human posts to channel]
        ↓
[Monitoring begins]
```

**Timeline:** 3–7 days from concept to live (depending on approval cycles)

---

## Post-Month 3 Approval Model (Proposed)

**Spot-check instead of full review:**

- **Content Manager Bot:** Can post content types 1–3x/week autonomously (Dan reviews sample weekly)
- **Visual Designer Bot:** Can create variations autonomously (Dan approves originals, bot remixes)
- **Paid Ads Bot:** Can adjust budgets/bids within guardrails (auto-alerts if >±20% adjustment)
- **Community Manager Bot:** Auto-responds to routine comments, escalates brand-sensitive issues
- **Copywriter Bot:** Drafts email campaigns (Dan approves template, bot generates variations)

**Still requires Dan approval:**
- Major campaign pivots
- Budget increases >10%
- Brand messaging changes
- Sensitive customer issues
- Crisis management

---

## Tool Stack (Recommended)

### Project Management
- **Tool:** Asana (agile-friendly, kanban boards, timeline view)
- **Why:** Visual workflow, dependency tracking, team collaboration
- **Setup:** Separate board per brand + cross-brand view
- **Automations:** Content calendar sync, approval gates, Telegram notifications

### Email Marketing
- **Tool:** Mailchimp (free tier sufficient to start)
- **Alternative:** Klaviyo (better for e-commerce/segmentation if needed later)
- **Setup:** 3 lists (Lucky 13, Vegan Table, RGD) + shared brand assets
- **Automation:** Newsletter schedule, promotional sequences, engagement tracking

### Analytics
- **Tool:** Google Analytics 4 (free, integrates Meta/TikTok)
- **Dashboard:** Custom Looker Studio dashboard (built by Analytics Bot)
- **Metrics tracked:** Footfall proxy (web traffic), online orders, email engagement, social growth
- **Reporting:** Real-time access + weekly/monthly digests

### Social Media Management
- **Primary:** Manual posting (Dan or team) via native apps (preserve algorithm benefit)
- **Monitoring:** Meta Business Suite + TweetDeck-style dashboard (custom)
- **Content repository:** Google Drive (organized by brand, asset type)

### Security & Code Review
- **Threat detection:** YARA rules + OpenAI content moderation API
- **Credential scanning:** git-secrets + truffleHog patterns
- **Code review:** Semgrep (SAST) + bandit (Python safety)
- **Compliance audit:** Custom checklist (PDPA, OpenClaw spec, OWASP)

### Communication
- **Primary:** Telegram (Dan's preference)
- **Channel structure:**
  - #alerts (security, customer issues, metric anomalies)
  - #daily-digest (summary of activity)
  - #approvals (content awaiting Dan review)

---

## Content Calendar Structure

**3 brands × channel-specific cadence:**

### Lucky 13 Sandwich
- **Facebook:** 5 posts/week (daily deals, location-specific, stories)
- **Instagram:** 4 posts/week (reels, behind-the-scenes, customer features) + daily stories
- **TikTok:** 2 posts/week (trending, challenges, quick content)
- **Email:** 1 weekly newsletter (specials, new locations, reviews)

### The Vegan Table
- **Facebook:** 4 posts/week (recipes, wellness, partnerships, events)
- **Instagram:** 5 posts/week (dish features, ingredient highlights, community) + daily stories
- **TikTok:** 2 posts/week (vegan hacks, dining experience, trends)
- **Email:** 1 bi-weekly newsletter (new menu, events, guest posts)

### Really Good Deli
- **Facebook:** 3 posts/week (product features, B2B partnerships, local spotlights)
- **Instagram:** 3 posts/week (product photography, recipe ideas, behind-the-scenes)
- **LinkedIn:** 2 posts/week (thought leadership, B2B insights, case studies)
- **Email:** 1 monthly B2B newsletter (new products, partnership opportunities, industry insights)

---

## KPI Dashboard & Reporting

### Real-Time Dashboard (Dan can check anytime)
- **Lucky 13:** Footfall proxy (web traffic), followers, engagement rate, top posts (past 7 days)
- **Vegan Table:** Same + review sentiment (TripAdvisor, HappyCow, Google)
- **Really Good Deli:** Pipeline opportunities (prospects contacted), email engagement, partnership leads

### Weekly Digest (Every Monday, Telegram)
- Top 3 posts per brand (engagement, reach, shares)
- Community highlights (notable comments, questions, brand mentions)
- Ad performance snapshot (spend, impressions, conversions, ROAS)
- Security report (threats detected, compliance status)
- Pending approvals (content awaiting Dan)

### Monthly Deep-Dive (First Monday of month, shared doc)
- 30-day performance summary
  - Follower growth trend
  - Engagement rate trend
  - Top-performing content categories
  - Audience demographics shift
- Ad spend analysis
  - ROI per channel
  - Audience segment performance
  - Creative fatigue assessment
  - Budget reallocation recommendation
- Competitor benchmarking
  - Prime Burger vs Lucky 13
  - Manston/Sloanes/Smokey Mountain vs RGD
  - Engagement/follower velocity comparison
- Recommendations for next 30 days

---

## Security & Compliance Checklist

**Security Bot runs these checks on all outputs:**

- [ ] No API keys, passwords, tokens, credentials in any output
- [ ] No malware signatures detected (YARA scan)
- [ ] No suspicious/malicious links
- [ ] No copyright/IP infringement in generated images
- [ ] No political content (Thai sensitivities)
- [ ] No crude/offensive language
- [ ] No false health/legal claims (especially food/wellness)
- [ ] No royal figure references (Thai law)
- [ ] No alcohol advertising violations (Thai law)
- [ ] All .md & skill files follow OpenClaw spec
- [ ] No hardcoded secrets in code
- [ ] Safe functions (no arbitrary exec, proper input validation)
- [ ] PDPA compliance (no personal data exposure)

**Weekly Security Report includes:**
- Threats detected & remediated
- Failed content (quarantined)
- Compliance violations found & fixed
- Recommendations for bot behavior tuning

---

## Team Communication & Escalation

### Dan's Primary Interface: Telegram

**Chat structure:**

```
@SimilanSecurityAlerts
├─ Malware/credential detected → URGENT
├─ Customer complaint/review → HIGH
├─ Metric anomaly (20%+ drop) → MEDIUM
└─ General info → LOW

@SimilanDailyDigest
├─ Daily summary (morning Bangkok time)
├─ Pending approvals
└─ Top posts from last 24h

@SimilanApprovals
├─ Content awaiting Dan review
├─ One message per post/asset
└─ Dan reacts (✅ approve, 📝 revise, ❌ reject)
```

### Bots' Internal Communication

**Via Asana:**
- Content Manager Bot → Visual Designer Bot: "Draft copy ready for designs"
- Project Manager Bot → Bots: "Post scheduled for Tuesday 9 AM"
- Analytics Bot → Content Manager Bot: "Post type X underperformed, suggest Y"

**Via Telegram (ops channel, not visible to Dan unless escalated):**
- Security Bot: "Flagged 2 malicious links in batch 4"
- Project Manager Bot: "Content calendar updated, 47 posts queued"

---

## 90-Day Launch Roadmap

### Week 1–2: Foundations
- Infrastructure: accounts, credentials, tools set up
- Bot onboarding: brand knowledge, competitor analysis loaded
- Deliverables: Content calendar Month 1 finalized

### Week 3–4: Go Live (Phase 1 Content)
- Launch: First posts live across all 3 brands
- Cadence: 10–12 posts/week per brand (per current scope)
- Dan review: 100% approval gate
- Deliverables: First week of live content, initial engagement data

### Week 5–8: Optimization & Ramp (Phase 2 Expansion)
- Capacity: Community Manager Bot live, more bots ramped
- Quality: Measure engagement, refine messaging, A/B test creative
- Expansion: Email campaigns, TikTok ramp, influencer research begins
- Deliverables: Monthly performance report, competitor analysis, campaign recommendations

### Week 9–12: Autonomy Trial & Stabilization (Phase 3)
- Autonomy: Limited bot posting without pre-approval (Dan spot-checks)
- Scale: Full content calendar execution, paid ads optimization at scale
- Integration: All bots humming, minimal manual work from bots
- Deliverables: Post-12-week operating model, 6-month forecast

### Month 4 Onward: Steady State & Growth
- Autonomy: Most bots posting autonomously (Dan approves exceptions)
- Focus: Data-driven optimization, experimentation (20% budget), new channel testing
- Planning: Pitch 4th client (post 6-month proof point)

---

## Success Metrics (90-Day Checkpoint)

**By end of Week 12, these should be in place:**

✅ All 10 bots operational (at least in standby mode)  
✅ Daily content posting on schedule (no delays >1 day)  
✅ 50+ posts live across 3 brands  
✅ Analytics dashboard tracking 10+ KPIs per brand  
✅ Zero security/compliance incidents  
✅ Dan approval time: <24h average  
✅ Community Manager Bot: Handling 80% of routine comments  
✅ Paid ads: Optimized for ROAS, not just impressions  
✅ Email subscribers: Growing (baseline → +15%)  
✅ Content ideas → live: 5–7 day turnaround  

**90-day win (from discovery):**
> "You guys all set up, channels working well, bots posting to a content calendar schedule — increased brand awareness as measured by proxy of followers etc."

✅ Achieved if:
- Follower growth: +20–30% per brand
- Engagement rate: +15% vs baseline
- Website traffic: +10% (if tracked)
- Email list: +15%
- No major content failures or brand damage

---

## Risks & Mitigations

| Risk | Mitigation |
|------|-----------|
| Dan bottleneck (slow approvals) | Telegram workflow, 24h SLA, escalation rules |
| Bot goes rogue (posts malicious content) | Security Bot gates everything, 24/7 monitoring |
| Credential leak (Meta, Google creds exposed) | No hardcoding, secure environment variables, bot audit trail |
| Thai law violations (alcohol, royal refs) | Security Bot checklist, legal review of copy templates |
| Low engagement (bots don't understand brand voice) | Copywriter Bot + Visual Designer Bot iterate on feedback, weekly reviews |
| Competitor copies strategy | Original content, proprietary audience insights, regular strategy reviews |
| Tools fail or aren't set up by week 2 | Backup manual process (Google Sheets, email approvals) ready to go |

---

## Next Steps

**For Panda (me):**
1. Build brand asset directory structure (ready for Dan to populate)
2. Audit competitors (Prime Burger, Bartels, Manston, Sloanes, Smokey Mountain)
3. Create Asana template (board structure, automation, views)
4. Propose Telegram workflow (exact channel names, message templates, reaction rules)
5. Design KPI dashboard (Looker Studio mockup)
6. Finalize tool recommendations (email platform, analytics stack)

**For Dan:**
1. Provide brand guides (.pdf, .psd, or links)
2. Provide initial photo/video library (per brand)
3. Confirm Meta Ads Manager & Google Ads access
4. Review bot architecture — any changes?
5. Confirm Telegram as primary comms channel
6. Approve Asana + tool stack selections

**Kick-off meeting:** Review this architecture doc, confirm decisions, set Week 1 start date.

---

**Questions? Concerns? Anything you want to change before we lock this in and start building?**
