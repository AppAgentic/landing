# App Agentic Landing Page

## Overview
Public company website for App Agentic (legal name App Agentic Ltd), a software studio with live products. Dark, premium, technical aesthetic (Apple-meets-cyberpunk). Pure static site, no dependencies or build step.

It was expanded from a single-screen "teaser" into a full, scrollable multi-section site after Apple **withdrew a Developer Program enrollment for "minimal content."** The page now provides the public substance Apple expects: a clear company/product explanation, concrete areas of work, contact/support paths, and a privacy policy + terms of use. **Do not regress it back to a one-liner teaser** — keep the substantive content sections.

## Tech Stack
- **HTML/CSS/vanilla JS** -- zero dependencies
- No framework, no npm, no build tools
- Static HTML/CSS. `index.html` contains the homepage styles inline; `privacy.html` and `terms.html` share `legal.css`.

## File Structure
```
Landing/
  index.html      # Homepage (HTML + CSS + small cosmetic JS)
  privacy.html    # Standalone website Privacy Policy
  terms.html      # Standalone website Terms of Use
  legal.css       # Shared styling for standalone legal pages
  .well-known/security.txt  # RFC 9116 security contact (security@appagentic.dev); renew Expires before 2027-10-05
  .nojekyll       # REQUIRED: Pages uses the legacy Jekyll build, which drops dot-folders like .well-known without this
  CLAUDE.md       # This file
  .gitignore      # Standard Node gitignore (from repo init)
```

## Page Structure (sections, all anchor-linked from the nav)
1. **Hero** (`#top`) — headline "Software for the agentic era", one-paragraph explanation, CTAs, orbital agent graph.
2. **About** (`#about`) — who we are, what AI-native means, current status. Sidebar of company facts (company App Agentic Ltd, HQ, founded, status, contact).
3. **Products** (`#products`) — cards linking to live App Agentic products: ClipSubtitles, SlideTok, SeedViral, App Listing Agent, AppRefer, MuseAIConnectors, StoryCrest. Descriptions mirror each product's own homepage meta description.
4. **What we build** (`#work`) — 4 cards: areas of work (agent-native apps, mobile, agent infrastructure, applied research).
5. **Approach** (`#approach`) — 4 principles (design first, privacy by default, human in the loop, built to last).
6. **Contact & support** (`#contact`) — mailto links for general / support / privacy / security, plus location.
7. **Legal** (`#legal`) — concise directory linking to the standalone legal pages.
8. **Footer** — brand, company/contact/legal link columns, copyright.

## Legal Pages
- `privacy.html` is the standalone website privacy policy (data collected, cookies, rights, retention).
- `terms.html` is the standalone informational-site terms of use.
- Keep legal documents on their own pages. Apple specifically questioned site substance/minimal content, and standalone legal URLs make the public website easier to review and reference.

## Content Truthfulness Rules (important)
- Status (updated 2026-09-24): App Agentic has **live products** (see `#products`). Only list a product after confirming the repo is in the AppAgentic GitHub org, the site is live, and its legal pages don't name a different entity or conflict with a UK company. StoryCrest was added 2026-10-05 (Joe approved; its site gains an "operated by App Agentic Ltd" line) for Meta Muse connector business verification, which needs the company site consistent with product sites.
- Never claim customers, funding, user counts or other metrics.
- The previous version contained **fabricated metrics** (uptime %, "agents online", latency, version numbers, marquee). These were removed because they are misleading and were a likely factor in the App Store rejection. **Do not reintroduce fake telemetry.**
- Keep claims verifiable. Product descriptions come from each product's own live homepage.
- Legal name is **App Agentic Ltd** (same as SeedViral's `LEGAL_NAME`). Never publish the registered address or company number (Joe, 2026-09-14). "Manchester, United Kingdom" is the public location.

## Design Tokens (CSS custom properties in `:root`)
| Token | Value | Usage |
|-------|-------|-------|
| `--bg` | `#0a0a0c` | Page background |
| `--bg-elev` | `#111114` | Card hover, elevated surfaces |
| `--border` / `--border-mid` | white @ 6% / 12% | Hairlines, card borders |
| `--text` / `--text-mid` / `--text-dim` | `#e8e8ed` / `#9a9aa5` / `#62626b` | Text hierarchy |
| `--accent` | `#63dce3` | CTA, shimmer, particles, links |
| `--warn` | `#f4c47a` | Amber accent node |
| `--maxw` | `1180px` | Content max width |
| `--pad-x` | `clamp(1.25rem, 5vw, 5rem)` | Horizontal gutters |

## Fonts (Google Fonts)
- `Geist` (sans, body/headings), `Geist Mono` (labels, nav, mono UI), `Instrument Serif` (italic accent words in headings).

## Animated / Decorative Elements
- **Shimmer** on the serif accent word in the hero headline.
- **Ambient orbs** — 3 blurred gradient circles, `position: fixed`, drift behind content.
- **Particles** — JS-generated cosmetic dots (`#particles`), skipped under `prefers-reduced-motion`. Page is fully readable without JS.
- **Orbital graph** — SVG with rotating orbits + pulsing nodes (decorative, `aria-hidden`).
- **Scan line** in eyebrow labels and chapter markers.
- Hero copy uses fade-up entrance animations that **end in the visible state** (`forwards`), so content is never permanently hidden.

## Accessibility / No-JS / Apple-review constraints
- All substantive content is in normal document flow and visible **without JavaScript** and **without scroll-triggered reveals** (no IntersectionObserver). This was deliberate so a reviewer (or crawler) sees full content immediately.
- `prefers-reduced-motion` disables animations and smooth scroll.
- Decorative SVGs/layers are `aria-hidden`.

## Responsive Behavior
- Hero is a 2-col grid that collapses to 1 col below 900px (graph moves above copy).
- Card/principle grids collapse to single column below 900px.
- Nav section links hide below 860px; brand + "Contact" CTA always remain.

## Assumptions to verify before launch
- **Email domain `appagentic.dev`** (hello@ / support@ / privacy@ / security@) is assumed from the AppAgentic browser-profile email. Confirm these mailboxes exist / forward, or swap to the real support address.
- **Company name** rendered as "App Agentic" (no legal entity suffix like Ltd). Add the registered entity name + company number/address if one exists — Apple looks favourably on a verifiable legal entity.
- **Location** stated as "Manchester, United Kingdom". Keep this aligned with Apple enrollment details.
- **Founded 2025** — Companies House: APP AGENTIC LTD incorporated 5 May 2025 (JSON-LD `foundingDate` 2025-05-05). Footer copyright year is the current year, not the founding year.

## Deployment
- Any static host: GitHub Pages, Netlify, Vercel, Cloudflare Pages, S3+CloudFront. No build step.

## Git
- Remote: `https://github.com/AppAgentic/landing.git`
- Branch: `main`

## SEO (added 2026-09-24)
- GitHub Pages serves `main` at `https://appagentic.dev` (www 301s to apex). Merging to `main` publishes immediately.
- `robots.txt` (allow all) and a static `sitemap.xml`. `lastmod` is the date each page's content last changed: update it only when you edit that page.
- Every page has a self-canonical (`https://appagentic.dev/`, `/privacy.html`, `/terms.html`), OG/Twitter tags and `og-image.png` (1200x630).
- `index.html` `<head>` has Organization JSON-LD (legalName App Agentic Ltd, locality only, `sameAs` = the GitHub org, the only confirmed profile), WebSite, and an ItemList of the products. Keep the ItemList in sync with the visible Products section.
- Add no `sameAs` profile you haven't confirmed exists and is ours. LinkedIn, X and Crunchbase were unconfirmed as of 2026-09-24.
