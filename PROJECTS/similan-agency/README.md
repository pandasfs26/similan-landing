# SIMILAN DIGITAL AGENCY — Project Overview

**Client:** Similan Digital Agency (Internal)  
**Launch 1:** April 6, 2026 (Vegan Table + Really Good Deli)  
**Launch 2:** May 6, 2026 (Lucky 13)  
**Bot Team:** 10 specialized AI bots  
**Timeline:** 3 weeks to first launch (March 17 → April 6)

---

## 📊 PROJECT STRUCTURE

```
similan-agency/
├── MASTER_ASSETS/          → Brand logos, photography, guides
├── CAMPAIGNS/              → Brand-specific campaigns (Q2 2026)
├── APPROVALS/              → Dan's review queue
├── REPORTS/                → KPI dashboards, weekly/monthly summaries
└── BOTS/                   → Bot workflow (inputs → outputs → logs)
```

---

## 🎯 BRANDS

| Brand | Type | Launch | Focus |
|-------|------|--------|-------|
| **Vegan Table** | Food/Wellness | April 6 | Thought leader, community hub, 10+ year history |
| **Really Good Deli** | B2B + B2C | April 6 | 10-year hotel supplier, now going direct |
| **Lucky 13** | Sandwiches | May 6 | 5 locations, fresh, community-first storytelling |

---

## 📅 TIMELINE

**Week 1 (March 17–23):**
- Upload brand logos → MASTER_ASSETS/BRAND_LOGOS/
- Upload photography → MASTER_ASSETS/PHOTOGRAPHY/
- Brief Content Manager bot
- First draft content

**Week 2 (March 24–30):**
- Content Manager outputs 50+ pieces
- Visual Designer creates graphics (3 variations per brief)
- Paid Ads bot starts Meta/Google campaigns
- Dan reviews & approves Week 1 content

**Week 3 (March 31–April 6):**
- Launch: Vegan Table + Really Good Deli
- Monitor metrics in real-time
- Community Manager handles comments/DMs
- Analytics bot sends daily digest

**Week 4+ (April 6–May 6):**
- Sustained operations across 2 brands
- Optimize based on performance
- Prepare Lucky 13 launch content
- May 6: Launch Lucky 13

---

## 🤖 BOT WORKFLOW

**Input → Bot → Output → Approval → Posting**

1. **Dan briefs:** Saves brief to `BOTS/content-manager/inputs/`
2. **Bot processes:** Reads brief, generates content
3. **Bot outputs:** Saves to `BOTS/content-manager/outputs/`
4. **Panda reviews:** Moves approved outputs to `CAMPAIGNS/*/PENDING-APPROVAL/`
5. **Dan approves:** Gives final sign-off or feedback
6. **Post:** Approved content moves to `CAMPAIGNS/*/APPROVED/` and scheduled

---

## 📋 CURRENT STATUS

- ✅ Bot system prompts (10 bots, locked in)
- ✅ Competitor audit (positioning locked)
- ✅ 12-week content calendars (drafted)
- ✅ Landing page live (Similan Islands background pending real images)
- ⏳ Brand logos needed
- ⏳ Brand photography needed
- ⏳ Credentials setup (.env file)

---

## 🚀 NEXT STEPS (BY EOD TODAY)

1. Upload Similan Islands photos → `MASTER_ASSETS/PHOTOGRAPHY/similan-islands/`
2. Upload brand logos → `MASTER_ASSETS/BRAND_LOGOS/{lucky13,vegan-table,rgd}/`
3. Create `.env` file with Meta, GA4, Asana, Telegram credentials
4. Confirm Asana workspace ready
5. Lock in weekly posting schedule

---

## 📞 DAN'S PREFERENCES

- **Response time:** <24h for approvals
- **Escalation:** Customer complaints, security threats, budget overages >20%
- **Autonomy:** First 2 months = Dan reviews all content; Month 3+ = spot-check mode
- **Communication:** Telegram (travels a lot), daily digest + alerts
- **Timezone:** Asia/Bangkok (GMT+7)
- **Tone:** Australian casual, direct, humor appreciated

---

## 🔗 RELATED FILES

- `BOTS/SYSTEM_PROMPTS/` — All 10 bot instructions
- `PROJECTS/similan-agency/CAMPAIGNS/2026-Q2-VEGAN-TABLE/CONTENT_CALENDAR.md` — Week-by-week plan
- `PROJECTS/similan-agency/CAMPAIGNS/2026-Q2-RGD/CONTENT_CALENDAR.md`
- `PROJECTS/similan-agency/CAMPAIGNS/2026-Q2-LUCKY13/CONTENT_CALENDAR.md`

---

**Ready? Start uploading assets. Panda's standing by.**
