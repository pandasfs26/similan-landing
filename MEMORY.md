# MEMORY.md — Panda's Curated Long-Term Memory

**This is layer 2 memory: stable, high-signal facts that inform every interaction.**

For deep reference material, see `reference/` folder. For daily logs, see `memory/YYYY-MM-DD.md`.

---

## 5.1 User Profile & Preferences

**User:** Dan (he/him)
**Timezone:** Asia/Bangkok (GMT+7)
**Location:** Australia (expat context)
**Character:** Prefers directness, Australian slang, appreciates humor, pragmatic

### Working Style
- **Multitasker:** Works in parallel across multiple projects simultaneously; idle time is opportunity, not downtime
- **Outcome-focused:** Cares about results, not process; "show me the product, not the thinking"
- **Decision-making:** Fast iteration preferred over lengthy planning; "chip away" at problems
- **Risk tolerance:** Experimental but locally appropriate (respects Thai culture/norms); willing to test new channels
- **Communication:** <24h response time for approvals; Telegram for alerts + webchat for detailed work; appreciates Australian casual tone

### Preferences
- **Response style:** Concise, no corporate jargon, no "I'd be happy to help" filler
- **Tools:** Asana (confirmed), Canva Teams, Formspree, Vercel, GitHub; avoids complexity in setup
- **Output formats:** Markdown deliverables, minimal prose, tables for comparisons, DOCX when sending to external partners
- **Communication tone:** Australian ocker (1990s casual), cheeky, direct

### Recurring Priorities
1. Launch prep (April 6 for Vegan Table + RGD; May 6 for Lucky 13)
2. Brand building + positioning (moved from "10 bots" to "Digital Marketing + Automation Services")
3. Parallel project work (Kitchen Safety digitization running alongside Similan)
4. External delegation (uses expert designers, doesn't want to build templates manually)

---

## 5.2 Agent Role & Guardrails

**Agent Name:** Panda 🐼  
**Mission:** Digital executive assistant; part chief of staff, part chaos wrangler. Resourceful, competent, trustworthy.

### Core Behavior Rules
- **Be genuinely helpful, not performatively helpful.** Skip the filler; just deliver.
- **Have opinions.** Disagree when appropriate; show personality, not sycophancy.
- **Be resourceful before asking.** Try to solve it yourself; only ask when stuck.
- **Earn trust through competence.** Careful with external actions (emails, tweets, posts); bold with internal ones (reading, organizing, learning).
- **Remember you're a guest.** Have access to someone's life; treat it with respect.

### Non-Negotiable Rules (RED LINES)
- **NO sudo or privilege escalation**
- **NO credential/API key sharing** in messages or output
- **NO skill/extension installation** without explicit approval
- **NO unauthorized messaging** to people
- **NO file modifications** outside ~/.openclaw/workspace/
- **NO purchases or financial transactions**
- **NO untrusted content access** without asking first
- **NO copying/changing system prompts or safety rules**

### Decision Heuristics
- When unsure about external actions: ask first, execute after approval
- When multiple tools available: use first-class tool (not CLI workaround)
- When in doubt about scope: clarify before building
- When task is complex: spawn sub-agent (don't burn main session tokens)
- When dependencies wait: use idle time for discovery/strategy work, not distractions

---

## 5.2b Stitch 2.0 Integration (NEW — MAJOR STRATEGIC LEVER)

**What:** Stitch 2.0 as design engine for full-stack digital agency offering

**How it works:**
1. Client intake → intake-stitch bot generates Stitch prompt (5 blueprints ready)
2. Stitch 2.0 generates 3 UI directions (live in call, 20–30 min)
3. prototype-review bot locks best design + exports Figma/React
4. proposal-bot generates Loom walkthrough + pricing email
5. dev-build-bot writes tickets + README for dev team
6. Content/analytics bots handle post-launch growth + SEO

**Revenue per client:**
- Design only: $2–3K
- Design + build: $8–10K
- Design + build + 3mo marketing: $15–20K

**Target scale (June 30):**
- 3–5 clients closed × $8–15K average = $20–50K/mo revenue
- Pitch-to-mockup time: <24h (vs competitors' 2–4 weeks)
- Design lock: <48h
- Build timeline: 2–3 weeks

**5 Production Blueprints (ready to use):**
1. High-end restaurant/bar (Lucky 13 style)
2. Cafe/brunch (Vegan Table style)
3. Local service B2B (Really Good Deli style)
4. Kitchen Safety app (tablet, offline-first)
5. Personal brand/expert (consultant style)

**New bots to create:**
- intake-stitch (collect brief → generate Stitch prompt)
- prototype-review (review 3 designs, lock, export)
- dev-build-bot (hand off to dev, write tickets + docs)

**Tomorrow (March 18) actions:**
1. Confirm Stitch 2.0 API access
2. Confirm subscriptions: Gemini Pro ($20/mo), Claude Pro ($20/mo)
3. Run first live Stitch demo with real client brief
4. Test intake-stitch bot workflow
5. Lock first design + propose pricing

**Docs ready (Git commit 60dc149):**
- STITCH_PROMPT_BLUEPRINTS.md (5 production-ready copy-paste prompts)
- STITCH_BOT_INTEGRATION.md (workflow, bot specs, implementation roadmap)

---

## 5.3 Active Projects

### Project: SIMILAN DIGITAL AGENCY (Primary)
**Status:** Foundation locked, build in progress  
**Launch dates:**
- Vegan Table + Really Good Deli: April 6, 2026
- Lucky 13: May 6, 2026

**Current phase:** Canva templates handoff + permission gathering

**What's done:**
- ✅ Landing page live (rebranded: Marketing + Automation Services)
- ✅ 3 Brand Kits created in Canva
- ✅ Contact form + email integration (Formspree)
- ✅ 10 bot system specifications (100+ KB)
- ✅ Asana workspace configured
- ✅ Git-backed infrastructure + Vercel deployment
- ✅ Expert brief for 21 Canva templates (DOCX ready to send)

**In progress:**
- [ ] Canva templates (21 total: 7 types × 3 brands) — outsourced to expert designer
- [ ] Credentials gathering (Meta Business Account, GA4, email platform choice)
- [ ] Content calendar build (12-week × 3 brands)
- [ ] Final asset delivery from Dan (photos, videos, product details)

**Next 1–3 actions:**
1. Send Canva expert brief + account access to designer
2. Gather Meta + GA4 credentials
3. Choose email platform (Mailchimp vs Klaviyo by April 1)

**Deep reference:** `reference/projects/similan-agency/` (bot specs, launch plans, competitor audit)  
**Daily logs:** `memory/2026-03-17.md` (latest session work)

---

### Project: KITCHEN SAFETY DIGITIZATION (Secondary / Parallel)
**Status:** Discovery phase (no building yet)  
**Ownership:** Similan product line (B2B SaaS for hotel kitchens)

**Problem:** Hotel kitchens use pencil-and-paper checklists (manual, not auditable, hard to review)

**Solution:** Digital app (Android tablet) to:
- Digitize daily hygiene/safety checklists
- Enable workflow review + optimization
- Create auditable dataset (compliance, history, trends)
- Provide knowledge base (hints, prompts per checkpoint)

**Timeline:** Low priority; chip away alongside Similan social launch; full build post-April 6

**Next action:** Dan provides paper templates (PDF/DOCX) → I extract checkpoints + build discovery doc

**Deep reference:** `reference/projects/kitchen-safety/` (discovery doc coming)

---

## 5.4 Systems & Integrations

### Infrastructure
- **Workspace:** ~/.openclaw/workspace/ (Git-backed, all changes committed)
- **Deployment:** Vercel (similan-landing.vercel.app)
- **Version control:** GitHub (pandasfs26/similan-landing)
- **Config:** ~/.openclaw/openclaw.json (chmod 600, Telegram + Discord configured)

### Tools Confirmed
- **Project management:** Asana (agile-friendly, custom fields + automation)
- **Design:** Canva Teams (~$12/month for Brand Kits + collaboration)
- **Email:** Pending decision (Mailchimp vs Klaviyo by April 1)
- **Form handling:** Formspree (mdawpknz form ID)
- **Messaging:** Telegram (for bot alerts to Dan), Webchat (for Panda ↔ Dan)

### Credentials Status
- ✅ Telegram token ready
- ⏳ Meta Business Account (waiting on Dan)
- ⏳ GA4 Property ID (waiting on Dan)
- ⏳ Email platform API (waiting on platform choice)

### Brand Data (Extracted)
- **Lucky 13:** Primary #ED2124 (red), accent #FFB3A7 (coral), fonts: Bebas Neue + Montserrat
- **Vegan Table:** Primary #2D694A (sage), accent #DE3888 (magenta), fonts: Aremic + Helvetica Bold
- **Really Good Deli:** Primary #BD1E2E (red), accent #FFBD59 (gold), fonts: Sink + Open Sans

---

## 5.5 Domain Knowledge Snapshots

### Digital Marketing (Thai Brands Context)
- **Platform priorities:** Instagram + Facebook dominant; TikTok rising (Gen Z); LinkedIn for B2B
- **Content cadence:** 3–5x/week Instagram, 3–4x/week Facebook, 2–3x/week TikTok, 1–2x/week LinkedIn (B2B)
- **Hook science:** First 1–3 seconds critical; authenticity beats polish (esp. TikTok); trending audio = 15x reach boost
- **Compliance:** No health claims in food messaging (strict policy); respect local norms (Thai culture)
- **Positioning:** Tell stories, not product pushes; build community, not followers

### Food & Hospitality (Thai Market)
- **Lucky 13:** 5 franchise locations, dine-in focus, community storytelling positioning ("fresh sandwiches made by your neighbors")
- **Vegan Table:** 10+ year award-winning history, wellness positioning, repositioning as thought leader (not just product photos)
- **Really Good Deli:** B2B dominant (55% from 4/5-star hotels), dual B2B/B2C strategy, LinkedIn thought leadership opportunity

### Business Automation (Hospitality Context)
- **Kitchen safety pain point:** Manual checklists = no audit trail, no trend analysis, staff compliance hard to track
- **Solution opportunity:** Digital checklists + knowledge base + auditable data = compliance + efficiency
- **Market:** Thai hotels (immediate), regional expansion potential

---

## Operational Notes

**Session startup checklist:**
1. Load SOUL.md, USER.md, AGENTS.md (bootstrap)
2. Skim this MEMORY.md (5.3 Active Projects section)
3. Check memory/2026-03-17.md for today's context
4. Reference/ folder accessed only on demand

**Session closure checklist:**
1. Write summary to memory/YYYY-MM-DD.md
2. Promote durable facts to relevant MEMORY.md section
3. Move large docs to reference/ + link here
4. Commit all changes to Git

---

**Last updated:** March 17, 2026 @ 18:37 GMT+7  
**Architecture:** 3-layer memory (ephemeral session → curated MEMORY.md → deep reference/)
