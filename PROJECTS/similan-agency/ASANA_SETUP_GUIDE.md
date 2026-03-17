# ASANA SETUP GUIDE — Similan Agency

**Goal:** Build a bulletproof Asana workspace in 30 minutes that orchestrates all 10 bots.

---

## STEP 1: CREATE THE MASTER PROJECT (5 minutes)

**In Asana:**
1. Click **+ New Project**
2. Name: `Similan Agency — Master`
3. Description: `10-bot system for Vegan Table, Really Good Deli, Lucky 13`
4. Privacy: `Private` (only you + bots)
5. Template: Start blank
6. Click **Create**

---

## STEP 2: SET UP SECTIONS (Workflow State Machine) (5 minutes)

Delete default sections. Create these:

| Section | Meaning | Who Can Move Tasks Here |
|---------|---------|------------------------|
| **Backlog** | Future work, ideas, not started | Project Manager Bot |
| **In Progress** | Actively being worked on | Content Manager, Visual Designer, other execution bots |
| **Review** | Waiting for approval | Security Bot, Dan (final approval) |
| **Approved** | Dan signed off, ready to publish | Community Manager (posts now) |
| **Scheduled** | Posted, waiting for publish time | Content Manager (batches for scheduling) |
| **Done** | Published, monitoring engagement | Analytics Bot (reports on performance) |

**How to create:**
1. Click **+ Add section** in the main area
2. Type section name
3. Press Enter
4. Repeat for all 6 sections
5. Drag sections into order (Backlog → In Progress → Review → Approved → Scheduled → Done)

---

## STEP 3: CREATE CUSTOM FIELDS (10 minutes)

These fields track what matters:

**Field 1: Brand**
- Type: Single Select
- Options:
  - Lucky 13
  - Vegan Table
  - Really Good Deli

**Field 2: Content Type**
- Type: Single Select
- Options:
  - Feed Post
  - Carousel
  - Reel/TikTok
  - Story
  - Email
  - Blog Post
  - LinkedIn Article
  - Ad Creative
  - Video
  - Other

**Field 3: Assigned Bot**
- Type: Single Select
- Options:
  - Content Manager
  - Visual Designer
  - Paid Ads
  - Community Manager
  - Analytics
  - Copywriter
  - Video Editor
  - Influencer
  - Project Manager
  - Security
  - Unassigned

**Field 4: ROAS Target** (for ads only)
- Type: Number
- Used by: Paid Ads Bot

**Field 5: Approval Status**
- Type: Single Select
- Options:
  - Pending Security Review
  - Pending Dan Approval
  - Approved
  - Rejected (needs revision)

**How to create custom fields:**
1. Click **Customize** (top right)
2. Click **+ Add custom field**
3. Fill in field name + type
4. Add options (for dropdown fields)
5. Click **Save**
6. Repeat for all 5 fields

---

## STEP 4: CREATE TASK TEMPLATES (10 minutes)

**Template 1: Social Media Content**

```
Task Name: [Brand] - [Content Type] - [Date]
Example: "Vegan Table - Instagram Carousel - March 24"

Description:
---
**Brief:**
[Content Manager Bot, fill this in with what the post should be about]

**Requirements:**
- Platform: [Instagram/Facebook/TikTok/LinkedIn]
- Post type: [Feed/Carousel/Reel/Story]
- Key message: [What's the main point?]
- CTA: [What do we want people to do?]
- Hashtags: [Any specific tags?]

**Workflow:**
1. Content Manager creates copy + brief
2. Visual Designer creates graphics (3 variations)
3. Security Bot reviews for compliance
4. Dan approves (or requests changes)
5. Post scheduled
6. Analytics tracks performance

**Subtasks:**
- [ ] Content brief finalized
- [ ] Copy written (Content Manager)
- [ ] Graphics created - Variation A (Visual Designer)
- [ ] Graphics created - Variation B (Visual Designer)
- [ ] Graphics created - Variation C (Visual Designer)
- [ ] Security review passed
- [ ] Dan approval received
- [ ] Posted
- [ ] Metrics logged (Analytics Bot)
---

Fields:
- Brand: [Select]
- Content Type: [Select]
- Assigned Bot: Content Manager
- Approval Status: Pending Security Review
- Due Date: [Pick date, 24 hours before publish]
```

**Template 2: Paid Ads Campaign**

```
Task Name: [Brand] - Ad Campaign - [Objective] - [Start Date]
Example: "Lucky 13 - Awareness Campaign - Foot Traffic - April 1"

Description:
---
**Campaign Brief:**
- Objective: [Awareness/Traffic/Conversions]
- Target Audience: [Description]
- Budget: $[amount]
- Duration: [Start → End date]
- ROAS Target: [e.g., 1.5:1]

**Deliverables:**
- [ ] Audience definition finalized
- [ ] 3 creative variations created (Visual Designer)
- [ ] Copy written (Copywriter)
- [ ] Campaign set up in Meta Ads Manager
- [ ] Pixel implemented
- [ ] A/B test configured
- [ ] Campaign launched
- [ ] Daily monitoring (Paid Ads Bot)
- [ ] Weekly optimization report (Analytics Bot)

**Success Criteria:**
- ROAS ≥ [target]
- Cost per action < $[amount]
- Landing page conversion rate > [%]
---

Fields:
- Brand: [Select]
- Content Type: Ad Creative
- Assigned Bot: Paid Ads
- ROAS Target: [number]
- Approval Status: Pending Dan Approval
- Due Date: [Date campaign launches]
```

**Template 3: Analytics & Reporting**

```
Task Name: [Brand] - Weekly Report - Week of [Date]
Example: "Vegan Table - Weekly Report - Week of March 24"

Description:
---
**Metrics to Pull:**
- Total reach
- Impressions
- Engagement rate
- Click-through rate
- Conversions (if applicable)
- Customer sentiment (comments)
- Top-performing post
- Bottom-performing post

**Report Sections:**
1. Executive summary (1 sentence)
2. Key metrics (table)
3. Top performer (screenshot + why it worked)
4. Bottom performer (screenshot + improvement plan)
5. Recommendations for next week

**Deliverables:**
- [ ] Data pulled from Meta Insights
- [ ] GA4 data (if applicable)
- [ ] Report written
- [ ] Sent to Dan (via Asana comment)

---

Fields:
- Brand: [Select]
- Content Type: Reporting
- Assigned Bot: Analytics
- Approval Status: Approved
- Due Date: [Friday, end of week]
```

---

## STEP 5: CREATE TASK TEMPLATES IN ASANA (Reusable)

**In Asana:**
1. Click **+ New task**
2. Fill in fields (use templates above as reference)
3. After creating, click **...** menu (top right)
4. Select **Save as template**
5. Name: `Social Media Content` / `Paid Ads Campaign` / `Analytics Report`
6. Repeat for each template

Now you can spawn new tasks from these templates instantly.

---

## STEP 6: SET UP CUSTOM WORKFLOW (Automation) (Optional but helpful)

**Automation Rules:**

**Rule 1: Auto-move to Approved**
- When: Task in "Review" section AND "Approval Status" = "Approved"
- Then: Move to "Approved" section

**Rule 2: Auto-assign to Community Manager**
- When: Task in "Approved" section
- Then: Assign to Community Manager Bot

**Rule 3: Auto-move to Done**
- When: Subtask "Posted" = Complete AND 24 hours have passed
- Then: Move to "Done" section

**How to set up:**
1. Click **Customize** (top right)
2. Click **Rules** (bottom)
3. Click **+ Create rule**
4. Select trigger (When X)
5. Select action (Then Y)
6. Save

---

## STEP 7: CREATE THE WORKFLOW EXAMPLE (2 minutes)

**Create one test task** to make sure everything works:

```
Task: "Test — Vegan Table — Instagram Post — March 24"

Description:
Post idea: Beautiful plant-based dish with wellness message

Subtasks:
- [ ] Content brief
- [ ] Copy written
- [ ] Graphics (3 variations)
- [ ] Security review
- [ ] Dan approval
- [ ] Post
- [ ] Monitor engagement

Fields:
- Brand: Vegan Table
- Content Type: Feed Post
- Assigned Bot: Content Manager
- Approval Status: Pending Security Review
- Due Date: March 24
```

Move it through the workflow (Backlog → In Progress → Review → Approved → Done) to test.

---

## STEP 8: ADD BOT INTEGRATIONS (Optional, for Month 2+)

Asana has API integrations. Once you get API token, bots can:
- Create tasks automatically
- Update task status
- Pull task data
- Send notifications

**For now:** Manual Asana + bots reading task descriptions works fine.

---

## DAILY STANDUP CHECKLIST (Project Manager Bot uses this)

**Every morning (8 AM):**
1. Open Asana
2. Filter: Tasks in "In Progress" or "Review"
3. Check: Are any overdue?
4. Flag: If yes, ping owner
5. Summarize: Status update to Dan (2 minutes)

---

## WEEKLY RHYTHM

**Monday 8 AM:**
- Plan week (create tasks for 5 content pieces per brand)

**Tuesday-Thursday:**
- Bots work through tasks
- Move tasks through workflow

**Friday 4 PM:**
- Analytics Bot creates Weekly Report task
- Review performance
- Plan next week

---

## QUICK REFERENCE: Task Lifecycle

```
CREATION (Project Manager):
  Task created with all details filled

IN PROGRESS (Content/Design Bots):
  Subtasks checked off as work progresses

REVIEW (Security Bot):
  Security Bot reviews, approves or rejects

DAN APPROVAL (Dan):
  Approves or requests changes

APPROVED (Community Manager):
  Ready to post

SCHEDULED (Content Manager):
  Batched for scheduling

DONE (Analytics Bot):
  Posted + metrics tracked
```

---

## GETTING STARTED (Right Now)

1. Create Master Project (name: "Similan Agency — Master")
2. Create 6 sections (Backlog, In Progress, Review, Approved, Scheduled, Done)
3. Create 5 custom fields (Brand, Content Type, Assigned Bot, Approval Status, ROAS Target)
4. Create 1 test task (use Social Media Content template)
5. Move it through sections to test
6. Create task templates (reusable)

**Time: ~30 minutes.**

---

## QUESTIONS TO ANSWER BEFORE YOU START

1. **Team members:** Just you + bots, or are you adding humans? (affects permissions)
2. **Bot access:** Will bots read Asana via API, or just via task descriptions? (for now: descriptions)
3. **Daily standup:** Do you want a recurring "Daily Standup" task, or just check manually?

Once Asana is ready, we'll:
1. Verify API connection works
2. Test one campaign end-to-end (task → approval → publication)
3. Brief the bots

Ready?
