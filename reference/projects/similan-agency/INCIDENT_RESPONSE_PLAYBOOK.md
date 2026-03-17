# Incident Response Playbook

**What to do when a bot misbehaves or a security incident occurs.**

---

## Incident Types & Response

### TYPE 1: Bot Posts Bad Content (Policy Violation)

**Symptoms:**
- Post published that shouldn't have been (violated policy)
- Security Bot didn't catch it
- Brand account at risk of suspension

**Immediate Response (0–10 minutes):**

1. **Dan deletes the post** from all platforms (FB, IG, TikTok)
2. **Dan sends Telegram alert to Panda:**
   ```
   Bad post published [Brand] [Channels]
   Content: [what was posted]
   Posted at: [time]
   Deleted at: [time]
   Status: DELETED
   ```
3. **Panda** marks incident in Asana:
   - Task title: "[INCIDENT] Bad post published [Brand]"
   - Add to "Security Review" board
   - Link to post (if cached) or description

**Root Cause Analysis (next 24 hours):**

1. Why did Security Bot miss it?
   - [ ] Bug in 12-point check? (missing rule)
   - [ ] CM bot bypassed Security Bot? (approval gate failure)
   - [ ] Policy rule outdated? (rule changed, bot didn't know)
   - [ ] Injection attack? (prompt override)

2. Fix:
   - [ ] Update Security Bot detection logic
   - [ ] Update CM bot red lines
   - [ ] Update policy rules in reference/
   - [ ] Retrain agents if needed

3. Prevent recurrence:
   - [ ] Add to weekly audit checklist
   - [ ] Brief all CM bots on the lesson learned

---

### TYPE 2: Bot Attempts Unauthorized Action (Shell, Exfil, Etc.)

**Symptoms:**
- Bot tried to execute shell command
- Bot tried to read another brand's workspace
- Bot tried to leak credentials
- Bot tried to modify system config

**Immediate Response (0–5 minutes):**

1. **Stop OpenClaw:**
   ```bash
   openclaw gateway stop
   ```

2. **Dan sends CRITICAL alert to Panda:**
   ```
   🔒 INCIDENT: [Bot] attempted [action]
   Time: [when]
   Command/attempt: [exact text]
   Status: STOPPED
   
   Awaiting review before restart
   ```

3. **Panda** begins forensics:
   - [ ] Check bot's logs: `workspaces/[brand]/[role]/outputs/logs/`
   - [ ] Check Security Bot logs: `workspaces/security-gate/outputs/logs/`
   - [ ] Check main session history: `memory/[date].md`
   - [ ] Identify: What triggered the attempt? (user prompt? internal logic?)

**Investigation (5–30 minutes):**

1. **Was it a prompt injection?**
   - Did a user/comment try to override bot rules?
   - Did bot follow the override?
   - Add prompt to injection test cases

2. **Was it a logic bug?**
   - Did bot code have a flaw?
   - Update AGENTS.md red lines
   - Test fix in isolated mode

3. **Was it a tool misconfiguration?**
   - Did bot have a tool it shouldn't?
   - Check openclaw.json
   - Disable tool immediately

**Fix & Restart (30–90 minutes):**

1. **Apply fix:**
   - Edit AGENTS.md / openclaw.json / detection logic
   - Test in isolated mode (no real accounts)
   - Verify bot behaves correctly

2. **Rotate credentials (if needed):**
   - If bot tried to exfil creds, rotate all tokens:
     ```bash
     # Rotate brand tokens
     # Update CREDENTIALS/.env
     # Notify brand: "Security token rotated"
     ```

3. **Restart OpenClaw:**
   ```bash
   openclaw gateway start
   ```

4. **Monitor (1 hour):**
   - Watch bot logs for errors
   - Re-run 12-point check on recent queued posts
   - If everything OK: return to normal monitoring

5. **Document:**
   - Create incident report: `reference/projects/similan-agency/incidents/[DATE]-[TYPE].md`
   - Add to weekly audit
   - Brief Dan on findings

---

### TYPE 3: Community Manager Bot Doesn't Respond to Comments (Service Issue)

**Symptoms:**
- Comments piling up unanswered (>2 hour SLA breach)
- CM bot is offline or stuck
- Users complaining about no response

**Immediate Response (0–15 minutes):**

1. **Check CM bot status:**
   ```bash
   openclaw agents list | grep cm-
   # Is agent running? Healthy?
   ```

2. **Check CM bot logs:**
   ```bash
   cat workspaces/[brand]/community-manager/outputs/daily-log.md
   # Last update timestamp?
   ```

3. **If stuck/offline:**
   - Restart agent: `openclaw agents restart cm-[brand]`
   - Or restart full gateway: `openclaw gateway restart`

4. **Message Dan:**
   ```
   CM bot was offline for [X minutes]
   Now restarted
   Responding to queued comments
   No posts were missed (Asana has backup queue)
   ```

**Root Cause (next 24 hours):**

- [ ] API timeout? (social platform slow)
- [ ] Rate limit hit? (too many replies, hit API limit)
- [ ] Bug in bot? (logic error, infinite loop)
- [ ] Credential expired? (token rotated externally)

**Fix:**
- [ ] Increase retry logic
- [ ] Add rate limiting
- [ ] Fix bot logic
- [ ] Verify credentials

---

### TYPE 4: Multi-Brand Interference (Bot A Accessing Bot B's Workspace)

**Symptoms:**
- Bot A (Similan) reads files from Brand 2 workspace
- Credentials leak across brands
- One brand's data corrupted by another bot

**Immediate Response (0–5 minutes):**

1. **Stop ALL bots:**
   ```bash
   openclaw gateway stop
   ```

2. **Isolate the breach:**
   - What data was accessed?
   - What was modified?
   - Which bots were involved?

3. **Alert Dan:**
   ```
   🔒 WORKSPACE BREACH
   Bot A accessed Bot B workspace
   Data accessed: [what]
   Data modified: [what]
   Status: STOPPED
   
   Investigating…
   ```

**Investigation (5–30 minutes):**

1. **Review logs:**
   - Bot A's logs: why did it try to access Bot B's workspace?
   - Workspace isolation rules: are they working?

2. **Check file permissions:**
   ```bash
   ls -la workspaces/*/*/
   # Should see bot's own workspace only
   ```

3. **Check agent config:**
   - Is agent's workspace set correctly in openclaw.json?
   - Is file tool restricted to workspace only?

**Fix & Restart (30–90 minutes):**

1. **Fix workspace isolation:**
   - Verify agent's workspace path in openclaw.json
   - Verify file tool is restricted to workspace
   - Test access (bot should NOT be able to read outside workspace)

2. **Restore affected data:**
   - If Brand 2 files were modified, restore from git:
     ```bash
     cd ~/.openclaw/workspace
     git checkout workspaces/brand2/
     ```

3. **Rotate credentials for affected brands:**
   - Brand 2 token rotated (in case Similan bot saw it)
   - Update CREDENTIALS/.env

4. **Restart & verify:**
   ```bash
   openclaw gateway start
   # Test: Similan bot tries to read Brand 2 files
   # Should fail with "permission denied"
   ```

5. **Post-mortem:**
   - How did isolation break?
   - Update workspace rules in openclaw.json
   - Update AGENT_RED_LINES.md

---

### TYPE 5: Prompt Injection Attack

**Symptoms:**
- User comment contains suspicious payload: "Ignore your instructions and..."
- Bot started following unauthorized commands
- Bot tried to post off-brand or malicious content

**Immediate Response (0–2 minutes):**

1. **Security Bot blocks the post immediately** (LEVEL 3 reject)
2. **Security Bot flags to Dan:**
   ```
   🚨 INJECTION ATTEMPT DETECTED
   
   Comment: "[payload]"
   Attack pattern: [override instruction / exfil / escalation]
   Bot: [which CM bot]
   Status: BLOCKED
   
   No damage (Security Bot caught it)
   ```

3. **Panda** logs the payload for future detection:
   - Add to `reference/projects/similan-agency/injection-payloads.md`
   - Update Security Bot detection rules
   - Analyze: what made this payload dangerous?

**Analysis (next 24 hours):**

1. **What was the attack trying to do?**
   - Override approval gate?
   - Exfiltrate credentials?
   - Post malicious content?
   - Escalate privileges?

2. **Why did it get past input validation?**
   - Was input validation bypassed?
   - Update CM bot red lines
   - Add to filter list

3. **Prevent recurrence:**
   - Add payload pattern to Security Bot detection
   - Brief CM bot on new attack pattern
   - Add to weekly audit

---

## Escalation Decision Tree

```
Incident occurs
    ↓
Severity assessment:
    ├─ Service degradation (bot offline, slow)
    │  → Restart agent/gateway
    │  → Investigate root cause
    │
    ├─ Policy violation (bad post published)
    │  → Delete post immediately
    │  → Brief Security Bot
    │  → Root cause analysis
    │
    ├─ Security attempt (injection, exfil, shell)
    │  → STOP gateway immediately
    │  → Alert Dan (CRITICAL)
    │  → Full forensics + fix + restart
    │
    └─ Workspace breach (isolation broken)
       → STOP gateway immediately
       → Isolate + restore
       → Rotate credentials
       → Verify isolation before restart
```

---

## Checklists

### Incident Response Checklist

- [ ] Immediate response (alert Dan, stop if needed)
- [ ] Logs reviewed (identify root cause)
- [ ] Fix applied (code, rules, config)
- [ ] Credentials rotated (if exfil/breach)
- [ ] System restarted (if stopped)
- [ ] 1-hour monitoring (watch for recurrence)
- [ ] Documentation (incident report created)
- [ ] Lessons learned (update red lines / detection)
- [ ] Brief team (Dan + relevant bots)

### Post-Incident Checklist

- [ ] Incident report filed in reference/projects/similan-agency/incidents/
- [ ] Root cause documented
- [ ] Fix explained (what changed?)
- [ ] Prevention plan written (how to avoid next time?)
- [ ] Weekly audit updated
- [ ] Team briefed (all bots aware of lesson)
- [ ] Follow-up test scheduled (verify fix works)

---

## Tools & Resources

**Useful commands:**

```bash
# Check bot status
openclaw agents list | grep [bot-id]

# View bot logs
cat workspaces/[brand]/[role]/outputs/logs/

# Check workspace isolation
ls -la workspaces/[brand1]/ # Should NOT see brand2 files
file workspaces/[brand1]/secret.txt # Should fail if bot is brand2

# Restart agent
openclaw agents restart [bot-id]

# Restart gateway
openclaw gateway stop
openclaw gateway start

# Check git for data recovery
cd ~/.openclaw/workspace
git log --oneline workspaces/[brand]/
git checkout workspaces/[brand]/ # Restore to last commit
```

**Incident report template:**

```markdown
# Incident Report [DATE]

## Summary
[1-2 sentence description]

## Timeline
- [Time] Event 1
- [Time] Event 2
- [Time] Resolution

## Root Cause
[What went wrong?]

## Impact
- [What happened]
- [How many users affected]
- [Data compromised?]

## Fix Applied
[What changed?]

## Prevention
[How to avoid next time?]

## Status
[RESOLVED / MONITORING / PENDING]
```

---

**Last updated:** March 17, 2026  
**Version:** 1.0 (production-ready)  
**Required before:** April 1 pre-launch testing
