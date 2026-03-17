# Stitch 2.0 Integration — OpenClaw Bot Workflow

**Version:** 1.0  
**Date:** March 17, 2026  
**Status:** Ready to implement tomorrow morning

---

## ARCHITECTURE OVERVIEW

**Stitch sits in the pitch-to-production pipeline:**

```
Client Brief (Intake Bot)
    ↓
Stitch Prompt Generation (intake-stitch bot)
    ↓
Stitch UI Generation (human runs Stitch 2.0 live)
    ↓
Prototype Review (prototype-review bot)
    ↓
Proposal Generation (proposal-bot)
    ↓
Design + Build (dev-build-bot)
    ↓
Launch + Marketing (content-bot + analytics-bot)
```

---

## NEW BOTS TO CREATE

### 1. Intake-Stitch Bot (`intake-stitch`)

**Role:** Collect client brief → Generate Stitch prompt

**Daily workflow:**
1. Receive client intake form (via Asana)
2. Extract key data:
   - Industry (restaurant, cafe, service, app, personal brand)
   - Brand constraints (colors, tone, audience)
   - Required pages/features
   - Budget tier
3. Match to blueprint (Blueprint 1–5)
4. Substitute client values into blueprint
5. Output: **Polished Stitch prompt** (ready to copy-paste into Stitch)
6. Notify: "Stitch prompt ready; run in Stitch 2.0 now"

**Tools:**
- http (Asana API to fetch brief)
- file (workspace files)
- stitch-prompts (blueprint templates)

**Success metric:**
- ✅ Stitch prompt generated in <15 min
- ✅ All client data captured, no gaps
- ✅ Prompt is copy-paste ready (zero manual tweaks)

---

### 2. Prototype-Review Bot (`prototype-review`)

**Role:** Review 3 Stitch outputs → Pick best → Export

**Daily workflow:**
1. Receive 3 Stitch UI outputs (designs A, B, C)
2. Review against brand fit:
   - Does layout match intended tone?
   - Are CTAs prominent?
   - Is mobile experience clear?
   - Any brand constraint violations?
3. Score each (A: 8/10, B: 9/10, C: 6/10)
4. Flag best option (B)
5. Request designer/client feedback (Asana comment)
6. Once approved: Export Figma + HTML/React from Stitch
7. Output: **Design locked + exports ready for dev**

**Tools:**
- file (review notes)
- design-feedback (annotation tool)
- stitch-export (grab Figma, code)

**Success metric:**
- ✅ Review completed in <2 hours
- ✅ Design locked within 1 business day
- ✅ No rework after lock

---

### 3. Proposal-Bot (Enhanced)

**Role:** Wrap Stitch design → Pricing + timeline email

**Daily workflow:**
1. Receive locked design + client info
2. Generate deliverables:
   - **Annotated screenshots** (3 key screens with callouts)
   - **Loom script** (5 min walkthrough: "Here's what we built for you")
   - **Pricing email:**
     ```
     Option 1: Design Only - $2,500
     (Figma file + handoff to your dev team)
     
     Option 2: Design + Build - $10,000
     (Fully built, deployed, ready to use)
     
     Option 3: Design + Build + 3mo Marketing - $18,000
     (Full launch + social + content + analytics setup)
     ```
3. Send proposal email (with Loom embed + screenshots)
4. Log in Asana
5. Await client response (track in CRM)

**Tools:**
- http (Loom API to generate video links)
- file (screenshot management)
- templates (proposal email templates)
- asana-api (log proposal status)

**Success metric:**
- ✅ Proposal sent within 24 hours of design lock
- ✅ 60%+ close rate on Option 2 or Option 3
- ✅ 14-day sales cycle average

---

### 4. Dev-Build-Bot (`dev-build-bot`)

**Role:** Hand off design → Write tickets + docs + risk flags

**Daily workflow:**
1. Receive approved design (Figma + Stitch exports)
2. Analyze what needs to be built:
   - Forms (contact, booking, signup)
   - API integrations (analytics, email, CMS)
   - Content management (blog, menu updates)
   - SEO setup (sitemap, schema markup)
3. Generate:
   - **Jira/Asana tickets** (one per feature/integration)
   - **README** (setup + deployment notes)
   - **Risk flags** (access requirements, third-party keys, timeline risks)
4. Assign to dev team
5. Coordinate with analytics-bot (post-launch tracking)
6. Output: **Development team ready to execute**

**Tools:**
- file (ticket + README generation)
- asana-api (create tasks)
- http (flag access/credential needs)

**Success metric:**
- ✅ Tickets generated in <4 hours
- ✅ Dev team can start same day
- ✅ All blockers flagged upfront
- ✅ <3 week build timeline for simple sites

---

## WORKFLOW TIMELINE

### Day 1: Client Call + Intake
- **10:00 AM:** Discovery call (30 min)
  - What do you do?
  - Who's your audience?
  - What's your main CTA?
  - Any brand constraints?
- **10:30 AM:** intake-stitch bot processes brief
- **11:00 AM:** Stitch prompt ready (Asana notification)

### Day 1: Design Generation
- **11:00 AM–12:00 PM:** You run Stitch 2.0 live
  - Paste prompt
  - Generate 3 options
  - Export Figma + HTML
- **12:00 PM:** Share 3 options with client (Figma link or screenshot)

### Day 1–2: Design Review
- **Day 1 PM:** Client feedback (usually 24–48h turnaround)
- **Day 2 morning:** prototype-review bot scores options, recommends best

### Day 2: Design Lock + Proposal
- **11:00 AM:** Design locked
- **11:30 AM:** proposal-bot generates Loom + email
- **12:00 PM:** Proposal sent to client
- **Next 3–14 days:** Sales cycle (typically closes within week)

### Upon Close: Build Handoff
- **Day 1:** dev-build-bot generates tickets + README
- **Day 2:** Dev team starts (typically 2–3 week build)
- **Week 3–4:** Launch + hand off to content + analytics bots

---

## STITCH API INTEGRATION

**What you need tomorrow:**
1. Stitch 2.0 API credentials (likely rate-limited free tier or pro plan)
2. Export endpoints:
   - `/generate` (POST: prompt → 3 designs)
   - `/export/figma` (GET: design ID → Figma file)
   - `/export/react` (GET: design ID → React/Tailwind code)
   - `/export/html` (GET: design ID → HTML/CSS)

**Bot integration:**
- intake-stitch calls `/prompt-generate` (our template → formatted Stitch prompt)
- prototype-review calls `/export/*` to grab design files
- dev-build-bot uses React export to scaffold component structure

---

## STORAGE & MEMORY

**Each project gets BRAND_UI.md:**

```
├── projects/
│   └── [client-name]/
│       ├── BRAND_UI.md (colors, fonts, tone)
│       ├── stitch-outputs/ (Figma, HTML, React)
│       ├── proposals/ (annotated screenshots, Loom link)
│       ├── development/ (tickets, README, deployed URL)
│       └── analytics/ (post-launch metrics)
```

**BRAND_UI.md fed to:**
- Content Bot (match social posts to design aesthetic)
- Community Bot (reply tone matches brand voice)
- Analytics Bot (measure which design elements convert)

---

## PRICING & TIERS

**Stitch 2.0:**
- Free tier: [TBD generation quota]
- Pro tier: [TBD cost, higher quota]
- **Decision:** Start free, monitor quota usage, upgrade if needed

**Your AI subscription stack (needed tomorrow):**
- **Gemini Pro:** $20/mo (LLMs for all bots + Stitch integration)
- **Claude Pro:** $20/mo (advanced reasoning for dev-build-bot + analytics)
- **Figma Teams:** $12/mo (already have)
- **Asana Pro:** $10.99/mo (task management)
- **Vercel:** ~$20/mo (deployment + scaling)

**Total:** ~$80–100/mo infra → Supports $20K–50K/mo client revenue

---

## SUCCESS METRICS

**By end of Q2 (June 30):**

| Metric | Target | Path to Success |
|--------|--------|-----------------|
| **Pitch-to-mockup time** | <24h | intake-stitch + Stitch generator |
| **Design lock time** | <48h | prototype-review bot speed |
| **Sales close rate** | 40%+ | Compelling proposal-bot emails + Loom videos |
| **Build timeline** | 2–3 weeks | dev-build-bot ticket generation |
| **Clients closed** | 3–5 | Run 1 full pilot (March 20–31) + scale (April+) |
| **Revenue** | $20–40K | 3 clients × $8–15K average |

---

## IMPLEMENTATION ROADMAP

**Tomorrow morning (March 18):**
1. Confirm Stitch 2.0 API access
2. Confirm subscriptions (Gemini Pro, Claude Pro)
3. Test intake-stitch bot with real client brief
4. Run Stitch generator live (show 3 options in call with Dan)
5. Lock first design

**March 20–31 (Week 1):**
1. intake-stitch bot fully operational
2. prototype-review bot tested
3. proposal-bot sending emails
4. First client proposal sent

**April 1–6 (Pre-launch):**
1. First client closed (likely)
2. dev-build-bot generating tickets
3. Build underway
4. Parallel: Kitchen Safety discovery ongoing

**April 6+ (Post-launch):**
1. First site launches
2. Analytics-bot tracks performance
3. Content-bot promoting it
4. 2–3 more clients in pipeline

---

## EDGE CASES & CONTINGENCIES

**What if Stitch quota hits limit?**
- Monitor usage weekly
- If approaching limit: Upgrade to pro tier or add Midjourney + Figma as overflow
- Keep templates tight (no endless iterations)

**What if design needs major revision after lock?**
- One revision round included in "Design" tier
- Anything beyond: $1–2K additional charge or move to Option 3

**What if dev timeline slips?**
- Flag in dev-build-bot risk assessment upfront
- Client expectation: "Tight but doable; we'll alert by day 5 if we see issues"
- Contingency: Hire freelance dev if needed (still margin-positive at $8K+ budget)

---

**Ready to execute tomorrow morning.**

Commit: STITCH_BOT_INTEGRATION.md + STITCH_PROMPT_BLUEPRINTS.md
