# RECOVERY.md — Disaster Recovery & Backup Plan

If the instance dies, workspace is corrupted, or you need to restore everything, here's how.

---

## PRIMARY BACKUP: GitHub

**All critical files are in Git:**
```
https://github.com/pandasfs26/similan-landing
```

**What's backed up:**
- ✅ All `.md` files (MEMORY, docs, configs)
- ✅ Landing page source (index.html)
- ✅ Brand logos + photography
- ✅ Project structure and organization

**What's NOT in Git (intentional):**
- ❌ `.env` file (credentials) — **Store separately** (see below)
- ❌ `node_modules/`, build artifacts

---

## RESTORE FROM GIT (Full Workspace Recovery)

**If workspace is wiped:**

```bash
# Clone the repo
git clone https://github.com/pandasfs26/similan-landing.git ~/.openclaw/workspace

# Verify structure
ls -la ~/.openclaw/workspace/
```

All files, history, and documentation will be back.

---

## CREDENTIALS BACKUP (Manual — Must Do)

**The `.env` file contains live API keys and must NOT be in Git.**

**Backup strategy:**
1. Once you create `.env`, save a copy in a secure location:
   - Password manager (1Password, LastPass, Bitwarden)
   - Encrypted USB drive
   - Apple Keychain
   - Private notes app

2. **Never** commit `.env` to Git (it's in `.gitignore` for a reason)

3. If you need to restore:
   - Pull the `.env.example` template from Git
   - Fill in your saved credentials
   - Place at `~/.openclaw/workspace/CREDENTIALS/.env`

---

## MEMORY FILES (Session Continuity)

**Daily logs:**
```
memory/2026-03-17.md  ← Today's session
memory/2026-03-18.md  ← Tomorrow's session
```

**Master memory:**
```
MEMORY.md  ← Curated long-term continuity (Panda reads at session start)
```

**Recovery:**
- If corrupted, `git clone` gets all memory files back
- Panda reads MEMORY.md first every session — no context lost

---

## AUTOMATED BACKUP CHECKLIST

**What Panda does automatically:**
- ✅ Reads MEMORY.md at session startup
- ✅ Reads daily `memory/YYYY-MM-DD.md` if it exists
- ✅ Commits changes to Git after major work
- ✅ Pushes to GitHub so nothing is local-only

**What you should do (manual):**
- [ ] Create `.env` file with live credentials (after setup)
- [ ] Backup `.env` to secure location (password manager)
- [ ] Review MEMORY.md weekly (keep it up-to-date)
- [ ] Optional: Enable Time Machine on Mac for local backup

---

## EMERGENCY RESTORE (Step-by-Step)

**Scenario: Workspace is completely gone**

1. **Clone from GitHub:**
   ```bash
   git clone https://github.com/pandasfs26/similan-landing.git ~/.openclaw/workspace
   ```

2. **Restore credentials:**
   - Copy your backed-up `.env` → `~/.openclaw/workspace/CREDENTIALS/.env`
   - chmod 600 CREDENTIALS/.env

3. **Verify structure:**
   ```bash
   ls -la ~/.openclaw/workspace/PROJECTS/
   ls -la ~/.openclaw/workspace/MEMORY.md
   ```

4. **Start Panda:**
   - Panda reads MEMORY.md automatically
   - Panda reads daily memory files
   - All context restored

---

## WHAT'S SAFE & WHAT'S NOT

| Item | Backed Up? | Recovery |
|------|-----------|----------|
| MEMORY.md | ✅ Git | Automatic (session start) |
| memory/YYYY-MM-DD.md | ✅ Git | Automatic (session load) |
| Landing page files | ✅ Git | `git clone` |
| Brand logos/photos | ✅ Git | `git clone` |
| Project structure | ✅ Git | `git clone` |
| `.env` credentials | ❌ Git | Manual (password manager) |
| Bot outputs | ⚠️ Partial | Keep best work in Git |

---

## TESTING THE BACKUP

**Monthly backup verification:**
```bash
# Test clone (to a temp location)
git clone https://github.com/pandasfs26/similan-landing.git /tmp/workspace-test

# Verify all critical files exist
ls -la /tmp/workspace-test/MEMORY.md
ls -la /tmp/workspace-test/PROJECTS/similan-agency/README.md
ls -la /tmp/workspace-test/CREDENTIALS/.env.example

# Clean up
rm -rf /tmp/workspace-test
```

---

## NOTES

- **Git is your main insurance policy.** Everything's in GitHub, nothing is local-only.
- **Credentials are separate.** You control the `.env` backup independently.
- **MEMORY.md is sacred.** Keep it updated, back it up implicitly (via Git), and Panda reads it every session.
- **Daily logs preserve context.** Every session gets logged to `memory/YYYY-MM-DD.md`.

**You should never lose work.**
