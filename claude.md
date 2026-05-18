# Project Constitution: My Salon Suite - Blaine

## Primary Goal
Maximize "Book a Tour" conversions. Every decision — copy, layout, imagery, email — serves this goal.

## Mindset
"A stylist lands here from a Google Ad and decides in 10–20 seconds if this is worth booking."

## Design Principles
- **Aesthetic**: Premium, clean, aspirational. Apple-level spacing, Airbnb-style lifestyle imagery, high-end beauty brand feel.
- **Avoid**: Corporate stiffness, overloaded text, generic stock feel, agency-style fluff, extra navigation.
- **UX**: Mobile-first (70%+ traffic from ads). Fast loading. Clear visual hierarchy.
- **Ad Alignment**: Must align with "Salon suites Blaine", "Rent salon space near me".

---

## Repo Structure

```
/
├── index.html              — v1 landing page (READ ONLY — never modify)
├── index-v2.html           — v2 landing page (client-approved updates)
├── index-v2-direct.html    — old "Direct Response" variant (preserved reference)
├── styles.css              — v1 base styles (READ ONLY — never modify)
├── styles-v2.css           — v2 additive styles only (no overrides to styles.css)
├── Blaineimages/           — original numbered images (1.jpg–9.jpeg) used in v1
├── blaine-photos/          — properly-named Drive images (use these in v2)
│   ├── Decorated Salon Suite.jpg
│   ├── Decorated Salon Suite_2.jpg
│   ├── Decorated Salon Suite_3.jpg
│   ├── Decorated Spa Suite.jpg
│   ├── Decorated Spa Suite_2.jpg
│   ├── Blank Salon Suite.jpg
│   ├── Lobby.jpg
│   ├── Client Lounge.jpg
│   ├── Decorated Salon Suite and Hallway.jpg
│   ├── Storefront.jpg
│   └── Storefront Logo.jpg
├── before-after/           — before/after transformation pairs (pairs 1–6)
│   ├── 1 - Before.jpg / 1 - After.jpg
│   ├── 2 - Before.jpg / 2 - After.jpg
│   ├── 3 - Before.jpg / 3 - After.jpg
│   ├── 4 - Before (spa).jpg / 4 - After (spa).jpg
│   ├── 5 - Before (spa).jpg / 5 - After (spa).jpg
│   └── 6 - Before.jpg / 6 - After.jpg
├── email/
│   ├── index.html          — interactive email viewer (v1/v2 toggle)
│   ├── 01–22-*.html/.txt   — v1 email sequences (READ ONLY)
│   └── v2/                 — v2 updated emails only
│       ├── 00-member-onboarding-html.html
│       ├── 01-tour-requested-html.html
│       ├── 02-tour-preparation-text.txt
│       └── 03-profit-visualization-html.html
```

---

## v1 vs v2 — What Changed

### Landing Page (index-v2.html vs index.html)

| Area | v1 | v2 |
|------|----|----|
| Hero background | Blurred CSS div | Real suite photo, no blur |
| Hero headline | Generic | "Own Your Space. Own Your Schedule. Keep Every Dollar." |
| Professions | 6 tags | 10 tags (+ Injectors, Eyelash Technicians, Tattoo Artists, Wellness Professionals) |
| USP headline | "Why My Salon Suite Blaine?" | "Why My Salon Suite?" |
| USP bullets | 3 generic | 4 updated: Free setup, Furnished, Community ("on your own but never alone"), Business resources |
| Blaine section | None | New 3-card section above USP with location photos |
| Comparison: MSS access | "24/7 Remote Access" | "100% Secure Access" |
| Comparison: Booth rental hours | Previous text | "Standard Salon Hours" |
| Section spacing | ~100px padding | 5–6rem padding |
| Gallery | Swiper carousel | Filtered grid (All, Decorated, Blank, Lobby, Exterior, Hallway, Lounge) |
| Before/After | None | img-comparison-slider web component |
| Images | Blaineimages/ numbered files | blaine-photos/ named Drive files |

### Emails (email/v2/ vs root email files)

| Email | Key Changes |
|-------|-------------|
| 00 — Onboarding (NEW) | Consolidated from Stacey + Kayley templates; checklist, app links, handbook links |
| 01 — Tour Requested | Added Calendly scheduling block + manager personalisation block |
| 02 — Tour Preparation | New intro line; removed suite-specific requirements paragraph |
| 03 — Profit Visualization | Reduced spacing; added Profit Calculator link |
| Global rule | No em dashes (`—`) in any v2 email — use `: ` or `, ` instead |

---

## Architectural Constraints

- **v1 is frozen**: `index.html` and `styles.css` must never be modified. They exist as the side-by-side reference for client comparison.
- **CSS pattern**: All v2 styles live in `styles-v2.css`. It is additive only — never imports or overrides `styles.css`.
- **No external JS libraries for gallery**: The filtered gallery uses pure vanilla JS (`filterGallery()`). Keep it that way.
- **Before/after slider**: Uses `img-comparison-slider` web component via CDN (`cdn.jsdelivr.net/npm/img-comparison-slider@8`). No npm install needed.
- **Form**: Embedded GHL form — must stay frictionless, no redirects. Payload fields: `name`, `phone`, `email`, `preferred_time`.
- **7 required sections**: Hero → Audience → Value → USP → Gallery → Testimonials → CTA. All must be present.

---

## Email Template Variables (GoHighLevel)

Used across all v2 emails. Map these in GHL contact fields:

| Variable | Description |
|----------|-------------|
| `{{name}}` | Prospect first name |
| `{{phone}}` | Prospect phone |
| `{{preferred_time}}` | Tour time window selected |
| `{{calendly_url}}` | Calendly booking link for this location manager |
| `{{manager_name}}` | Location manager name (Kayley or Stacey) |
| `{{manager_photo_url}}` | Headshot URL for manager personalisation |
| `{{manager_phone}}` | Manager direct phone |
| `{{manager_email}}` | Manager email address |
| `{{facebook_group_url}}` | Location-specific member Facebook group URL |

---

## Key Stakeholders

- **Rachel Kueppers** — Operations Manager, MSS Minnesota. Primary reviewer and feedback source.
- **Kayley** — Location manager (one location). Name and contact used in manager personalisation blocks.
- **Stacey** — Location manager (other location). Original onboarding email template author.

---

## Asset Sources

| Asset type | Source |
|------------|--------|
| Blaine location photos | Google Drive (downloaded to `blaine-photos/`) |
| Before/after pairs | Google Drive folder `1MwamZ_mAxqmdPjP0wJMcOqZLNbVLbdz7` (downloaded to `before-after/`) |
| MSS brand photos | `www.mysalonsuite.com/wp-content/uploads/` |
| Logo (SVG) | `https://www.mysalonsuite.com/wp-content/uploads/2025/06/logo-small.svg` |
| Community Handbook | `https://canva.link/cjbgkqr3nyyymdc` |
| Virtual Leasing Folder | `https://canva.link/4kmecnnm2pcobkj` |
| Document Upload Form | `https://docs.google.com/forms/d/e/1FAIpQLScKItqA1YFv1yhdm_9xK8a1s0mND3kddHGfjnannOdGB-DssQ/viewform` |
| Liability insurance vendors | `https://members.mysalonsuite.com/s/extras#section2` |
| MSS App (iOS) | `https://apps.apple.com/us/app/my-salon-suite/id1673785078` |
| MSS App (Android) | `https://play.google.com/store/apps/details?id=com.mysalesforce.mycommunity.C00D1I0000002oPcUAI.A0OT8W000000fxSMWAY` |
| ButterflyMX (iOS) | `https://apps.apple.com/us/app/butterflymx/id714133074` |
| ButterflyMX (Android) | `https://play.google.com/store/apps/details?id=com.butterflymx.butterflymx` |
| Profit Calculator | `https://www.mysalonsuite.com/profit-calculator/` |

---

## Email Sequence Map

### v1 Sequences (in `email/`)
| # | File | Type | Sequence |
|---|------|------|----------|
| 01 | 01-tour-requested-html.html | HTML | Tour |
| 02 | 02-tour-preparation-text.txt | Text | Tour |
| 03 | 03-profit-visualization-html.html | HTML | Tour |
| 04 | 04-brand-freedom-text.txt | Text | Tour |
| 05 | 05-lead-nurture-community-html.html | HTML | Tour |
| 06 | 06-guide-delivery-html.html | HTML | Guide |
| 07 | 07-guide-followup-text.txt | Text | Guide |
| 08 | 08-guide-tour-push-html.html | HTML | Guide |
| 09 | 09-evergreen-security-html.html | HTML | Evergreen |
| 10 | 10-evergreen-decor-text.txt | Text | Evergreen |
| 11 | 11-evergreen-client-exp-html.html | HTML | Evergreen |
| 12 | 12-evergreen-tax-benefits-text.txt | Text | Evergreen |
| 13 | 13-evergreen-final-push-html.html | HTML | Evergreen |
| 14 | 14-review-request-text.txt | Text | Member |
| 15 | 15-review-google-html.html | HTML | Member |
| 16 | 16-evergreen-tech-stack-html.html | HTML | Evergreen |
| 17 | 17-evergreen-education-text.txt | Text | Evergreen |
| 18 | 18-evergreen-all-pros-html.html | HTML | Evergreen |
| 19 | 19-evergreen-no-hidden-fees-text.txt | Text | Evergreen |
| 20 | 20-evergreen-quiz-html.html | HTML | Evergreen |
| 21 | 21-reactivation-timing-text.txt | Text | Reactivation |
| 22 | 22-reactivation-whats-new-html.html | HTML | Reactivation |

### v2 Emails (in `email/v2/`)
| # | File | Trigger |
|---|------|---------|
| 00 | 00-member-onboarding-html.html | New member signed lease |
| 01 | 01-tour-requested-html.html | Tour form submitted |
| 02 | 02-tour-preparation-text.txt | 24h before tour |
| 03 | 03-profit-visualization-html.html | Day after tour, no booking |

---

## Data Schemas

(Refer to `gemini.md` for specific GHL payload definitions and IO shapes)
