# CANVA SETUP GUIDE — Similan Agency

**Goal:** Set up Canva Team account with Brand Kits + templates for Visual Designer Bot to create designs at scale.

---

## STEP 1: CREATE CANVA TEAM ACCOUNT (5 minutes)

**In Canva:**

1. Go to **canva.com**
2. Click **Sign up** (if not already logged in)
3. Choose **Teams** (not personal account)
4. Name: `Similan Agency`
5. Plan: **Canva Teams** (~$120/year or $12/month, 5 team members included)
6. Click **Create team**

---

## STEP 2: SET UP BRAND KITS (ONE PER BRAND) (15 minutes)

A Brand Kit locks in colors, fonts, and logos so every design feels cohesive.

### **BRAND KIT 1: LUCKY 13**

**In Canva:**

1. Click **Brand kit** (left sidebar)
2. Click **+ New brand kit**
3. Name: `Lucky 13`
4. Description: `Fresh sandwiches, 5 locations, community-focused`

**Colors:**
- Primary: `#FF6B5B` (Coral — appetite, energy, warmth)
- Secondary: `#0A3A3A` (Teal dark — trust, local)
- Accent: `#f5d5a3` (Sand — warmth, approachable)
- Neutral: `#FFFFFF` (White)

**Fonts:**
- Headline: **Poppins Bold** (modern, friendly)
- Body: **Open Sans** (readable, clean)

**Logo:**
- Upload Lucky 13 logo (from `MASTER_ASSETS/BRAND_LOGOS/lucky13/logo.png`)
- Set as primary logo

**Save brand kit.**

### **BRAND KIT 2: VEGAN TABLE**

**Repeat steps 1–4, but fill in:**

- Name: `Vegan Table`
- Description: `Award-winning plant-based, wellness community`

**Colors:**
- Primary: `#6B8E23` (Sage green — nature, wellness)
- Secondary: `#f5f5f5` (Off-white — clean, premium)
- Accent: `#d4a574` (Warm brown — earthy, organic)
- Neutral: `#FFFFFF` (White)

**Fonts:**
- Headline: **Montserrat Bold** (elegant, premium)
- Body: **Inter** (modern, clean)

**Logo:**
- Upload Vegan Table logo

**Save brand kit.**

### **BRAND KIT 3: REALLY GOOD DELI**

**Repeat steps 1–4, but fill in:**

- Name: `Really Good Deli`
- Description: `10-year supplier, premium B2B + B2C, professional`

**Colors:**
- Primary: `#2c3e50` (Dark blue — professional, trustworthy)
- Secondary: `#ecf0f1` (Light gray — clean, premium)
- Accent: `#e74c3c` (Red — attention, urgency for deals)
- Neutral: `#FFFFFF` (White)

**Fonts:**
- Headline: **Roboto Bold** (professional, modern)
- Body: **Roboto Light** (elegant, readable)

**Logo:**
- Upload RGD logo

**Save brand kit.**

---

## STEP 3: CREATE DESIGN TEMPLATES (20 minutes)

Templates are pre-built layouts that Visual Designer Bot customizes. Create ONE template per platform, then duplicate + customize for each brand.

### **MASTER TEMPLATE 1: INSTAGRAM FEED POST (1080×1080)**

**In Canva:**

1. Click **+ Create a design**
2. Search for **Instagram Post** template (1080×1080)
3. Choose a clean, minimal template
4. **Customize:**
   - Delete all text (we'll add per-post)
   - Add your logo to corner (small, subtle)
   - Set background color to your primary brand color
   - Add 2–3 secondary color accent blocks (design elements)
   - Keep text areas open (copy added later)

5. **Name:** `[Brand] — Instagram Feed Post Template`
6. **Save to Canva** (not download yet)

**Duplicate 3 times** (one per brand):
- Lucky 13 — Instagram Feed Post Template
- Vegan Table — Instagram Feed Post Template
- RGD — Instagram Feed Post Template

Then customize each with brand colors + logo.

### **MASTER TEMPLATE 2: INSTAGRAM CAROUSEL (1080×1080 ×5)**

**Repeat:** Create 5-slide carousel template
- Slide 1: Hook (eye-catching)
- Slides 2–4: Progressive story
- Slide 5: CTA (call-to-action)

Save 3 versions (one per brand).

### **MASTER TEMPLATE 3: FACEBOOK POST (1200×628)**

**Repeat:** Create horizontal template
- Left side: Image area
- Right side: Text area + CTA button

Save 3 versions.

### **MASTER TEMPLATE 4: INSTAGRAM REEL THUMBNAIL (1080×1920)**

**Repeat:** Create vertical template
- Full-screen design
- Text safe area (center 80%, not edges)
- Hook-focused (first frame must stop scroll)

Save 3 versions.

### **MASTER TEMPLATE 5: EMAIL HEADER (1200×300)**

**Repeat:** Create horizontal header template
- Left: Image area
- Right: Brand color block + text space
- Responsive to mobile

Save 3 versions.

### **MASTER TEMPLATE 6: LINKEDIN ARTICLE THUMBNAIL (1200×628)**

**Repeat:** Create professional template
- Image area (product/professional context)
- Title text area
- Subtle branding

Save 3 versions.

---

## STEP 4: ORGANIZE CANVA WORKSPACE (10 minutes)

**Create folders for organization:**

1. **Folder: LUCKY_13**
   - Subfolder: Feed Posts
   - Subfolder: Carousels
   - Subfolder: Reels
   - Subfolder: Ads

2. **Folder: VEGAN_TABLE**
   - Same subfolders

3. **Folder: RGD**
   - Same subfolders

4. **Folder: TEMPLATES**
   - All template files organized here

5. **Folder: BRAND_KITS**
   - Nothing goes here (Brand Kits are in Brand Kit section)

**How to create folders:**
- Click **Folder icon** (left sidebar)
- Click **+ New folder**
- Name it
- Drag designs into folders as you create them

---

## STEP 5: SHARE TEAM ACCESS (5 minutes)

**In Canva:**

1. Click **Team settings** (top right)
2. Click **Members**
3. Invite team members (if any — optional for now)
4. Set permissions:
   - Editor (can edit designs)
   - Viewer (can only view)

For bots, we'll give **Editor** permissions later (via API integration in Month 2).

---

## STEP 6: ENABLE BRAND KIT AUTOAPPLY (2 minutes)

**In Canva:**

1. Click **Brand kit**
2. For each brand kit, toggle **Auto-apply brand kit**
3. When Visual Designer Bot selects this brand kit, colors/fonts auto-apply to new designs

---

## STEP 7: CREATE FIRST DESIGN (Test) (5 minutes)

**Test that everything works:**

1. Click **+ Create a design**
2. Choose **Instagram Post**
3. Select a template
4. Click **Apply brand kit** (top of editor)
5. Select **Lucky 13** brand kit
6. Colors + fonts auto-apply ✅
7. Add text: "Test Post"
8. Download or save
9. Name: `Test — Lucky 13 — Feed Post`
10. Save to LUCKY_13 → Feed Posts folder

---

## HOW VISUAL DESIGNER BOT USES CANVA

**Daily workflow:**

1. **Bot receives brief** from Content Manager (what to design)
2. **Bot opens Canva** (templates pre-built)
3. **Bot selects template** for platform (Instagram, Facebook, etc.)
4. **Bot applies brand kit** (auto-applies colors, fonts)
5. **Bot customizes:**
   - Uploads image/photos
   - Adds copy from Content Manager
   - Positions CTA button
   - Adjusts sizing for platform
6. **Bot creates 3 variations** (A, B, C)
7. **Bot saves** to folder (e.g., VEGAN_TABLE → Feed Posts)
8. **Bot exports** as PNG (transparent background)
9. **Submits** for approval

---

## CANVA TIPS FOR VISUAL DESIGNER BOT

**Speed hacks:**
- Use templates (don't design from scratch)
- Apply brand kit (auto-colors + fonts)
- Use stock photos (Canva has 100M+ free/paid)
- Duplicate designs (faster than creating new)
- Batch designs (5 at a time, similar layouts)

**Quality standards:**
- Export at 2x intended size (1080px becomes 2160px for high-quality)
- Use PNG for transparency (images with text overlays)
- Use JPG for photos-only (no text)
- Always check mobile view (how it looks on phone)

**Platform-specific settings:**

| Platform | Size | Export | Notes |
|----------|------|--------|-------|
| Instagram Feed | 1080×1080 | PNG | Square, high quality |
| Instagram Carousel | 1080×1080 ×5 | PNG | 5 separate files |
| Instagram Reel | 1080×1920 | MP4 | Video export |
| Facebook | 1200×628 | JPG | Horizontal, web-optimized |
| Email Header | 1200×300 | PNG | Responsive design |
| LinkedIn | 1200×628 | JPG | Professional aesthetic |

---

## DAILY STANDUP CHECKLIST (Visual Designer Bot)

**Every morning:**
1. Check Asana for new design briefs
2. Review Brand Kit colors + fonts (consistency check)
3. Open templates
4. Create 3 variations per brief
5. Save to correct folder
6. Export at correct resolution
7. Submit for approval
8. Log: Designs created, variations, status

---

## STORAGE & BACKUP

**Designs are stored in Canva.** To backup:
- Download finals as PNG/JPG
- Store in `PROJECTS/similan-agency/MASTER_ASSETS/DESIGNS/`
- Also commit to Git (version control)

---

## GETTING STARTED (Right Now)

1. Create Canva Team account (5 min)
2. Create 3 Brand Kits (15 min)
3. Create 6 design templates (20 min)
4. Organize folders (10 min)
5. Test 1 design (5 min)

**Total: ~55 minutes.**

---

## CANVA PRICING

- **Canva Teams:** ~$120/year or $12/month
- **Canva Pro:** ~$120/year or $12/month (individual)
- **Canva Teams > Canva Pro:** Better for collaboration + brand kits

Recommendation: **Canva Teams** (you + bots + any future team members).

---

## QUESTIONS BEFORE YOU START

1. Do you already have a Canva account? (If yes, we upgrade to Teams)
2. Do you have Vegan Table + RGD logos as PNG files? (Check: `MASTER_ASSETS/BRAND_LOGOS/`)
3. Any design preferences? (colors, style, templates to avoid?)

Ready?
