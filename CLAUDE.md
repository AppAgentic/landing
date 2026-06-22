# App Agentic Landing Page

## Overview
Public company website for App Agentic, a pre-launch software studio. Dark, premium, technical aesthetic (Apple-meets-cyberpunk). Pure static site, no dependencies or build step.

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
  CLAUDE.md       # This file
  .gitignore      # Standard Node gitignore (from repo init)
```

## Page Structure (sections, all anchor-linked from the nav)
1. **Hero** (`#top`) — headline "Software for the agentic era", one-paragraph explanation, CTAs, orbital agent graph.
2. **About** (`#about`) — who we are, what AI-native means, pre-launch status. Sidebar of company facts (HQ, founded, status, contact).
3. **What we build** (`#work`) — 4 cards: agent-native apps, mobile experiences, agent infrastructure, applied research. Framed as *areas of work*, not shipped products.
4. **Approach** (`#approach`) — 4 principles (design first, privacy by default, human in the loop, built to last).
5. **Contact & support** (`#contact`) — mailto links for general / support / privacy, plus location.
6. **Legal** (`#legal`) — concise directory linking to the standalone legal pages.
7. **Footer** — brand, company/contact/legal link columns, copyright.

## Legal Pages
- `privacy.html` is the standalone website privacy policy (data collected, cookies, rights, retention).
- `terms.html` is the standalone informational-site terms of use.
- Keep legal documents on their own pages. Apple specifically questioned site substance/minimal content, and standalone legal URLs make the public website easier to review and reference.

## Content Truthfulness Rules (important)
- The company is **pre-launch** — never claim live products, customers, funding, or metrics.
- The previous version contained **fabricated metrics** (uptime %, "agents online", latency, version numbers, marquee). These were removed because they are misleading and were a likely factor in the App Store rejection. **Do not reintroduce fake telemetry.**
- Keep claims to verifiable, generic descriptions of intent ("we are building…", "areas of work").

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
- **Email domain `appagentic.dev`** (hello@ / support@ / privacy@) is assumed from the AppAgentic browser-profile email. Confirm these mailboxes exist / forward, or swap to the real support address.
- **Company name** rendered as "App Agentic" (no legal entity suffix like Ltd). Add the registered entity name + company number/address if one exists — Apple looks favourably on a verifiable legal entity.
- **Location** stated as "Manchester, United Kingdom". Keep this aligned with Apple enrollment details.
- **Founded 2026** — adjust if incorrect.

## Deployment
- Any static host: GitHub Pages, Netlify, Vercel, Cloudflare Pages, S3+CloudFront. No build step.

## Git
- Remote: `https://github.com/AppAgentic/landing.git`
- Branch: `main`
