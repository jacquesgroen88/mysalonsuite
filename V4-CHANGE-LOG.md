# MySalonSuite — V4 Change Log
**Date:** 2026-06-17  
**Source:** Rachel's Content Review Doc (6/15, 6/10, 6/3) + email file audit  
**Working folder:** `/email/v4/`  
**V3 preserved at:** git tag `v3-delivered-2026-06-17` + `/email/` (untouched)  
**V4 viewer:** `/email/v4/index.html`

---

## Version Control Structure

| Path | What it is |
|---|---|
| `/email/` | V3 — delivered to Rachel. FROZEN. Do not edit. |
| `/email/v4/` | V4 working files — all edits happen here |
| git tag `v3-delivered-2026-06-17` | Permanent snapshot of V3 state |

---

## Global Changes (apply to every email)

| Rule | Detail |
|---|---|
| Em dashes | Only email 05 has one (testimonial attribution "— Rebekah"). Remove or replace with a comma/line break. Scan all HTML files for `—` before deploying. |
| Semi-colons | Audit all text emails for semi-colons and rewrite as separate sentences. |
| Exclamation marks | Read through each email and add where energy should be higher — especially in subject lines and CTAs. |
| Sign-off names | Personalise based on location. Blaine leads → Stacey Cleveland. Apple Valley / Bloomington / Chanhassen leads → Kayley Mundis. Text emails currently say "The My Salon Suite Team - Blaine" — change to manager name + title. HTML emails need a manager sign-off block added. |
| Placeholders | Email 02 still has `[Insert Address]`, `[Insert Phone]`, `[Your Name]`, `[Phone Number]` — fill in Stacey's details for Blaine (1341 113th Ave NE, Blaine MN 55434 / 612-429-6360). |

---

## Per-Email Change Log

### 01. Tour Requested — HTML
**File:** `01-tour-requested-html.html`  
**Current photo:** `content-with-links-01.jpg`  
**GHL vars:** `{{name}}`, `{{preferred_time}}`, `{{phone}}`  
**Changes:**
- Swap hero image → `Decorated Salon Suite_4.jpg` (from shared Drive)
- Stacey is called three different things in the same email ("relationship manager", "manager", "suite specialist") — pick one title and make it consistent throughout. Rachel's confirmed title is Member Relationship Manager.
- Change "we're checking the schedule" phrasing to: "we're checking the schedule to make sure..."
- Remove the "If you'd rather we reach out directly" section — fold its intent into the opening paragraph instead
- Add Stacey's name + title to sign-off block (not currently personalised)
- Add at least one more exclamation mark

**Calendly note:** Rachel wants the tour request to sync with Calendly so leads can book a time slot immediately. This is pending the Calendly URL from Rachel — wire it in once received.

---

### 02. Tour Preparation — TEXT
**File:** `02-tour-preparation-text.txt`  
**Rachel's rating:** "Good to go!" (6/10 notes) — approved as-is for copy  
**Changes:**
- Fill in Blaine-specific details replacing all placeholders:
  - `[Insert Address]` → 1341 113th Ave NE, Blaine, MN 55434
  - `[Insert Phone]` → 612-429-6360
  - `[Your Name]` → Stacey Cleveland
  - `[Phone Number]` → 612-429-6360
- Reword: "Here are a few quick details as you prepare for your visit:" (Rachel's 6/10 note)
- Remove: "If you have any specific requirements for your suite (like extra storage, specific lighting, or neighbors you'd like to be near), feel free to let me know beforehand." (Rachel flagged this)

---

### 03. Profit Visualization — HTML
**File:** `03-profit-visualization-html.html`  
**Current photo:** `haircut.webp`  
**GHL vars:** `{{name}}`  
**Changes:**
- Re-center the top hero photo so both faces are visible on desktop AND mobile (currently crops unevenly)
- Remove extra spacing above "Stop Splitting Your Success" headline and around the "100%" stat box
- Add profit calculator link: https://www.mysalonsuite.com/profit-calculator/

---

### 04. Brand Freedom — TEXT
**File:** `04-brand-freedom-text.txt`  
**Changes:**
- Fill placeholder: `[Your Name]` → Stacey Cleveland, `[Phone Number]` → 612-429-6360
- Open question from Rachel: "How will we make sure to update the suite availability?" — this needs a process answer before go-live (either dynamic GHL field or manual update cadence). Not a copy change but flag for Rachel on the call.

---

### 05. Community Profile — HTML
**File:** `05-lead-nurture-community-html.html`  
**Current photo:** `christina-01.jpg`  
**Em dash:** Yes — `"— Rebekah, Nail Artist"` in testimonial  
**Changes:**
- Swap photo → `Arielle.jpeg` (from shared Drive). Zoom/crop so there is no excess background space at top or sides.
- Remove the em dash in testimonial attribution. Change `"— Rebekah, Nail Artist"` to `"Rebekah, Nail Artist"` with a preceding comma or line break.
- Same suite availability question as email 04 — flag for Rachel.

---

### 06. Guide Delivery — HTML
**File:** `06-guide-delivery-html.html`  
**Current photo:** `haircut.webp`  
**GHL vars:** `{{name}}`, `{{guide_link}}`  
**Changes:**
- Swap hero image → `Generic Member.JPG` (Rachel's 6/15 note)
- Guide content decision: Rachel's options were (a) the Canva link, (b) the external startup list, or (c) focus on the profit calculator. **Recommended: use the profit calculator link as the primary CTA** since the guide doesn't fully exist yet. Update `{{guide_link}}` GHL field to point to https://www.mysalonsuite.com/profit-calculator/
- Remove "as requested" from intro (leads may not have actually requested anything) — rephrase naturally
- Remove "I'll check in with you in a few days" — replace with a simple "Have any questions? Just hit reply."
- Add Stacey sign-off

---

### 07. Casual Follow Up — TEXT
**File:** `07-guide-followup-text.txt`  
**Current sign-off:** "The My Salon Suite Team - Blaine"  
**Changes:**
- Change sign-off from "The My Salon Suite Team - Blaine" to Stacey Cleveland, Member Relationship Manager

---

### 08. Tour Push — HTML
**File:** `08-guide-tour-push-html.html`  
**Current photo:** `content-with-links-03.jpg`  
**GHL vars:** `{{name}}`  
**Changes:**
- Swap hero image → `Generic Member 2.JPG` (Rachel's 6/15 note)
- Change: "Can't make it this week?"
  → "Looking for a specific time? Shoot us a reply with a time that works best for you!"
- Add Stacey sign-off

---

### 09. Security Benefit — HTML
**File:** `09-evergreen-security-html.html`  
**Current photo:** `haircut.webp`  
**GHL vars:** `{{name}}`  
**Changes:**
- Swap hero image → location-specific lobby photo. For Blaine: `Lobby.jpg` (from shared Drive)
  - Note: This email will need location variants for the other 5 locations when scaling. Apple Valley/Plymouth/Bloomington → `Lobby.jpeg`. Rogers → `Lobby.jpg`. Chanhassen → `Lobby.jpeg`.
- Add `Security System - Call Box.jpg` in the "State-of-the-Art Security" section — **for Bloomington and Plymouth versions only** (not Blaine, AV, Rogers, Chanhassen)
- Reduce spacing between the hero photo and the title — too much gap currently
- Change all instances of "facility" → "Suites" (found in body and CTA button "Tour The Facility")
- CTA button: change "Tour The Facility" → "Tour The Suites"

---

### 10. Custom Decor — TEXT
**File:** `10-evergreen-decor-text.txt`  
**Current sign-off:** "The My Salon Suite Team - Blaine"  
**Changes:**
- Change: "Want to blast your own curated playlist instead of top 40 radio? You have the aux cord."
  → "Want to blast your own curated playlist instead of Christmas music on repeat? You have the control."
- Change sign-off → Stacey Cleveland, Member Relationship Manager
- Before/after photos: Rachel asked for 3 examples. This is a text email — add a line directing them to reply to request before/after photos, or consider converting to HTML to display them. Flag this decision with Jacques.

---

### 11. VIP Client Experience — HTML
**File:** `11-evergreen-client-exp-html.html`  
**Current photo:** `christina-01.jpg`  
**GHL vars:** `{{name}}`  
**Changes:**
- Swap hero image → `Client - Hair.JPG` (Rachel's 6/15 note)
- Find and change "roar" → "sound" (in body copy re: music)
- Find and change "demographic" → "clients"
- Find and change "high-end stylist equipment" → "high-end furniture"

---

### 12. Tax Benefits — TEXT
**File:** `12-evergreen-tax-benefits-text.txt`  
**Current sign-off:** "The My Salon Suite Team - Blaine"  
**Changes:**
- Remove the three write-off bullet examples:
  - "That expensive specialized treatment you want to offer? Write it off."
  - "The complimentary beverages you provide to your VIP clients? Write it off."
  - "The cost of your suite rental itself? Write it off."
- Replace with:
  - Stride Tax app paragraph: "And you won't have to figure it out alone. Every My Salon Suite member gets free access to the Stride Tax app, which helps you understand your tax obligations, track and maximize your deductions year round, and lower your tax bills. Quarterly taxes, multiple income streams, and deductions stop being a guessing game."
  - Add: "We also have a trusted tax professional we can refer you to, and recorded webinars with her are at your fingertips to help you prepare for tax season."
- Change sign-off → Stacey Cleveland, Member Relationship Manager

---

### 13. Final Check-In — HTML
**File:** `13-evergreen-final-push-html.html`  
**GHL vars:** `{{name}}`  
**No photo currently.**  
**Changes:**
- Position change only: In V4 sequence, this email moves to AFTER emails 23–25 (Business Resources). Already reflected in v4 index.html sidebar order.
- Copy update: Rachel noted "Would be nice to have already sent the business resources sequences and include that as something we've sent them." Add a line referencing what's been shared (profit math, security, decor, tech, business resources) before the close.
- CTA: "Schedule A No-Pressure Tour" — keep as is, this works.

---

### 14. Check-In — TEXT (Current Member Sequence)
**File:** `14-review-request-text.txt`  
**Current sign-off:** "The My Salon Suite Team - Blaine"  
**Changes:**
- Find and change "drop a quick line" → "check in"
- Find and remove "of bookings" (Rachel flagged)
- GHL scheduling: set to send on a Monday (workflow setting, not copy change)
- Change sign-off → Stacey Cleveland, Member Relationship Manager

---

### 15. Review Request — HTML (Current Member Sequence)
**File:** `15-review-google-html.html`  
**GHL vars:** `{{name}}`, `{{google_review_link}}`  
**No hero image — decorative stars only.**  
**Changes:**
- Add a sentence explaining the benefit to the member: "The more Google reviews we have, the higher we rank when potential clients are searching for services to book near them — which means more visibility for your suite and your chair."
- This reinforces it's in their interest, not just a favour to MSS.

---

### 16. Tech Stack — HTML
**File:** `16-evergreen-tech-stack-html.html`  
**Current photo:** `content-with-links-01.jpg` (same as email 01 — consider swapping)  
**GHL vars:** `{{name}}`  
**Changes:**
- No specific copy changes from Rachel
- CTA "View Available Suites" — confirm this links correctly for each location
- Consider this the lead-in to the Business Resources sequence (emails 23–25 follow)

---

### 17. Business Education — TEXT
**File:** `17-evergreen-education-text.txt`  
**Current sign-off:** "The My Salon Suite Team - Blaine"  
**Changes:**
- No specific copy changes from Rachel
- Change sign-off → Stacey Cleveland, Member Relationship Manager

---

### 18. All Professionals — HTML
**File:** `18-evergreen-all-pros-html.html`  
**Current photo:** `haircut.webp`  
**GHL vars:** `{{name}}`  
**Changes:**
- Fix the "J" formatting issue in the title (likely a font/rendering artifact — check in browser)
- Add "and more!" to the list of professions at the end
- Tattoo artists: Blaine does NOT allow tattoo artists — ensure this profession is not listed for Blaine version

---

### 19. No Hidden Fees — TEXT
**File:** `19-evergreen-no-hidden-fees-text.txt`  
**Current sign-off:** "The My Salon Suite Team - Blaine"  
**Changes:**
- After the utilities list, add "etc." — Rachel noted there are more inclusions not listed
- Change sign-off → Stacey Cleveland, Member Relationship Manager

---

### 20. Top Funnel Quiz — HTML
**File:** `20-evergreen-quiz-html.html`  
**GHL vars:** `{{name}}`  
**No hero image currently.**  
**Changes:**
- Add hero photo → `Traci Ribbon Cutting.jpeg` (Rachel's 6/15 note — source from shared Drive)

---

### 21. Better Timing — TEXT (Reactivation)
**File:** `21-reactivation-timing-text.txt`  
**Current sign-off:** "The My Salon Suite Team - Blaine"  
**Changes:**
- Find and remove the phrase referencing "you mentioned..." (paraphrasing a reason they gave — may not apply)
- Find and remove "for the upcoming year" (only applicable near year-end)
- Change sign-off → Stacey Cleveland, Member Relationship Manager

---

### 22. What You Missed — HTML (Reactivation)
**File:** `22-reactivation-whats-new-html.html`  
**GHL vars:** `{{name}}`  
**No hero image currently.**  
**Changes:**
- Add hero image → `Group - Hallway 3.JPG` (Rachel's 6/15 note — source from shared Drive)
- Availability logic: Rachel flagged that this email should only send when suites are available. If a location is full, a waitlist variant should fire instead. This is a GHL workflow rule, not a copy change — flag for workflow build.

---

## New Emails to Write (Pending Rachel's Data)

### 23. Business Tools & Savings — HTML (NEW)
**File to create:** `23-business-tools-html.html`  
**Status:** PENDING  
**Blocked on:** Exact Square discount %, full vendor/partner list from Rachel  
**Content direction:** Highlight tangible savings available to members. Lead with Square discount. List all vendors with the actual benefit per vendor.

### 24. Product Partners & Revenue — HTML (NEW)
**File to create:** `24-product-partners-html.html`  
**Status:** PENDING  
**Blocked on:** Names of partner companies, what the income opportunities actually are  
**Content direction:** Explain how members can add income streams through product partnerships. Be specific — "Company X offers Y% commission on Z product."

### 25. Health, Wellness & Protection — HTML (NEW)
**File to create:** `25-health-wellness-html.html`  
**Status:** PENDING  
**Blocked on:** List of companies members get access to (health insurance, income protection, etc.)  
**Content direction:** Position this as a benefit traditional commission salons don't offer. Name the actual providers.

### 26. In Business for Yourself — HTML (NEW)
**File to create:** `26-community-html.html`  
**Status:** PENDING  
**Blocked on:** Jennifer.png (Blaine cosmetologist photo) from Rachel  
**Content direction:** Community sell. Main photo: `Group - Hallway.JPG`. Add site-specific member spotlight at bottom. For Blaine: Jennifer (cosmetologist, member since 2025, came from commission salon). Photo: Jennifer.png.

---

## Outstanding From Rachel (before V4 can be finalised)

| Item | Needed For |
|---|---|
| Calendly URL | Email 01 Calendly booking block |
| Square discount % | Email 23 |
| Vendor/partner list | Emails 23–25 |
| Partner company names (health/wellness) | Email 25 |
| Jennifer.png | Email 26 |
| Suite availability update process | Emails 04, 05, 22 |
| Confirmation that `lease-signed` GHL tag is created | Onboarding workflows |

---

## What Can Be Done Right Now (no blockers)

Emails 02, 03, 05, 06, 07, 08, 09, 10, 11, 12, 13, 14, 15, 18, 19, 20, 21 — all changes in Sections above can be applied immediately. Photos exist in the shared Drive album.

Email 01 — all changes except Calendly block can be done now.  
Email 22 — photo swap can be done now; availability logic is a workflow task.

---

## Deploy Plan

1. Apply all changes to files in `/email/v4/`
2. Commit: `feat(v4): apply Rachel feedback rounds 6/3, 6/10, 6/15`
3. Push to Netlify — v4 goes live at `https://mysalonsuite.netlify.app/email/v4/`
4. Send Rachel the v4 link for sign-off
5. Once emails 23–26 are written, update v4 index and push again
6. Final: upload all v4 HTML files to GHL templates

