# Homework Day 4 — Branding, AI Creatives & Lovable
**Kasim Aslam — Delegation Masterclass Landing Page**
*Submitted by: Axel | April 4, 2026*

---

## Overview

The goal was to keep building Kasim Aslam's landing page for his 2-hour delegation webinar, and layer in a brand kit (logo, favicon, fonts, color palette) plus AI-generated graphics.

**Live page:** https://axeleonhardt639.github.io/paretoTalent/

---

## 1. Brand Kit

### Logo & Favicon

The logo wordmark and favicon were generated using **[favicon.io](https://favicon.io/)** — a free browser tool that creates full favicon sets from text + font combinations.

- **Font used for logo:** [Jomhuria](https://fonts.google.com/specimen/Jomhuria) (Google Fonts) — bold, distinctive, Mediterranean character. Chosen because it gives the "KA" initials a premium, editorial stamp feel that matches the dark luxury brand.
- **Favicon files generated:**

| File | Size | Use |
|---|---|---|
| `favicon_io/favicon.ico` | Multi-size ICO | Browser tab icon (all browsers) |
| `favicon_io/favicon-32x32.png` | 32×32px | Standard browser tab |
| `favicon_io/favicon-16x16.png` | 16×16px | Small browser tab |
| `favicon_io/apple-touch-icon.png` | 180×180px | iOS home screen icon |
| `favicon_io/android-chrome-192x192.png` | 192×192px | Android home screen icon |
| `favicon_io/android-chrome-512x512.png` | 512×512px | Android splash screen |
| `favicon_io/site.webmanifest` | — | PWA manifest (links all icons) |

All favicon files live in the `/favicon_io/` folder and are linked in the `<head>` of `index.html`.

---

### Fonts

Two fonts from **[Google Fonts](https://fonts.google.com/)**, one locally loaded via `@font-face`:

| Role | Font | Weight | Use |
|---|---|---|---|
| **Logo / Wordmark** | [Jomhuria](https://fonts.google.com/specimen/Jomhuria) | Regular | Logo mark only — "KA" initials in the nav/favicon |
| **Primary (Main)** | [Inter](https://fonts.google.com/specimen/Inter) | 400 · 500 · 600 · 700 · 800 · **900** | All headlines, body text, UI, buttons |
| **Secondary (Accent)** | [Playfair Display Italic](https://fonts.google.com/specimen/Playfair+Display) | 700 · 900 | Pull quotes, emotional emphasis lines — used sparingly |

**How they load in the page: promtp**
```html
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800;900
  &family=Playfair+Display:ital,wght@0,700;0,900;1,700
  &family=Jomhuria
  &display=swap" rel="stylesheet" />
```

---

### Color Palette

Three colors maximum, each with a defined role:

| Role | Name | Hex | Where it appears |
|---|---|---|---|
| **Background** | Deep Charcoal | `#111317` | Page background, hero, all dark sections |
| **Primary Accent** | Brand Gold | `#FFD24D` | CTAs, headline highlights, borders on hover, logo, stat numbers — THE only accent |
| **Primary Text** | Warm White | `#FFF9E6` | All headlines and display text |

Supporting shades (not additional colors — just variations of the base palette):

| Name | Hex | Use |
|---|---|---|
| Card Dark | `#161a20` | Card and section backgrounds |
| Card Darker | `#1c2028` | Nested containers, tertiary depth |
| Gold Dim | `#D4BC80` | Secondary body text, muted labels |
| Steel Body | `#a0a8b4` | Captions, metadata |
| Border | `#2a2f3a` | Card edges, dividers |

**The rule:** Dark background everywhere. Gold is the ONLY accent color. No blue, no purple, no neon.

---

## 2. AI Tools Used — Process Log

### Claude Code (CLI) — Main Build Tool ✅

**What we built with it:**
- Full `index.html` landing page (~1,100 lines of HTML + CSS + JS, zero external dependencies)
- 7 sections: Hero, Problem, Outcomes, About Kasim, Who It's For, Testimonials, Final CTA
- Sticky gold navbar with "Reserve Your Seat" CTA
- Countdown timer to the webinar
- Scroll-driven fade-up animations (IntersectionObserver)
- Kasim's photo integrated into the hero with a left-to-right gradient overlay
- Favicon set wired up in `<head>`
- Multiple refinement passes fixing the hero photo, gradient, and layout

**AI chat used:** Claude Code CLI (this session and prior sessions) running in `C:\Users\axele\Desktop\pareto\homework 3\`

**Key git commits from Claude Code:**
```
b2003b6  Fix hero photo: smaller face (82%), anchor to bottom
450e2a3  Use CSS background-image for PNG: fixes transparency
55c920a  Fix PNG transparency: position as absolute img
317aff1  Fix hero: PNG with transparent bg, smooth gradient, golden glow
f3cd1b8  Fix photo src, smooth gradient, refine golden glow
2d8ac29  Add golden halo, dark bg, bring photo closer
d7ee844  Update hero headline, subtitle, and outcome cards copy
e5664d7  Add Kasim Aslam delegation webinar landing page
```

---

### Google Stitch — Tried, Not Useful ⚠️

**What we tried:** Prompted it to generate the Kasim landing page hero and sections using the design brief.

**Outcome:** The generated designs didn't align well with the premium dark brand. The components it produced were generic and didn't respect the specific gold-on-charcoal aesthetic. The output wasn't ready to use or easy to adapt — we would have spent more time cleaning it up than building from scratch.

**Decision:** Abandoned. Claude Code produced a better result faster with full control over the code.

---

### Google AI Studio (Gemini) — Worked, With Issues ⚠️✅

**What it is:** Google's AI Studio (aistudio.google.com) running Gemini models — a web-based interface for prompting AI to generate content, code, and assets.

**What we used it for:** Generating the banner graphic (`bannerKasimLanding.png`) and exploring layout ideas / copy variations for the landing page sections.

**Outcome:** Gemini was able to produce useful output — the banner image and some copy direction came from here. However, there were some friction points:
- The image generation quality was inconsistent — required multiple regeneration attempts to get something usable
- Some of the generated copy had a different tone than the Kasim brand voice (too generic/motivational rather than direct and authoritative)
- Integration into the HTML required manual work

**Assets from Gemini:**
- `bannerKasimLanding.png` — main landing page banner (1221 KB)
- `resizeBanner.jpg` — resized version for web use (137 KB)

---

## 3. Assets Inventory

| File | Type | Source | Use |
|---|---|---|---|
| `Kasim-Aslam-600x600.jpg` | Photo | Original | Hero section — Kasim's headshot |
| `bannerKasimLanding.png` | Banner | Google AI Studio (Gemini) | Page banner / graphic |
| `resizeBanner.jpg` | Banner | Resized from above | Web-optimized version |
| `favicon_io/favicon.ico` | Icon | favicon.io + Google Fonts (Jomhuria) | Browser tab icon |
| `favicon_io/favicon-32x32.png` | Icon | favicon.io | Browser tab (standard) |
| `favicon_io/favicon-16x16.png` | Icon | favicon.io | Browser tab (small) |
| `favicon_io/apple-touch-icon.png` | Icon | favicon.io | iOS home screen |
| `favicon_io/android-chrome-192x192.png` | Icon | favicon.io | Android home screen |
| `favicon_io/android-chrome-512x512.png` | Icon | favicon.io | Android splash |
| `favicon_io/site.webmanifest` | Config | favicon.io | PWA icon manifest |
| `index.html` | Page | Claude Code | Full landing page |
| `DESIGN.md` | Docs | Claude Code | Full design system reference |

---

## 4. Design System Summary (Brand Kit)

```
LOGO FONT:    Jomhuria (Google Fonts) — wordmark & favicon
MAIN FONT:    Inter 900 — all headlines and UI
ACCENT FONT:  Playfair Display Italic 700 — pull quotes only

COLORS (3):
  #111317  Deep Charcoal  — background
  #FFD24D  Brand Gold     — sole accent (CTAs, highlights)
  #FFF9E6  Warm White     — headlines and primary text

FAVICON:  Generated via favicon.io using Jomhuria font
          Full set: .ico + PNG @ 16/32/192/512px + apple-touch + webmanifest
```

---

## 5. Tools Reference

| Tool | URL | Used For |
|---|---|---|
| Claude Code | claude.ai/code | Built entire landing page (index.html) |
| Google Stitch | stitch.withgoogle.com | Tried for UI generation — not used |
| Google AI Studio | aistudio.google.com | Generated banner graphic |
| favicon.io | favicon.io | Generated logo + full favicon set |
| Google Fonts | fonts.google.com | Jomhuria · Inter · Playfair Display |
| GitHub Pages | github.com | Hosting the live page |
