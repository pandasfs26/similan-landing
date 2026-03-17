# OpenClaw Workspace — Multi-Project Agency Operations

Welcome. This is your command center for all digital agency work. One place for credentials, bots, and infinite projects.

---

## 🗂️ DIRECTORY GUIDE

### **CREDENTIALS/** 
🔒 **Master vault for API keys and secrets**
- `.env` — Live credentials (DO NOT commit to Git)
- `.env.example` — Template for reference (safe to commit)
- Permissions: `600` (Panda only)
- Used by: All bots across all projects

### **SHARED_INFRASTRUCTURE/**
⚙️ **Cross-project tools and configs**
- `API_CONFIGS/` — Asana, Slack, Telegram, Meta settings
- `DEPLOYMENT/` — Vercel, GitHub, hosting scripts
- `MONITORING/` — Health checks, logging, alerts

### **BOTS/**
🤖 **The 10-bot system (shared across projects)**
- `SYSTEM_PROMPTS/` — Locked, master bot instructions
- `SHARED_TOOLS/` — Common utilities, helper scripts
- `BOT_LOGS/` — Execution history, debug logs

### **SKILLS/**
📚 **Reusable OpenClaw skills library**
- Custom skills you develop for recurring tasks
- Shareable, versionable, scalable

### **PROJECTS/**
🎯 **Client work, campaigns, deliverables**

Each project folder (e.g., `similan-agency/`) contains:

#### **MASTER_ASSETS/**
- `BRAND_LOGOS/` — Client logos (primary, secondary, icon variants)
- `PHOTOGRAPHY/` — All approved brand photography
- `BRAND_GUIDES/` — PDFs, color codes, typography rules

#### **CAMPAIGNS/**
- `2026-Q2-VEGAN-TABLE/` — Brand-specific campaign folder
  - `DRAFTS/` — Work-in-progress (bot outputs here first)
  - `PENDING-APPROVAL/` — Ready for Dan review
  - `APPROVED/` — Dan signed off, ready to post
- `CONTENT_CALENDAR.md` — Week-by-week plan
- `PERFORMANCE_NOTES.md` — What's working, what's not

#### **APPROVALS/**
Dan's review queue:
- `PENDING/` — Waiting for sign-off
- `APPROVED/` — Locked in, schedule to post
- `REJECTED/` — Sent back with feedback

#### **REPORTS/**
Auto-generated metrics:
- `WEEKLY/` — Daily digest summaries
- `MONTHLY/` — KPI rollups
- `QUARTERLY/` — Strategic reviews

#### **BOTS/** (Project-level)
Bot workflow folders:
- `content-manager/` → `inputs/` (briefs) → `outputs/` (copy) → `logs/`
- `visual-designer/` → `inputs/` → `outputs/` → `logs/`
- (Same for all 10 bots)

---

## 📋 NAMING CONVENTIONS

- **Dates:** `YYYY-MM-DD` prefix
  - Good: `2026-03-17-Lucky13-Instagram-Carousel.md`
  - Bad: `lucky13_march_carousel_v2.md`

- **Brands:** lowercase with hyphens
  - Good: `lucky13`, `vegan-table`, `rgd`
  - Bad: `Lucky 13`, `LUCKY_13`, `Lucky-Thirteen`

- **Versions:** `v1`, `v2`, `FINAL` suffix
  - Good: `2026-03-17-Post-PENDING-APPROVAL-v2.md`
  - Bad: `draft_latest_final_real.md`

- **Status in filename:** Explicit
  - `PENDING-APPROVAL`, `APPROVED`, `REJECTED`, `DRAFT`, `SCHEDULED`

---

## 🔐 PERMISSIONS GUIDE

| Path | Permissions | Purpose |
|------|-------------|---------|
| `CREDENTIALS/.env` | `600` | Master secrets (Panda only) |
| `BOTS/SYSTEM_PROMPTS/` | `644` | Shared bot instructions (readable by all) |
| `PROJECTS/*/MASTER_ASSETS/` | `644` | Brand assets (readable by bots) |
| `PROJECTS/*/APPROVALS/PENDING/` | `644` | Bot outputs → Dan review |
| `PROJECTS/*/APPROVALS/APPROVED/` | `644` | Dan approved → ready to post |
| `PROJECTS/*/BOTS/*/outputs/` | `644` | Bot workflow outputs |
| `MEMORY.md` | `600` | Master continuity (workspace only) |

---

## 🚀 WORKFLOW: ADD A NEW PROJECT

1. Create folder: `PROJECTS/new-project-name/`
2. Copy structure (MASTER_ASSETS, CAMPAIGNS, APPROVALS, REPORTS, BOTS)
3. Create `README.md` with project overview
4. Add brand-specific system prompts to `BOTS/SYSTEM_PROMPTS/`
5. Done — bots can start reading from `inputs/`, writing to `outputs/`

---

## 🔄 TYPICAL BOT WORKFLOW

1. **Dan briefs:** "Create 5 Instagram captions for Lucky 13 this week"
2. **Input:** Brief saved to `PROJECTS/similan-agency/BOTS/content-manager/inputs/2026-03-17-Lucky13-Brief.md`
3. **Bot runs:** Content Manager reads brief, generates 5 variations
4. **Output:** `PROJECTS/similan-agency/BOTS/content-manager/outputs/2026-03-17-Lucky13-Captions-v1.md`
5. **Move:** Panda moves approved outputs to `CAMPAIGNS/2026-Q2-LUCKY13/PENDING-APPROVAL/`
6. **Dan reviews:** Approves or rejects with feedback
7. **Post:** Approved content moves to `CAMPAIGNS/2026-Q2-LUCKY13/APPROVED/` and scheduled

---

## 📖 CONTINUITY FILES (MASTER LEVEL)

- **MEMORY.md** — Long-term continuity between you & Panda (workspace-wide)
- **SOUL.md** — Panda's persona and boundaries
- **AGENTS.md** — Workspace guidelines and philosophy
- **TOOLS.md** — Local setup notes (cameras, SSH hosts, etc.)
- **USER.md** — You (Dan) — timezone, preferences, communication style

---

## 🎯 GETTING STARTED

1. **Add credentials:** `CREDENTIALS/.env` (get template from `.env.example`)
2. **Configure bots:** Drop system prompts into `BOTS/SYSTEM_PROMPTS/`
3. **Create first project:** Similan Agency is live in `PROJECTS/similan-agency/`
4. **Upload assets:** Drop logos into `PROJECTS/similan-agency/MASTER_ASSETS/BRAND_LOGOS/`
5. **Start campaigns:** Create campaign folders, brief the bots, watch them go

---

## ⚡ QUICK COMMANDS

```bash
# View workspace structure
tree -L 3 ~/.openclaw/workspace/PROJECTS/

# Check file permissions
ls -la ~/.openclaw/workspace/CREDENTIALS/

# Create new project
mkdir -p ~/.openclaw/workspace/PROJECTS/new-project/{MASTER_ASSETS,CAMPAIGNS,APPROVALS,REPORTS,BOTS}

# Archive old campaign
mv ~/.openclaw/workspace/PROJECTS/similan-agency/CAMPAIGNS/OLD_CAMPAIGN ~/.openclaw/workspace/PROJECTS/similan-agency/CAMPAIGNS/ARCHIVED/
```

---

**Questions? Ask Panda. She's got the full map.**
