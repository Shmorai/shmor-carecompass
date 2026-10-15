# CareCompass (carecompass.shmor.ai)

A Shmor marketplace (shared rules in `../../CLAUDE.md`): its own brand, design and SEO. Find US dentists, cosmetic surgeons and private clinics offering free consultations, with every insurance plan explained. Repo: `Shmorai/shmor-carecompass` (private until launch). Status: **building**.

## Where things are
| What | Where |
|---|---|
| Card on shmor.ai, search keywords, **referral links**, offers, SEO defaults | `shmor-site.json` |
| Pages (1 JSON file = 1 Google landing page) | `content/` (`home.json` = homepage) |
| Design: header, logo, footer | `templates/layout.html` |
| Design: styles | `assets/site.css` (kit defaults; add this site's theme block at the bottom) |
| Generated output (don't edit by hand) | `index.html`, `*/index.html`, `sitemap.xml`, `robots.txt`, `404.html`, `search/` |

## Design
"Clinical calm" (built 2026-10-15): warm white pages #FBF8F6, deep navy ink #13213F (top bar, CTA band, footer), rose #C93A5E (buttons, wordmark "Compass"; card/logo rose #FF8FA3), teal #0E7C74 ("Free consult" header button, links, free/insurance badges). Fonts: Fraunces (display serif) + Inter. Logo = compass (rose north needle, white south) in a navy rounded square + "Care**Compass**" + "by Shmor.ai" pill. Navy top bar: "Free consultations · Every insurance plan explained · Independent". Hero photos get a navy gradient overlay; homepage hero has badge pills (`heroHtml`, class `cc-badges`). Footer carries a medical disclaimer (not a provider/insurer, call 911 in emergencies). Header "Free consult" button hides below 400px. Checked at 320/375/768/1024/1280 (no horizontal scroll).

## Positioning (important)
The user asked to "showcase free appointments and all insurance taken". CareCompass is a guide, not a clinic, so it must not claim to accept insurance or give appointments itself. Wording used: "Free consultations" (how to find/book them at practices) and "Every insurance plan explained / all insurance welcome" (guides for every plan type). Keep it that way, and never invent clinics, prices, reviews or stats.

## Pages (36)
Home · free-consultations · insurance · dentists · dental-implants · teeth-whitening · clear-aligners · emergency-dentist · cosmetic-surgery · botox-fillers · private-healthcare · blog (+24 posts).
Menu: Free consults, Insurance, Dental care, Cosmetic surgery, Private care, Health news.

## Blog (/blog/, menu "Health news")
24 posts (2026-09-20 → 2026-10-15) on US healthcare news + dental/cosmetic guides: Medicare OE 2027, ACA OE 2027, ACA subsidies, Medicaid work requirements, drug price negotiation 2027, Part D cap, HSA changes, No Surprises Act, medical debt, Medicare dental, dental insurance, savings plans, low-cost dental, kids/CHIP, fluoridation, compounded GLP-1s, choosing a plastic surgeon, medical tourism, med spa safety, Medicare telehealth, urgent care vs ER, price transparency, consultation checklist, aligners vs braces.
**Backlinking:** every post's `related` = 3 other posts (same topic first, then date neighbours) + 1 landing page; posts also link to each other and to landing pages inline; landing pages link to posts via `related` and prose; homepage shows the 6 newest (`latestPosts: 6`). Keep this pattern for new posts.
Dated facts (as of 2026-10-15): Part D cap $2,400 (2027), deductible $700; Medicare OE Oct 15–Dec 7 2026; HealthCare.gov OE Nov 1 2026–Jan 15 2027 (Dec 15 for Jan 1 start; window length was litigated); enhanced ACA credits expired end-2025, no extension enacted; Medicaid work requirements from Jan 1 2027 (CMS IFR June 2026); 2027 HSA limits $4,500/$9,000; Medicare telehealth flexibilities through Dec 31 2027. Re-check these on each refresh and bump `updated`.

## Commands (run here)
```bash
node tools/build.js           # rebuild after ANY change to content/, templates/ or shmor-site.json
node tools/serve.js <port>    # local preview (see the "carecompass" preview config)
```
After changing `shmor-site.json`, also run `node tools/sync-network.js` in `../../shmor-ai`.

## Referral links
Add to `shmor-site.json` → `"links"`, list slugs in a page's `"partners"` (or add `"offers"`), rebuild, sync the master, then commit both repos.
