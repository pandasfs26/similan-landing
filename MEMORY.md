# MEMORY.md — Panda's Long-Term Memory

---

## SIMILAN DIGITAL AGENCY PROJECT (Current)

**Status:** Foundation locked, build in progress  
**Launch Dates:**
- Vegan Table + Really Good Deli: April 6, 2026
- Lucky 13 Sandwich: May 6, 2026 (one month later)
- Timeframe: 3 weeks from today (March 14 → April 6 launch)

**What's Complete:**
1. ✅ AGENCY_DISCOVERY.md — Full questionnaire (all sections, Dan approved)
2. ✅ BOT_ARCHITECTURE.md — 10-bot system, 3 phases, 90-day roadmap
3. ✅ SIMILAN_FILE_STRUCTURE.md — Directory org, permissions, naming
4. ✅ WAYS_OF_WORKING.md — Tools, APIs, workflows, security, Asana confirmed
5. ✅ VEGAN_TABLE_LAUNCH_PLAN.md — 4-week content strategy
6. ✅ RGD_LAUNCH_PLAN.md — 4-week B2B/B2C content strategy
7. ✅ LUCKY_13_LAUNCH_PLAN.md — 4-week multi-location content strategy
8. ✅ BOT_SYSTEM_PROMPTS_ALL.md — 10 bot prompts (Content Manager, Visual Designer, Paid Ads, Community Manager, Analytics, Copywriter, Video Editor, Influencer, Project Manager, Security)
9. ✅ COMPETITOR_AUDIT.md — 5 competitors analyzed, positioning gaps identified

**In Progress:**
- Detailed 12-week content calendars (per brand, week-by-week)
- Email templates (18 total, 6 per brand)
- Ad copy variations (45 total)
- KPI dashboard mockup (Looker Studio)

**Tools Confirmed:**
- **PM Tool:** Asana (agile-friendly, confirmed)
- **Email Platform:** Deferred to April 1 (Mailchimp vs Klaviyo decision)
- **Comms Channel:** Webchat (for Panda ↔ Dan), Telegram (for bots → Dan alerts)

**Key Brand Details:**
- **Lucky 13:** 5 franchise locations, focus on dine-in footfall increase
- **Vegan Table:** 10+ year history, award-winning, positioning refresh
- **Really Good Deli:** B2B dominant (55% of sales from 4/5-star hotels), dual B2B/B2C strategy

---

## INFRASTRUCTURE & INTEGRATION

### Channels Configured
**Telegram:**
- ✅ Enabled (groupPolicy: "open")
- Bots will send alerts to Dan via Telegram
- Dan ↔ Panda via webchat (this interface)

**Discord:**
- ✅ Enabled (groupPolicy: "open")
- Guild ID: 1481918556789674126
- User ID: 1481875278119567471
- Channel: 1481926970286542990 (general, allow: true)
- Ready for additional channels (code tasks, research, automations)

**Model:** Switched from Haiku 4.5 to Opus (3.5 Sonnet) for better strategic output

---

## NEXT STEPS (PRIORITY ORDER)

**By EOD today:**
1. Build detailed content calendars (12 weeks × 3 brands)
2. Create email templates (18 total)
3. Generate ad copy variations (45 total)
4. Design KPI dashboard mockup

**Before March 27 (1 week before launch):**
1. Dan provides brand assets (photos, videos, brand guides)
2. Dan provides/confirms product details (menu, locations, hours, sourcing)
3. Dan approves all Week 1 content
4. Credential verification (Meta, GA4, email lists ready)

**April 1:**
- Decision: Mailchimp vs Klaviyo for email platform
- Review first month metrics
- Plan April strategy

**April 6 - May 3:**
- Launch Vegan Table + RGD
- Monitor metrics daily
- Weekly optimization

**May 6 onwards:**
- Launch Lucky 13
- Sustained operations across 3 brands

---

## COMPETITIVE POSITIONING (KEY DIFFERENTIATORS)

**Lucky 13 vs PRIME Burger & Bartels:**
- Beat on: Community engagement, storytelling, frequency (4–5x/week vs 2–3x/week), fun tone, local pride
- Positioning: "Fresh sandwiches made by your neighbors" (vs premium/trendy)

**Vegan Table (no direct competitors):**
- Position as: Local authority, thought leader, community hub
- Emphasize: 10-year history, awards, values-driven, wellness community
- Content: Stories + engagement (not just product photos)

**Really Good Deli vs Manston, Sloanes, Smokey Mountain:**
- Beat on: B2B LinkedIn thought leadership (competitors have zero presence), engagement frequency, storytelling, dual B2B/B2C positioning
- Positioning: "10-year hotel supplier + now available to you" (vs transactional/silent)

---

## BOT TEAM (10 BOTS, LOCKED IN)

| Bot | Primary Role | Key Constraints |
|-----|--------------|-----------------|
| Content Manager | Social copy, captions, hashtags | No health claims, respect platform cadence |
| Visual Designer | Graphics, layouts, templates | 3 variations per brief, brand colors |
| Paid Ads Bot | Meta/Google campaigns, optimization | ROAS >1.2:1, budget guardrails, A/B test always |
| Community Manager | Comments, DMs, engagement | <2h response time, escalate immediately |
| Analytics Bot | KPIs, dashboards, reporting | Real-time data, weekly digest, flag anomalies |
| Copywriter Bot | Long-form: emails, blogs, thought leadership | Persuasive, authentic, strategic |
| Video Editor Bot | Short-form Reels, TikToks | 15–30s, hook in 0–3s, trending sounds |
| Influencer/Outreach Bot | Partnerships, collaborations | Phase 3+ only, Dan approval required |
| Project Manager Bot | Workflow orchestration, Asana | Daily status, escalate blockers |
| Security & Compliance Bot | 24/7 threat monitoring, content review | 12-point security checklist, auto-quarantine |

**Approval gates:** Content → Security Bot → Dan → Posting → Monitoring

---

## DAN'S PREFERENCES & DECISION RULES

- **Response time:** <24h for approvals (Telegram via webchat)
- **Escalation triggers:** Customer complaints, security threats, budget overages >20%
- **Autonomy:** First 2 months = Dan reviews all content; Month 3+ = spot-check mode
- **Risk tolerance:** Experimental but locally appropriate (respect Thai culture/norms)
- **Testing budget:** 20% of ad spend for new channels/tactics
- **Timezone:** Asia/Bangkok (GMT+7)
- **Communication:** Daily digest + Telegram alerts for urgent issues
- **Tone preference:** Australian casual, direct, appreciation for humor

---

## FILES & FOLDER STRUCTURE

**Main docs (locked, ready to reference):**
- `/SIMILAN_AGENCY_SETUP/AGENCY_DISCOVERY.md`
- `/SIMILAN_AGENCY_SETUP/BOT_ARCHITECTURE.md`
- `/SIMILAN_AGENCY_SETUP/SIMILAN_FILE_STRUCTURE.md`
- `/SIMILAN_AGENCY_SETUP/WAYS_OF_WORKING.md`
- `/SIMILAN_AGENCY_SETUP/LAUNCHES/` (3 launch plans)
- `/SIMILAN_AGENCY_SETUP/BOTS/SYSTEM_PROMPTS_ALL.md`
- `/SIMILAN_AGENCY_SETUP/COMPETITOR_RESEARCH/COMPETITOR_AUDIT.md`

**In progress:**
- `/SIMILAN_AGENCY_SETUP/LAUNCHES/CONTENT_CALENDARS/` (to build)
- `/SIMILAN_AGENCY_SETUP/TEMPLATES/` (to build)
- `/SIMILAN_AGENCY_SETUP/REPORTS/` (auto-populated when reporting starts)

---

## SESSION NOTES

**March 14, 2026 Session:**
- Switched to Opus 3.5 Sonnet for better strategic thinking
- Fixed Telegram/Discord config (openclaw.json updated)
- Created MEMORY.md for persistence
- Built foundation (prompts + competitor audit)
- Ready to build content calendars next

---

**This memory file is your continuity. Update it after each major session.**
