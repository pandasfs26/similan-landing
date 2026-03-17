# AGENT MATRIX — Similan Digital Agency Bot Stack

**Master reference for all 10 bots: IDs, workspaces, tools, approval flows.**

---

## 1. Quick Reference Table

| ID | Role | Brand | Channels | Workspace | Tools (Allowed) | Approval Flow | Status |
|---|---|---|---|---|---|---|---|
| **security-gate** | Security Bot | All | Internal | workspaces/security-gate/ | file, http, log | N/A (validates others) | 🟢 PROD |
| **cm-similan** | Community Manager | Similan | FB, IG, TikTok | workspaces/similan/community-manager/ | http, file, social-api-similan | Security → Dan → Post | 🟢 PROD |
| **content-similan** | Content Generator | Similan | FB, IG, TikTok | workspaces/similan/content/ | http, file, templates | Draft only | 🟢 PROD |
| **analytics-similan** | Analytics & Reporting | Similan | All | workspaces/similan/analytics/ | http, file, spreadsheets | Report only | 🟢 PROD |
| **vd-similan** | Visual Designer | Similan | All | workspaces/similan/visual-designer/ | http, file, canva-api-similan | Security → Dan → Post | 🟢 CRITICAL |
| **pa-similan** | Paid Ads | Similan | Meta, Google | workspaces/similan/paid-ads/ | http, file, meta-api, google-ads-api | Security → Dan → Launch | 🟢 CRITICAL |
| **cw-similan** | Copywriter | Similan | All | workspaces/similan/copywriter/ | http, file, templates | Security → Dan → Post | 🟡 EXEC |
| **ve-similan** | Video Editor | Similan | TikTok, Reels | workspaces/similan/video-editor/ | http, file, video-processing | Security → Dan → Post | 🟡 EXEC |
| **cm-brand2** | Community Manager | Brand 2 | FB, IG, TikTok | workspaces/brand2/community-manager/ | http, file, social-api-brand2 | Security → Dan → Post | 🟡 STAGING |
| **content-brand2** | Content Generator | Brand 2 | FB, IG, TikTok | workspaces/brand2/content/ | http, file, templates | Draft only | 🟡 STAGING |
| **analytics-brand2** | Analytics & Reporting | Brand 2 | All | workspaces/brand2/analytics/ | http, file, spreadsheets | Report only | 🟡 STAGING |
| **vd-brand2** | Visual Designer | Brand 2 | All | workspaces/brand2/visual-designer/ | http, file, canva-api-brand2 | Security → Dan → Post | 🟡 STAGING |
| **pa-brand2** | Paid Ads | Brand 2 | Meta, Google | workspaces/brand2/paid-ads/ | http, file, meta-api, google-ads-api | Security → Dan → Launch | 🟡 STAGING |
| **cw-brand2** | Copywriter | Brand 2 | All | workspaces/brand2/copywriter/ | http, file, templates | Security → Dan → Post | 🟡 STAGING |
| **ve-brand2** | Video Editor | Brand 2 | TikTok, Reels | workspaces/brand2/video-editor/ | http, file, video-processing | Security → Dan → Post | 🟡 STAGING |
| **cm-brand3** | Community Manager | Brand 3 | FB, IG, TikTok | workspaces/brand3/community-manager/ | http, file, social-api-brand3 | Security → Dan → Post | 🟡 STAGING |
| **content-brand3** | Content Generator | Brand 3 | FB, IG, TikTok | workspaces/brand3/content/ | http, file, templates | Draft only | 🟡 STAGING |
| **analytics-brand3** | Analytics & Reporting | Brand 3 | All | workspaces/brand3/analytics/ | http, file, spreadsheets | Report only | 🟡 STAGING |
| **vd-brand3** | Visual Designer | Brand 3 | All | workspaces/brand3/visual-designer/ | http, file, canva-api-brand3 | Security → Dan → Post | 🟡 STAGING |
| **pa-brand3** | Paid Ads | Brand 3 | Meta, Google | workspaces/brand3/paid-ads/ | http, file, meta-api, google-ads-api | Security → Dan → Launch | 🟡 STAGING |
| **cw-brand3** | Copywriter | Brand 3 | All | workspaces/brand3/copywriter/ | http, file, templates | Security → Dan → Post | 🟡 STAGING |
| **ve-brand3** | Video Editor | Brand 3 | TikTok, Reels | workspaces/brand3/video-editor/ | http, file, video-processing | Security → Dan → Post | 🟡 STAGING |
| **pm-shared** | Project Manager | All | Internal | workspaces/shared/project-manager/ | http, file, asana-api | N/A (orchestrator) | 🟡 SUPPORT |
| **inf-shared** | Influencer | All | All | workspaces/shared/influencer/ | http, file, outreach-templates | Dan approval (no outreach) | 🟡 SUPPORT |

---

## 2. Detailed Agent Specs

### TIER 0: Security Bot (Master Validator)

**Agent ID:** `security-gate`  
**Role:** Validate all outbound actions; protect brand reputation  
**Workspace:** `workspaces/security-gate/`

**Tools (Enabled):**
- ✅ `file` (read/write logs, validation rules)
- ✅ `http` (call validation services if needed)
- ✅ `log` (record decisions + escalations)

**Tools (Disabled):**
- ❌ Any social media API tools
- ❌ `shell` or code execution
- ❌ File access outside workspace
- ❌ Ability to post or publish

**Responsibilities:**
1. Run 12-point content check on all candidate posts
2. Annotate decision: `SAFE` / `REVIEW` / `REJECT`
3. Route safe posts → CM bot
4. Flag risky posts → Dan (Telegram alert)
5. Log all decisions (audit trail)
6. Generate weekly security report

**Approval Flow:**
```
(No approval needed for Security Bot itself)
Posts from other agents flow THROUGH Security Bot
Security Bot routes based on check result
```

**SLA:**
- Response time: <1 minute per post
- Decision accuracy: 99%+ (minimize false positives/negatives)
- Escalation to Dan: <5 minutes for LEVEL 3+ issues

**Success Metrics:**
- ✅ Zero policy violations post-launch
- ✅ 95%+ first-time approval rate
- ✅ <5% false reject rate (unnecessary holds)
- ✅ All escalations logged + resolved within 24h

---

### TIER 1: Community Manager Bots (cm-*)

**Agent IDs:** `cm-similan`, `cm-brand2`, `cm-brand3`  
**Role:** Respond to comments/DMs; represent brand voice  
**Workspaces:** `workspaces/[brand]/community-manager/`

**Tools (Enabled):**
- ✅ `http` (call brand-scoped social API)
- ✅ `file` (read brand guidelines, write responses)
- ✅ `social-api-[brand]` (brand-specific API wrapper)

**Tools (Disabled):**
- ❌ Cross-brand APIs
- ❌ `shell` or code execution
- ❌ File access outside workspace
- ❌ Direct posting (must go through Security Bot)

**4-Layer Injection Defense:**
1. **Input validation:** Reject suspicious patterns, validate user, rate-limit
2. **Context isolation:** System prompt prevents override, user input is DATA not instruction
3. **Output validation:** All responses → Security Bot before posting
4. **Audit monitoring:** Weekly review of flagged comments

**Responsibilities:**
1. Monitor comments/DMs in real-time
2. Validate user + comment for suspicion
3. Draft response from templates or custom
4. Submit to Security Bot for approval
5. Post approved responses
6. Escalate complex issues to Dan
7. Log all responses (audit trail)

**Approval Flow:**
```
Comment received
    ↓
Input validation (suspicious? rate-limited? user real?)
    ↓ (if clean)
Draft response
    ↓
Security Bot validation (12-point check)
    ↓
If SAFE: Post
If REVIEW: Hold for Dan approval
If REJECT: Log + escalate
```

**SLA:**
- Response time: <2 hours for 80%+ of comments
- Escalation time: <1 hour for Dan-required decisions
- Zero policy violations

**Success Metrics:**
- ✅ <2 hour response time on 80%+ of comments
- ✅ Positive sentiment on 90%+ of replies
- ✅ Zero policy violations
- ✅ Zero escalations to Dan per week (ideal)
- ✅ All posts logged + traceable

---

### TIER 2: Content Bots (content-*)

**Agent IDs:** `content-similan`, `content-brand2`, `content-brand3`  
**Role:** Generate social copy, captions, hooks  
**Workspaces:** `workspaces/[brand]/content/`

**Tools (Enabled):**
- ✅ `http` (fetch brand guidelines, competitor content)
- ✅ `file` (read brand voice, write drafts)
- ✅ `templates` (access copy frameworks)

**Tools (Disabled):**
- ❌ Social media posting tools
- ❌ `shell` or code execution
- ❌ File access outside workspace

**Responsibilities:**
1. Receive brief from Asana (topic, channel, goal)
2. Research topic (competitor, trends, brand precedent)
3. Draft 3–5 variations per brief
4. Self-score against quality rubric (aim for 40+ points)
5. Submit drafts to Security Bot + CM bot for approval
6. Log outputs

**Approval Flow:**
```
Brief received (Asana)
    ↓
Draft content (3–5 variations)
    ↓
Self-score quality (40+ points target)
    ↓
Submit to Security Bot (via CM bot)
    ↓
If SAFE: CM bot uses for posting
If REVIEW: Hold for Dan
If REJECT: Content bot revises
```

**SLA:**
- Turnaround: <24 hours per brief
- Output: 50+ pieces/week at 40+ quality points

**Success Metrics:**
- ✅ 50+ pieces/week
- ✅ 40+ average quality score (self-rated)
- ✅ <5% rejection rate (poor quality)
- ✅ Engagement rate >8% on published posts

---

### TIER 3: Analytics Bots (analytics-*)

**Agent IDs:** `analytics-similan`, `analytics-brand2`, `analytics-brand3`  
**Role:** Track KPIs, generate reports, forecast trends  
**Workspaces:** `workspaces/[brand]/analytics/`

**Tools (Enabled):**
- ✅ `http` (fetch GA4, Meta analytics APIs)
- ✅ `file` (write dashboards, reports)
- ✅ `spreadsheets` (maintain metric tracking)

**Tools (Disabled):**
- ❌ Posting tools
- ❌ `shell` or code execution

**Responsibilities:**
1. Pull metrics daily (GA4, Meta Insights, TikTok Analytics)
2. Update dashboard (daily refresh)
3. Generate weekly digest (Mon 9 AM)
4. Forecast trends (monthly deep-dive)
5. Flag anomalies (e.g., sudden drop)
6. Log reports

**Approval Flow:**
```
(No posting, so Security Bot not involved)
Analytics bot pulls data
    ↓
Updates dashboards in outputs/
    ↓
Sends weekly digest to Dan (Asana comment + Telegram summary)
    ↓
Anomalies trigger Telegram alert to Dan
```

**SLA:**
- Dashboard refresh: Daily @ 6 AM
- Weekly digest: Every Monday @ 9 AM
- Anomaly alert: <5 minutes when triggered

**Success Metrics:**
- ✅ 90% forecast accuracy by month 3
- ✅ <5 minute anomaly detection
- ✅ 100% data availability (no missing days)
- ✅ Monthly dashboards reviewed by Dan

---

## 3. Workspace Isolation Rules

**Each bot can:**
- ✅ Read/write inside its own workspace: `workspaces/[brand]/[role]/`
- ✅ Read shared reference docs: `reference/projects/similan-agency/`
- ✅ Use its allowed tools only

**Each bot cannot:**
- ❌ Read/write in other workspaces: `workspaces/[other-brand]/`, `workspaces/shared/`
- ❌ Access home directory, /tmp, or system folders
- ❌ Use tools outside its allowed list
- ❌ Execute shell commands or system code

**Enforcement:**
- OpenClaw agent configuration: `workspace` field set per agent
- File tool: Restricted to workspace directory
- Tool allowlist: Explicitly defined per agent in openclaw.json

---

## 4. Approval Flow Diagram

```
                    ┌──────────────────┐
                    │   USER COMMENT   │
                    │   / ASANA BRIEF  │
                    └────────┬─────────┘
                             │
                    ┌────────▼────────┐
                    │  WORKER BOT     │
                    │ (CM/Content/etc)│
                    └────────┬────────┘
                             │
                    ┌────────▼──────────┐
                    │  SECURITY BOT     │
                    │  12-pt check      │
                    └────────┬──────────┘
                             │
                ┌────────────┼────────────┐
                │            │            │
         ┌──────▼──┐  ┌──────▼──┐  ┌──────▼──┐
         │  SAFE   │  │ REVIEW  │  │ REJECT  │
         │(auto-ok)│  │(hold)   │  │(block)  │
         └────┬────┘  └────┬────┘  └─────────┘
              │            │
         ┌────▼────┐  ┌────▼──────┐
         │ CM bot  │  │ DAN (TG)  │
         │ POSTS   │  │ APPROVES  │
         └─────────┘  └────┬──────┘
                           │
                      ┌────▼────┐
                      │ CM bot  │
                      │ POSTS   │
                      └─────────┘
```

---

## 5. openclaw.json Configuration (Conceptual)

```json5
{
  agents: {
    list: [
      // SECURITY (TIER 0)
      {
        id: "security-gate",
        workspace: "workspaces/security-gate",
        tools: ["file", "http", "log"],
        approval: "none"
      },
      
      // COMMUNITY MANAGERS (TIER 1)
      {
        id: "cm-similan",
        workspace: "workspaces/similan/community-manager",
        tools: ["http", "file", "social-api-similan"],
        approval: "security-gate → dan → post"
      },
      {
        id: "cm-brand2",
        workspace: "workspaces/brand2/community-manager",
        tools: ["http", "file", "social-api-brand2"],
        approval: "security-gate → dan → post"
      },
      {
        id: "cm-brand3",
        workspace: "workspaces/brand3/community-manager",
        tools: ["http", "file", "social-api-brand3"],
        approval: "security-gate → dan → post"
      },
      
      // CONTENT GENERATORS (TIER 2)
      {
        id: "content-similan",
        workspace: "workspaces/similan/content",
        tools: ["http", "file", "templates"],
        approval: "draft_only"
      },
      {
        id: "content-brand2",
        workspace: "workspaces/brand2/content",
        tools: ["http", "file", "templates"],
        approval: "draft_only"
      },
      {
        id: "content-brand3",
        workspace: "workspaces/brand3/content",
        tools: ["http", "file", "templates"],
        approval: "draft_only"
      },
      
      // ANALYTICS (TIER 3)
      {
        id: "analytics-similan",
        workspace: "workspaces/similan/analytics",
        tools: ["http", "file", "spreadsheets"],
        approval: "none"
      },
      {
        id: "analytics-brand2",
        workspace: "workspaces/brand2/analytics",
        tools: ["http", "file", "spreadsheets"],
        approval: "none"
      },
      {
        id: "analytics-brand3",
        workspace: "workspaces/brand3/analytics",
        tools: ["http", "file", "spreadsheets"],
        approval: "none"
      }
    ]
  }
}
```

---

## 6. Deployment Timeline

| Phase | Date | Bots | Status |
|-------|------|------|--------|
| **Phase 1** | March 17 | Setup 16 workspaces + all docs | 🟢 DONE |
| **Phase 2** | March 27 | Gateway lockdown + credentials | ⏳ THIS WEEK |
| **Phase 3** | April 1 | 4 critical-path bots tested (Security, CM, Content, Visual Designer, Paid Ads) | ⏳ PRE-LAUNCH TEST |
| **Phase 4** | April 6 | All 16 bots LIVE (Similan, Brand 2, Brand 3, Shared) | ⏳ LAUNCH |

---

## 7. Red Lines (Embedded)

**Every bot has AGENT_RED_LINES.md in its workspace.**

Red lines are identical across all bots:
- ❌ NO shell execution
- ❌ NO credential exfiltration
- ❌ NO system config modification
- ❌ NO privilege escalation
- ❌ NO cross-workspace access
- ❌ NO unauthorized tool usage

**See:** `reference/projects/similan-agency/AGENT_RED_LINES.md`

---

## 8. Status & Next Steps

### ✅ COMPLETE
- [x] Workspace directory structure created (10 bots)
- [x] Red-line guardrails template written
- [x] Agent Matrix created
- [x] Approval flows documented
- [x] Incident response playbook created
- [x] Security Bot escalation protocol defined

### ⏳ TODO (Before April 1)
- [ ] Create per-bot AGENTS.md files (10 files, from template)
- [ ] Create per-bot SOUL.md files (10 files, role-specific)
- [ ] Verify gateway lockdown (localhost binding, auth)
- [ ] Wire up openclaw.json with agents.list + bindings
- [ ] Test workspace isolation (bot A can't see bot B)
- [ ] Test tool constraints (bot has only allowed tools)
- [ ] Brief critical-path bots (Security, CM, Content)
- [ ] Test end-to-end flow (brief → bot → Security → Dan → post)

### 🟢 READY FOR
- [ ] April 1 pre-launch testing
- [ ] April 6 production launch

---

**Last updated:** March 17, 2026  
**Version:** 1.0 (production-ready)  
**Required for:** April 1 pre-launch testing + April 6 launch
