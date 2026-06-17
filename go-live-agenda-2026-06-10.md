# Go-Live Meeting Agenda — Rachel / Jacques
**Wed June 10, 2026 · 9:30–10:15am SAST · Google Meet**
Prepared from: 3 call transcripts (Apr 2, Apr 23, May 28) + full email thread history

---

## 0. Context recap (30 sec)
We've moved from "build & review" into "launch." Blaine is the pilot; the rest of the
6 locations replicate once it's proven (per May 28 tiered-rollout strategy).

---

## 1. What's DONE since last call ✅ (lead with wins)
- **26 email templates** live in GoHighLevel with full HTML content (22 v1 + 4 v2)
- **v2 landing page** finished & hosted: `mysalonsuite.netlify.app/index-v2.html`
- **Manager data + headshots** integrated (Stacey for Blaine, all 6 locations on file)
- **4 GHL custom fields** created (preferred_time, calendly_url, guide_link, google_review_link)
- **Workflow build kit** ready: setup guide + AI-builder prompts for all 4 automations

---

## 2. GO-LIVE BLOCKERS — must resolve to launch Blaine 🔴

| # | Blocker | Owner | Status |
|---|---------|-------|--------|
| 1 | **Number porting / call forwarding** | Rachel + Diane | OPEN — Rachel chasing since Jun 9. RingCentral invoice received. Lead routing (text + call bridge) can't go live without this. |
| 2 | **Landing-page form is not wired to GHL** | Jacques | Form currently shows a popup but sends nothing. Needs connecting to a GHL inbound webhook so submissions create contacts + fire workflows. |
| 3 | **4 workflows not built yet** | Jacques + Rachel | Build kit ready; needs ~40 min in GHL UI (API can't create them). |
| 4 | **Calendly URL** still not provided | Rachel | Blocks the "Tour Requested" email booking button. |
| 5 | **`lease-signed` tag** not created | Stacey/Rachel | Onboarding + post-tour workflows depend on it. |

---

## 3. DECISIONS needed from Rachel today
1. **Launch scope** — Blaine-only pilot first, or push more locations at once?
   (Recommend: Blaine pilot → collect 1 month data → replicate. Matches May 28 validation plan.)
2. **Hosting domain** — go live on `blamysalons.com` subpages (per Apr 2 plan) or stay on
   Netlify for the pilot? DNS update needed if using the custom domain.
3. **Lead-response SLA** — confirm the Apr 2 model: immediate auto-text on inquiry +
   salesperson call-bridge ~50 min later. Who is the responder for Blaine? (Stacey?)
4. **Brand standards / "v3"** — Rachel sent brand standards Jun 3. Are there changes
   required BEFORE launch, or is current v2 approved to go live and v3 is a follow-up?
5. **Calendly** — can we get the Blaine booking link in this call so I wire it today?

---

## 4. PROPOSED GO-LIVE SEQUENCE (the actual launch path)
1. Rachel provides Calendly link + confirms launch domain → I wire the form to GHL (same day)
2. I build the 4 workflows in GHL using the prep kit (~40 min)
3. Stacey creates `lease-signed` tag + we map the form's time field
4. End-to-end test: submit form → contact created → email #1 arrives → confirm
5. Number porting completes (Rachel/Diane track) → enable text + call-bridge routing
6. Flip workflows Draft → Published → **Blaine is LIVE**
7. Begin 1-month performance data collection for validation

---

## 5. OPEN ITEMS carried over from prior calls (don't let these slip)
- **MOU / partnership formalization** (May 28) — status? Needed before multi-location rollout.
- **Location Drive folders** for the other 5 locations (May 28 action: Rachel to send) — needed to replicate.
- **NFC product collaboration / review-shield SaaS** (Apr 23) — park for post-launch?
- **Content strategist GPT + marketing calendar** (Apr 23 / Apr 2) — revisit after launch?
- **HD images 1920×1080** (Apr 2) — confirm all received in the Jun 3 shared album.

---

## 6. Suggested close / next steps
- Confirm the 5 decisions above
- Lock a target launch date for Blaine
- Schedule the porting-completion checkpoint with Diane
- Next standing call: same time next week to confirm Blaine is live + plan location #2

---

### Quick reference — links
- v2 Landing: https://mysalonsuite.netlify.app/index-v2.html
- Email viewer: https://mysalonsuite.netlify.app/email/
- Workflow setup guide: https://mysalonsuite.netlify.app/workflow-setup-guide.html
- Rachel's Content Review doc: https://docs.google.com/document/d/1uI5fOwTB_8d54KdAZir95L5mTjCRhRr0lVF3aKM4Ps8/edit
- Shared assets album: https://drive.google.com/drive/folders/1va_iUnM8B6OUvozqAtaTntzX73Vndy2N
