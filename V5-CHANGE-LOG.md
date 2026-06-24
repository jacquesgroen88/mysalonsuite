# MySalonSuite — V5 Change Log / Build Spec

**Date:** 2026-06-24
**Source:** Rachel's Content Review doc — **6/18/26 + 6/22/26** rounds (the feedback added *after* v4 was delivered)
**Doc:** https://docs.google.com/document/d/1uI5fOwTB_8d54KdAZir95L5mTjCRhRr0lVF3aKM4Ps8/edit
**V4 frozen at:** git tag `v4-delivered-2026-06-18` (commit d434352)

---

## Versioning rule (so nothing is lost / overwritten)

| Layer | v4 (FROZEN — do not edit) | v5 (today's work) |
|---|---|---|
| Blaine landing | `index-v4.html` | `index-blaine-v5.html` |
| Location landings | `index-{loc}.html` (bare names) | `index-{loc}-v5.html` ×5 |
| Landing CSS | `styles-v4.css` | `styles-v5.css` (additive) |
| Emails | `email/v4/` | `email/v5/` (full copy of v4, then edit) |

- Flat `-v5` suffix chosen (matches existing `index-v4.html` pattern, single folder, clean `git diff`).
- Three ways to see the diff: (1) `git diff v4-delivered-2026-06-18` , (2) this change-log, (3) v5 toggle added to the email viewer + dashboard.

---

## Photo manifest — ALL confirmed downloadable, 5 new ones already pulled

Staged in `_new-photos-2026-06-24/` (byte-verified against Drive):

| File | Bytes | Destination folder | Used for |
|---|---|---|---|
| Laundry Room.jpg | 258,006 | `blaine-photos/` | Blaine location photos (add) |
| Double Suite.JPG | 362,663 | `blaine-photos/` | Blaine "Double Suite (Customized)" (add) |
| Kira 2.JPG | 546,126 | `apple-valley-photos/` | Apple Valley member quote |
| Tetyana 2.jpg | 2,626,670 | `bloomington-photos/` | Bloomington member quote |
| Butterfly.jpg | 277,701 | shared email asset | Email 09 security swap |

Already-local (export, byte-matched, also re-downloadable by Drive ID): Nikki Suite.jpeg, Tracee.jpg, Generic Member(.2), Client - Hair, Cient - Eyelashes 3, Traci Ribbon Cutting, Group - Hallway(.3), Jennifer.png, Mindy, Arielle, Decorated Salon Suite_4, Lobby (per-loc), Security System - Call Box, Suite Decor (local crop).

**No missing assets.**

---

## A. LANDING PAGES — applies to all 6 v5 pages unless noted

| # | Change | Note ref | Detail / before → after |
|---|---|---|---|
| A1 | **TRADEMARK FIX (do first)** | 6/18 | Replace "The Suite Life" phrase (1× per page, all 6) — trademarked by another franchise. Pick a safe replacement headline. |
| A2 | Suite-advantage photos → squares | 6/18 | Change the advantage-section images to square crops to cut scroll length. (Locate exact section heading at build.) |
| A3 | Spacing between transformation sliders | 6/18 / 6/3 | Add gap between the before/after sliders; consider two side-by-side. |
| A4 | Location-photos section edits | 6/18 | Remove close-up exterior logo photo. **Blaine:** add Laundry Room.jpg + Double Suite.JPG. |
| A5 | Member quotes + photos (real) | 6/18 | Add the 4 supplied member quote cards to the matching location page (see below). Center crop on face. |
| A6 | Keep "view available suites" wording | 6/18 | No change to that CTA label. |
| A7 | Gallery filter labels | 6/3 | "Suites (Decorated)" → "Suites (Customized)"; "Suites (Blank)" → "Suites (Blank Canvas)". Verify actual labels at build. |

### Member quote cards (A5) — place on the matching location page
- **Chanhassen** — Nikki: "Having my own suite means I offer only the services I want and carry the products I truly believe in, instead of following someone else's directives." (Nikki Suite.jpeg)
- **Bloomington** — Tracee: "I love the flexibility to create my own hours and make my own decisions. Everyone has noted how much happier I am, and a part of me wishes I had made this move years ago." (Tracee.jpg)
- **Apple Valley** — Kira: "I finally have the classy, private space I always envisioned, and the freedom to grow on my own terms." (Kira 2.JPG)
- **Bloomington** — Tetyana: "My own suite has allowed me to create a calm, private space where clients feel comfortable and cared for. It has truly elevated my services and my business." (Tetyana 2.jpg)

### Per-location config to confirm present (6/3)
- Furniture colour: Bloomington & Plymouth = dark brown (gray-box intercom); Apple Valley & Chanhassen = cream; Rogers & Blaine = white.
- "Why My Salon Suite ___" USPs per location (Blaine: Secure Access, Client Lounge, Location — etc.).
- Tattoo in services? Blaine no / Rogers yes / Apple Valley no / Chanhassen yes / Bloomington yes / Plymouth yes.

---

## B. EMAILS — copy v4 → v5, then apply (per 6/18)

| Email | Change |
|---|---|
| 01 Tour Requested | Fit text within border; keep "Member Relationship Manager" on one line; move Stacey photo above her bio. |
| 02 Tour Preparation | Add booked tour day/time. **BLOCKED:** how to pull from Calendly / manager calendar — needs Rachel answer. |
| 03 Profit Visualization | Add space between "Run Your Numbers" and "Book A Tour" buttons. |
| 05 Community Profile | Crop closer on face; add a real member quote + photo + location; "Only 3 Premium Suites Left" → "Limited Suites Available Now". |
| 06 Guide Delivery | Rename email to "Profit Calculator"; add Stacey photo; change "Something worth reading." to a run-your-numbers line; add stat: "3 in 4 Members report making more money in a salon suite; the 4th works fewer hours." |
| 07 Casual Follow Up | Pivot from guide → ask if they've run their numbers in the profit calculator. |
| 08 Tour Push | Reference running the numbers (profit calculator) instead of the guide; add Stacey photo. |
| 09 Security Benefit | Replace security-monitor photo with Butterfly.jpg. The current monitor photo is used for **Bloomington & Plymouth only**. |
| 14 Check-In | Subject → "Checking In!"; remove "Our whole goal at My Salon Suite Blaine is to make sure you have the perfect foundation..." sentence. |
| 16 Tech Stack | Three reworded headings: (1) Square partnership — flat 2.45% processing rate (vs 2.6% + $0.10 swipe) plus subscription discounts; (2) Liability insurance discounts — 3+ options at discounted pricing; (3) Marketing connections — exclusive Vistaprint promos + Salon S.O.S. tools. |
| 20 Top Funnel Quiz | Re-crop photo centered on the person + ribbon. |
| 23–25 Member Business Resources | Make concise (don't repeat full description each section; keep all partners). Move into the lease/member sequence. **BLOCKED:** exact Square %, vendor list, health-insurance providers. |
| 26 In Business For Yourself | Mobile view: center the words on the main picture. |

---

## C. Blocked on Rachel (carry to next call — do NOT hold the rest)
1. Calendly → pulling booked tour day/time into email 02.
2. Emails 23–25 specifics: exact Square %, recommended vendor list, health-insurance company names.
3. Suite-availability update process (recurring question, affects "view available suites" + reactivation logic).

---

## D. Build order
1. ✅ Tag v4 (`v4-delivered-2026-06-18`).
2. ✅ Download + byte-verify 5 new photos.
3. Move 5 staged photos into destination folders.
4. Scaffold v5: copy v4 landing pages → `-v5`, copy `email/v4/` → `email/v5/`, `styles-v4.css` → `styles-v5.css`.
5. Apply Section A (landing) — trademark fix first.
6. Apply Section B (emails).
7. Add v5 toggle to email viewer + dashboard.
8. Commit per workstream; push to Netlify; send Rachel the v5 link.

---

## E. BUILD STATUS — verified 2026-06-24

**Landing pages (all 6 v5):** trademark fix, styles-v5.css linked, square advantage photos (live: aspect-ratio 1/1), slider spacing, face-crop CSS. Blaine: logo close-up removed, Laundry Room + Double Suite added, Amenities filter. Member quotes live: Nikki (Chanhassen), Kira (Apple Valley), Tracee + Tetyana (Bloomington). All verified via grep + live render + image HTTP 200.

**Emails (v5):** 01 (photo above bio, title one line), 03 (button spacing), 05 (real member quote/photo + Limited Suites Available Now + face crop), 06 (renamed Profit Calculator + headline + 3-in-4 stat + Stacey photo), 07 (pivot to profit calculator), 08 (profit-calculator wording + Stacey photo), 09 (Butterfly.jpg swap), 14 (Checking In! + sentence removed), 16 (3 reworded headings), 20 (re-crop), 26 (mobile center). All verified.

**Dashboard:** V5 row + V5 location-pages section added.

### BLOCKED on Rachel (faithfully flagged, not fabricated)
- **Email 02** — added {{tour_datetime}} line; needs Calendly to GHL field mapping before go-live.
- **Emails 23-25 (Member Business Resources)** — "make concise + keep all partners" requires the exact Square %, vendor/partner list, and health-insurance provider names. Left as v4 content pending Rachel's data. Do NOT ship until provided.

### Not yet done (post-approval)
- Commit per workstream + push to Netlify (awaiting your go-ahead).
- Upload final v5 HTML to GHL templates.
---

## F. QA PASS 2 — caught + fixed after visual review (2026-06-24)

Two items were marked done on grep alone but were NOT actually correct on screen. Fixed and re-verified:

1. **Slider gap (A3) — was broken, now fixed.** .before-after-duo's side-by-side grid layout existed only under \ody.v3\; the v4/v5 pages are \ody.v4\, so the two transformation sliders were stacking flush (exactly Rachel's 6/18 complaint). \gap\ alone did nothing on a non-grid block. styles-v5.css now defines \ody.v4 .before-after-duo\ as a 2-col grid (gap 3rem desktop) collapsing to 1-col with 2.5rem gap on mobile. Verified live: desktop = 2 cols same row, 48px gap; mobile = stacked, 40px measured gap.

2. **Social links (6/18) — was missed entirely.** Rachel specified Instagram \mysalonsuite_mn\ for all emails + locations, and per-location Facebook URLs. Fixes:
   - All 6 location pages: Instagram \mysalonsuite/\ -> \mysalonsuite_mn/\.
   - Apple Valley Facebook: \mysalonsuiteapplevalley\ -> \mysalonsuiteapplevalleymn\ (was missing the "mn").
   - Email 01: Facebook generic \MySalonSuite\ -> \mysalonsuiteblaine\; Instagram -> \mysalonsuite_mn\.
   - Added a Facebook (Blaine) + Instagram (mysalonsuite_mn) line to every HTML email footer that lacked one (19 emails).

### Per-location config re-checked (6/3 carryover, confirmed correct in v5)
Tattoo profession: Blaine omitted (microblading instead), Apple Valley omitted, Rogers/Chanhassen/Bloomington/Plymouth included. Per-location "Why My Salon Suite {City}?" USP cards present.

### Flagged for cleanup (pre-existing, not a Rachel item)
- email/v5 has DUPLICATE 23/24/25 files (two naming variants each, inherited from v4). Resolve when emails 23-25 are finalised with Rachel's data.
- Email 09: Bloomington & Plymouth need a variant that keeps the Call Box photo (commented in 09; only the Blaine/generic set exists today).
---

## G. QA PASS 3 — full line-by-line audit vs pasted 6/18 notes (2026-06-24)

- **Emails 23-25 "make concise" — DONE (was wrongly deferred).** The emails already contained the partner data (Square 2.45%, the four insurers, VistaPrint, PBA, Salon S.O.S.; SalonInteractive, Jack Winn Pro, Brazilian Professionals, KAO/Goldwell, Sam Villa, Minerva, MeyerSPA, Cricket, KELA, Leaf and Flower; Empower, Malden, Stride, Ally). Trimmed every verbose description to a one-line partner + offer. All partners retained (verified).
- **Page titles bumped v4/JCE Media -> v5** on all 6 landing pages.
- **Removed 3 orphaned duplicate email files** (23-member-resources-tools, 24-member-resources-partners, 25-member-resources-protection) that the viewer never referenced.

### Remaining (genuinely needs Rachel, not buildable now)
- Email 02: confirm HOW to pull booked tour day/time from Calendly into GHL (the {{tour_datetime}} field is wired and waiting).
- "23-25 should be in the lease email sequence" — a GHL workflow placement, not an HTML change.
- Email 09 Bloomington/Plymouth Call Box variant — only when per-location email sets are produced.
- Internal note (security system varies by location) — intentionally NOT applied to emails, per Rachel's "do not update emails with this info".