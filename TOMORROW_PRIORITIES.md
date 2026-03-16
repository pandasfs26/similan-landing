# TOMORROW PRIORITIES — March 17, 2026

## INFRASTRUCTURE FIX (CRITICAL)

**Must fix before any bot work:**

1. ✅ **Tools profile upgraded** → "full" (DONE)
2. ✅ **Git/SSH configured** → Can push to GitHub (DONE)
3. ❌ **Telegram routing** → Messages go to bot, not me (FIX TOMORROW)
   - Issue: `dmScope` might be "per-channel" instead of "per-peer"
   - Fix: Review openclaw.json Telegram config, test messaging
4. ❌ **Browser automation** → Extract images from websites reliably (FIX TOMORROW)
   - Current: Can open browser, screenshot, but extracting image URLs is manual
   - Fix: Improve snapshot/evaluation to pull direct image URLs from DOM
5. ❌ **API key storage** → Safe vault for Meta, Google, Mailchimp credentials (FIX BEFORE BOTS)
   - Current: `.env` file (basic, works)
   - Better: Encrypted .env or external vault if available in OpenClaw

---

## LANDING PAGE CLEANUP (QUICK WIN)

- [ ] Extract real brand logos (Lucky 13, Vegan Table, Really Good Deli) from websites
- [ ] Find free Similan Islands panoramic image (Unsplash or similar)
- [ ] Update landing page with real imagery
- [ ] Push to GitHub, verify on Vercel
- **Time estimate:** 20 minutes once browser tools are reliable

---

## WAYS OF WORKING REVIEW

**What's in the doc:**
- 10 platforms (Meta, GA4, Google Ads, email, Asana, Telegram, Canva, Premiere, Looker, Drive)
- Bot interaction workflows (who talks to whom)
- Approval gates (Security → Dan → Project Manager → Post)
- Communication protocols (3 Telegram channels, response times)
- Weekly/monthly/quarterly cadence
- Data retention, troubleshooting, security best practices

**What we need to do tomorrow:**
1. [ ] **Section 1 (Tools):** Dan confirms which tools to actually use (some TBD)
2. [ ] **Section 2 (Credentials):** Dan provides access to Meta, GA4, etc. (or confirms timeline)
3. [ ] **Section 5 (Processes):** Agree on weekly rhythm (posting times, approval SLA)
4. [ ] **Section 8 (Security):** Lock in credential rotation schedule, incident response

**Key questions for Dan:**
- Which email platform? (Mailchimp vs Klaviyo decision deferred to April 1 — confirmed?)
- Which video editor? (DaVinci Resolve or Adobe Premiere?)
- Telegram channels ready? (Or do we set them up tomorrow?)
- Who's the backup approver if you're unavailable?

---

## BOT SETUP CHECKLIST (BEFORE WE START)

**These gates must pass:**

1. **Telegram integration working** — Messages from bots land in your channel, not somewhere else
2. **Image extraction automated** — I can grab logos and backgrounds from websites
3. **API credentials secured** — All keys in .env, nothing hardcoded, rotation schedule locked
4. **Asana connected** — Bots can read/write tasks, webhooks firing
5. **GA4 + Meta API verified** — Test pulls work, rate limits understood
6. **Security Bot rules drafted** — You approve what gets flagged/quarantined

**Once all 6 pass → Bot setup is safe to start**

---

## TONIGHT'S WORK SUMMARY

**What we delivered:**
- ✅ Domain (similan.digital.com) DNS pointed to Vercel
- ✅ Landing page deployed (similan-landing.vercel.app)
- ✅ Professional design (hero, bots, brands, CTA sections)
- ✅ Git/SSH authentication working
- ✅ Tools profile upgraded to "full"

**What fell short:**
- ❌ Real brand logos (fell back to text placeholders)
- ❌ Panoramic island background (fell back to gradient)
- ❌ Browser image extraction (hit friction, needs refinement)

**Why?**
- Late hour + tool limitations + one-shot attempts
- Should have focused infrastructure setup first, visual polish second

**Lesson for tomorrow:**
- Infrastructure > decoration
- Test tools early, don't assume capability
- If a task feels blocky, pivot to something else (landing page doesn't need perfect images to be useful)

---

## DAN'S EVENING FEEDBACK

> "I'm very disappointed. If this is what we're going through with you, how hard is it going to be to get each of the 10 bots set up?"

**Fair. Here's why:**
- I overpromised (said I could extract logos easily)
- I didn't diagnose tool friction early (browser image extraction is harder than expected)
- I settled for workarounds instead of stopping and explaining limitations
- **Result:** 2 hours of back-and-forth for landing page v0.9

**Tomorrow's approach:**
1. **Diagnose infrastructure gaps FIRST** (test Telegram, image extraction, API access)
2. **Fix them BEFORE touching bots** (no more guessing, all tools verified)
3. **Be honest about friction early** (if something's hard, say it immediately)
4. **Stop and escalate, don't workaround** (you can decide faster than I can hack around it)

---

## TOMORROW MORNING PLAN

**08:00 AM — Infrastructure diagnosis (30 min)**
- [ ] Test Telegram: Send message from me, confirm it lands in your session (not bot)
- [ ] Test image extraction: Try to pull a logo URL from Lucky 13's site programmatically
- [ ] Test API: Confirm Meta API + GA4 can be queried

**08:30 AM — Fix what's broken (60 min)**
- [ ] If Telegram routing broken: Debug dmScope, test fix
- [ ] If image extraction slow: Refine browser automation
- [ ] If API auth missing: Get credentials from Dan

**09:30 AM — Review WAYS_OF_WORKING.md (60 min)**
- [ ] Walk through 10 platforms together
- [ ] Lock in which tools to actually use
- [ ] Confirm approval process, Telegram channels, response times

**10:30 AM — Quick win: Landing page upgrade (20 min)**
- [ ] Pull real logos + panoramic
- [ ] Push to GitHub
- [ ] Verify on Vercel

**11:00 AM — Lock infrastructure, plan bot work**
- [ ] All 5 gates passing? ✅ Go to bot setup
- [ ] Any gates still failing? ⛔ Fix before moving on

---

**Sleep. We'll nail it tomorrow.**
