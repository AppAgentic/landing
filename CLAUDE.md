# App Agentic Landing Page

## Overview
Minimal, mysterious pre-launch landing page for App Agentic. Dark, techy, premium aesthetic (Apple-meets-cyberpunk). Pure static site with no dependencies or build step.

## Tech Stack
- **HTML/CSS/vanilla JS** -- zero dependencies
- No framework, no npm, no build tools
- Single `index.html` file contains everything (styles inline, JS inline)

## File Structure
```
Landing/
  index.html      # The entire landing page (HTML + CSS + JS)
  CLAUDE.md       # This file
  .gitignore      # Standard Node gitignore (from repo init)
```

## Design Tokens
| Token | Value | Usage |
|-------|-------|-------|
| `--bg` | `#0a0a0a` | Page background |
| `--surface` | `#111111` | Input/card backgrounds |
| `--border` | `#1a1a1a` | Subtle borders |
| `--text` | `#e0e0e0` | Primary text |
| `--text-dim` | `#555555` | Secondary text, brand name |
| `--accent` | `#4fffff` | CTA button, shimmer highlight, particles |

## Animated Elements
1. **Shimmer text** -- hero headline cycles a cyan highlight across the text via `background-position` animation
2. **Ambient orbs** -- three large blurred gradient circles drift and pulse behind the content
3. **Particles** -- 30 small dots float upward at varying speeds (pure CSS animation, JS-generated elements)
4. **Hero glow** -- radial gradient behind the headline pulses in and out

## Responsive Behavior
- Hero text uses `clamp(2.2rem, 6vw, 3.8rem)` for fluid scaling
- On mobile (<480px), the signup form stacks vertically (email input above button)
- Content max-width is 680px, centered

## Email Form
- Client-side only -- no backend wired up
- On valid email submission, the form transitions to a "You're on the list" confirmation state
- To connect a backend: intercept the button click handler in the inline `<script>` and POST to your endpoint

## Font
- Uses Google Fonts `Inter` with system font fallback stack
- Weights loaded: 300 (hero), 400 (tagline), 500 (brand), 600 (CTA button)

## Favicon
- Inline SVG data URI in the `<link rel="icon">` tag -- a minimal concentric circle mark in cyan on dark

## Deployment
- Any static host works: GitHub Pages, Netlify, Vercel, Cloudflare Pages, S3+CloudFront
- No build step needed -- just serve the directory

## Git
- Remote: `https://github.com/AppAgentic/landing.git`
- Branch: `main`
