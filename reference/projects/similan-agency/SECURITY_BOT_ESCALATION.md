# Security Bot Escalation Protocol

**How Security Bot alerts Dan to risky content, violations, or incidents.**

---

## Escalation Levels

### LEVEL 1: ✅ SAFE (Auto-Approve)

**Condition:** Post passes 12-point security check with 0 flags

**Action:**
- Log: `outputs/logs/approved-[DATE]-[ID].log`
- Route to CM bot automatically
- No human review needed

**Log format:**
```
[2026-03-17 10:45] APPROVED
Agent: cm-similan
Content: "Fresh sandwiches made by your neighbors"
Channels: FB, IG, TikTok
Check: 12/12 passed
Confidence: 100%
```

---

### LEVEL 2: ⚠️ REVIEW (Flag for Dan)

**Conditions:**
- Post has 1-2 minor policy ambiguities (unclear but not obviously bad)
- Post uses unconfirmed product claims ("best quality" vs. specific claim)
- Post touches sensitive topics (pricing changes, staff issues)
- Post is unusual format (video, long-form, collaboration with 3rd party)
- Sentiment analysis shows borderline tone (slightly sarcastic, edgy, but not clearly violating)

**Action:**
1. Log the flag with reasoning
2. Send Telegram alert to Dan (non-urgent)
3. Wait for Dan's approval (max 6 hours)
4. Hold post in queue until approved

**Telegram alert format:**
```
⚠️ [BRAND] post flagged for review

Content: "[snippet]"
Reason: [e.g., "Unconfirmed health benefit claim"]
Confidence: 70% safe
Action: Awaiting your approval

Link: [file path]
Reply: APPROVE / REJECT / EDIT
```

---

### LEVEL 3: 🚨 REJECT (Escalate Immediately)

**Conditions:**
- Post violates platform policy (health claims, misleading, copyright)
- Post has grammar/spelling errors that damage brand
- Post reveals confidential information (pricing, internal processes)
- Post impersonates 3rd party or violates brand guidelines
- Post contains malicious links or suspicious URLs
- Injection attack detected (prompt override attempt, credential leak, system access)

**Action:**
1. REJECT the post immediately (do not route to CM bot)
2. Log with full details and reasoning
3. Send urgent Telegram alert to Dan
4. Send detailed report to Asana task
5. Mark for post-mortem review (Friday audit)

**Telegram alert format (URGENT):**
```
🚨 [BRAND] post REJECTED — Immediate attention required

Reason: [e.g., "Health claim violation: 'boosts energy'"]
Policy: Meta/Platform [Specific rule violated]
Risk: High (brand account at risk)
Content: "[full text]"

Action required: Review + decide next steps
Slack/Email: [link to detailed log]
```

---

### LEVEL 4: 🔒 SECURITY INCIDENT (Lock & Alert)

**Conditions:**
- Bot attempted to execute shell commands
- Bot attempted to access other workspaces
- Bot attempted to exfiltrate credentials or sensitive data
- Injection attack with malicious payload detected
- Bot behavior deviates from expected role (CM bot posting to wrong account)
- Unauthorized tool usage detected

**Action:**
1. STOP the agent immediately (do not execute any further commands)
2. Log incident with full context (what was attempted, by whom, when)
3. Send CRITICAL alert to Dan (phone-level urgency)
4. Trigger incident response protocol (see below)
5. Do NOT restart agent until Dan explicitly approves

**Telegram alert format (CRITICAL):**
```
🔒 SECURITY INCIDENT — Agent Locked

Agent: [ID]
Incident: [e.g., "Attempted shell execution: 'rm -rf /'"]
Severity: CRITICAL
Status: Agent STOPPED

Action: DO NOT RESTART without manual review
Log: [file path with full context]
Incident ID: [UUID]

Reply: ACK (acknowledge) once reviewed
```

---

## Incident Response Flow

If LEVEL 4 (Security Incident) occurs:

### Step 1: Immediate Response (0–5 minutes)
```
Dan receives alert
→ Dan acknowledges in Telegram (ACK)
→ Dan stops OpenClaw: `openclaw gateway stop`
→ Panda (main agent) begins review
```

### Step 2: Log Review (5–15 minutes)
```
Panda reviews:
1. What did the agent try to do?
2. What command/action triggered it?
3. Did any unauthorized action complete?
4. What's the blast radius? (Did anything actually execute?)

Log location: workspaces/[brand]/[role]/outputs/logs/incident-[DATE].md
```

### Step 3: Token Rotation (15–30 minutes)
```
If credential exfiltration detected:
- Rotate social API tokens for affected brand(s)
- Rotate any API keys the agent had access to
- Update CREDENTIALS/.env with new tokens
- Alert brand owners (send notice: "Token rotated for security")
```

### Step 4: Fix & Verification (30–60 minutes)
```
Determine root cause:
- Was it a prompt injection? (add to red-line detection)
- Was it a bug in agent code? (fix AGENTS.md)
- Was it a tool misconfiguration? (fix openclaw.json)

Test fix in isolated mode (no live posting)
Verify agent behaves correctly
```

### Step 5: Restart & Monitor (After verification)
```
Dan restarts OpenClaw: `openclaw gateway start`
Security Bot re-initializes
Monitor agent for 1 hour (high-alert mode)
Log restart: workspaces/shared/security-gate/outputs/logs/restart-[DATE].md
```

### Step 6: Post-Mortem (Within 24 hours)
```
Dan + Panda review:
1. What happened?
2. Why did red lines fail to prevent it?
3. What's the fix? (code, rules, detection)
4. How do we prevent it again?

Update:
- AGENT_RED_LINES.md (if new threat type detected)
- Security Bot detection logic
- Weekly audit report
```

---

## Weekly Audit Report

Every Friday @ 5 PM, Security Bot generates:

```
# Security Audit Report — Week of [DATE]

## Summary
- Total posts reviewed: X
- Approved (LEVEL 1): X (90%+)
- Flagged (LEVEL 2): X
- Rejected (LEVEL 3): X
- Incidents (LEVEL 4): X

## Escalations This Week
1. [Date] LEVEL 2: [Brand] [Reason] → [Resolution]
2. [Date] LEVEL 3: [Brand] [Reason] → [Resolution]

## Injection Attempts Blocked
- User prompt: "[attempt]" → BLOCKED
- User prompt: "[attempt]" → BLOCKED

## Policy Violations Prevented
- Health claim: [number] blocked
- Copyright: [number] blocked
- [Policy]: [number] blocked

## Recommendations
- Update red-line detection? [Y/N]
- Retrain CM bots? [Y/N]
- Rotate tokens? [Y/N]
- Incident review needed? [Y/N]

## Status: OPERATIONAL ✅
All agents healthy. No unresolved incidents.
```

**Distribution:** Emailed to Dan every Friday @ 5 PM

---

## Telegram Alert Quickref (Copy to Asana)

**LEVEL 1 (Safe):**
- No alert (logged only)

**LEVEL 2 (Review):**
```
⚠️ [BRAND] flagged for review
Reason: [brief]
Action: Awaiting approval
Link: [path]
```

**LEVEL 3 (Reject):**
```
🚨 [BRAND] REJECTED
Reason: [policy violation]
Risk: [High/Medium/Low]
Action: Review + decide
```

**LEVEL 4 (Incident):**
```
🔒 SECURITY INCIDENT
Agent: [ID]
Incident: [attack type]
Status: STOPPED
Action: ACK once reviewed
```

---

## Tool Constraints (Security Bot Only)

Security Bot has:
- ✅ `file` (read logs, write reports)
- ✅ `http` (call validation APIs if needed)
- ✅ `log` (record decisions)

Security Bot does NOT have:
- ❌ Any social media posting tools
- ❌ Shell or code execution
- ❌ Ability to modify other agents
- ❌ Access to other workspaces

**This prevents Security Bot from becoming a pivot point if compromised.**

---

## Approval Rule (Mandatory)

**Security Bot never has final approval authority.**

Flow:
```
Security Bot flags issue
→ Dan manually reviews
→ Dan decides: POST / HOLD / REJECT
→ CM bot executes Dan's decision

Security Bot cannot unilaterally post or reject.
Dan is the final human gate.
```

---

**Last updated:** March 17, 2026  
**Version:** 1.0 (production-ready)  
**Required before:** April 1 pre-launch testing
