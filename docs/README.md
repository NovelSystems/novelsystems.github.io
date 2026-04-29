# Handoff: Novel Systems Engineering — marketing site

## Overview

Single-page marketing site for **Novel Systems Engineering LLC**, the independent research vehicle of Samuel C. Ryan. The site introduces the company and presents two project threads — **DDR** (a polarimetric SWIR LiDAR architecture, patent-pending) and **CANDOR** (a multi-agent framework for mitigating LLM sycophancy, published).

Tone: independent researcher, editorial, monospace-leaning, parchment + dark olive. Not a startup site, not a defense-prime site — a small research practice's quiet portfolio.

## About the Design Files

The files bundled here (`Novel Systems.html`, plus the `images/` folder) are **design references created in HTML**. They are not production code to copy directly. The task is to **recreate this design in the target codebase's environment** (Next.js / Astro / Eleventy / plain static — pick what fits the project) using its established patterns. If no codebase exists yet, choose the simplest stack that delivers the typography and image fidelity required — a static-site generator (Astro or Eleventy) is recommended over a heavy SPA.

If you go with a static or SSG approach, treat the HTML as a single source-of-truth template you can split into partials/components: `Header`, `Hero`, `About`, `Project` (used twice), `Founder`, `Footer`.

## Fidelity

**High-fidelity.** Final colors, typography, spacing, and image treatments are decided. Recreate pixel-faithfully. The accent color (dark olive) and typography (Fraunces + JetBrains Mono) are non-negotiable.

## Screens / Views

This is a **single-page** site with five stacked sections. Two project detail pages (DDR, CANDOR) are planned but not in this handoff — they live in `Novel Systems Wireframes.html` as a wireframe reference for the codex-spread layout. Build the landing page first.

### 1. Header (sticky-candidate, currently static)
- Layout: flex row, space-between, max-width 1100px, 22px vertical / 40px horizontal padding.
- Left: 30px circular outlined glyph (italic lowercase "n", 1.5px border var(--ink)) + uppercase mono name "Novel Systems Engineering" (11px, letter-spacing 0.18em, color var(--ink-2)).
- Right: nav with 4 links — About / Projects / Founder / Contact. JetBrains Mono 11px, 0.14em letter-spacing, uppercase, gap 32px. Hover: color shifts to var(--olive-deep) with a 1px bottom border.

### 2. Hero
- Full-width image plate, aspect-ratio 16/7, `object-fit: cover; object-position: center 22%` so the bird is fully framed.
- Image filter: `sepia(0.10) saturate(0.92) contrast(0.98) brightness(1.02)` — gives the parchment-tone match.
- Bottom-left overlay caption: "Plate I · Frontispiece · MMXXVI" in JetBrains Mono 10px, 0.18em letter-spacing, uppercase, paper color, soft text-shadow.
- Subtle bottom fade: linear-gradient from transparent to rgba(241,234,215,0.65) at the bottom 45% to blend into the page.
- Below the plate, inside the 1100px container:
  - Eyebrow: "An independent research vehicle" — JetBrains Mono 11px, 0.22em, olive-deep, with a 24×1px olive rule before it.
  - Headline: "Novel Systems *Engineering.*" — Fraunces, weight 400, clamp(56px, 7.6vw, 104px), line-height 0.92, letter-spacing -0.025em. The word "Engineering." is italic and colored var(--olive-deep).
  - Right column (auto-width, aligned to bottom): lede in Fraunces italic 22px, line-height 1.4, max-width 380px, color var(--ink-2). Text: "A research vehicle for novel sensor architectures and AI systems."
  - Below band, separated by 1px var(--rule): meta row, JetBrains Mono 11px, 0.14em uppercase, var(--ink-3). Left: "Wilsonville, Oregon · LLC · Established 2026" with 10×1px olive marker. Right: "novelsystems.me".

### 3. About — § I, "On the Work"
- Section head: 200px gutter for `§ I  On the Work` (mono 11px 0.22em uppercase olive-deep) + section title "Problems without commercial solutions." (Fraunces italic 36px). Bottom border 1px var(--rule-strong).
- Body grid: `200px 1fr 200px`, gap 48px.
  - Left aside: short stacked label, mono 10px 0.18em uppercase var(--ink-3), with top border var(--rule). Content: "Two threads / One workshop / Sensor + AI".
  - Center: two paragraphs. First paragraph has a serif italic dropcap (`::first-letter`, font-size 5.4em, line-height 0.85, color olive-deep, padding-right 12px). Body 19px Fraunces, line-height 1.55.
  - Right aside: same treatment, "Patent pending / Paper published / Available for review".

### 4. Projects — § II, "Two threads, independent."
Each project is a grid `200px 1fr` with 48px gap. First project no top border; subsequent projects separated with `border-top: 1px var(--rule)` and 64px top margin.

**Left column (sidebar, per project):**
- Big italic numeral (i. / ii.) — Fraunces 64px, line-height 0.9, color olive-deep, weight 300.
- Meta label: mono 10px 0.18em uppercase var(--ink-3), two lines.
- Status tag: mono 10px 0.16em uppercase, padded 4×8px, background var(--olive-soft), color olive-deep.

**Right column (body):**
- Image: aspect-ratio 16/9, 1px var(--rule) border, with bottom-left absolute caption pill (mono 10px paper-on-ink box).
- Title: Fraunces 56px, line-height 1, letter-spacing -0.02em.
- Expansion: italic Fraunces 22px var(--ink-2), 6px below.
- Abstract: Fraunces 22px, line-height 1.45 — the punchy one-liner.
- Summary: Fraunces 16px, line-height 1.6, var(--ink-2), max-width 640px.
- CTA: "Read more →" — mono 11px 0.16em uppercase, olive-deep, 1px bottom border. Hover: rust.

Project content (verbatim — do not paraphrase):

#### DDR
- Numeral: `i.`
- Meta: `Sensor · SWIR LiDAR` / `Polarimetric · 2026`
- Status tag: `Utility · Pending`
- Image: `images/ddr_laser.jpg`, caption `DDR · Polarized SWIR Return`
- Title: `DDR`
- Expansion: `Differential Depolarization Response`
- Abstract: `DDR classifies targets by material composition — not shape or motion.`
- Summary: `When a pulsed SWIR laser illuminates a surface, the return signal depolarizes at a rate that depends on material structure. The asymmetry between horizontal and vertical polarization states is a physically grounded material signature, stable across target geometries and viewing angles.`

#### CANDOR
- Numeral: `ii.`
- Meta: `AI · Multi-agent` / `RLHF · 2026`
- Status tag: `Published · +34.5%`
- Image: `images/candor_courtroom.jpg`, caption `CANDOR · Principled Agent Debate`
- Title: `CANDOR`
- Expansion: `Core Architecture for Non-Deference, Oversight, and Reasoning`
- Abstract: `RLHF-trained language models tend to agree with whoever is talking to them. CANDOR mitigates this through structured agent debate.`
- Summary: `The core mechanism, Principled Agent Debate (PAD), pairs two models as philosophical opponents — one for the user's position, one against — while a third evaluates the exchange. The white paper reports a 34.5% accuracy improvement over control baselines.`

### 5. Founder — § III, "Samuel C. Ryan."
- Section head same pattern as About.
- Body grid: `200px 220px 1fr`, gap 48px.
  - Aside (left): mono 10px 0.18em uppercase, top-bordered. Lines: `Wilsonville, OR / M.S. Semiconductor / Process Engineering / 15 yrs · 7 industries`.
  - Portrait: 220px × aspect-ratio 4/5 box, 1px var(--rule) border. `images/sam_ryan_headshot.jpg`, sepia 0.05 / saturate 0.95.
  - Body: name "Samuel C. Ryan" — Fraunces 32px, weight 400. Role "Founder & Principal Investigator" — Fraunces italic 16px var(--ink-2), 4px above / 20px below. Two paragraphs Fraunces 17px line-height 1.6 max-width 640px. Verbatim:
    1. `Samuel C. Ryan is a systems engineer and inventor based in Wilsonville, Oregon. He holds an M.S. in Semiconductor Process Engineering from the University of Oregon and has designed instrumentation systems across seven industries over fifteen years, including work at FLIR Systems on DOD-qualified thermal imaging hardware and at ESS Tech on long-term energy storage.`
    2. `Novel Systems Engineering LLC is his independent research vehicle, focused on problems that don't yet have a commercial solution.`

### 6. Footer
- 1px solid var(--rule-strong) top border, 48/56px padding.
- Three-column grid `200px 1fr 200px`, gap 48px:
  - Left: "Affiliation" label (mono 10px 0.22em uppercase olive-deep).
  - Center: Birthmark callout — Fraunces 17px line-height 1.55 var(--ink-2). "The Birthmark Standard Foundation" is non-italic, weight 500, var(--ink). Link "birthmarkstandard.org →" is olive-deep with 1px bottom border.
  - Right: meta block, mono 10px 0.16em uppercase var(--ink-3), right-aligned. "Novel Systems / Engineering LLC / © MMXXVI" (the © line in var(--ink-4)).

## Interactions & Behavior

- All nav links scroll to anchor (`#about`, `#projects`, `#founder`). `Contact` is a `mailto:sam@novelsystems.me`.
- Hovers: nav links and the project CTA shift color and underline color (olive-deep → rust on the CTA). 150ms transition.
- No animations, no carousels, no modals. The site is intentionally still.
- Responsive: at <900px, collapse the three-column About/Footer grids to single column, stack the project grid (sidebar above body), reduce hero plate to aspect-ratio 4/5, and let nav wrap or move to a small dropdown. Mobile breakpoints are not in the reference HTML — implementer's discretion using these tokens.

## State Management

None. Static site.

## Design Tokens

```css
/* Surface */
--paper:       #f1ead7;   /* page background */
--paper-2:     #e9e0c7;   /* image-box fallback */
--paper-edge:  #d8ccab;

/* Ink */
--ink:    #1f1c14;        /* primary text */
--ink-2:  #4a4538;        /* secondary text */
--ink-3:  #847d68;        /* muted / meta */
--ink-4:  #b8af96;        /* faintest */

/* Accent */
--olive:       #4a5a2a;
--olive-deep:  #34401d;   /* primary accent */
--olive-soft:  rgba(74, 90, 42, 0.10);
--rust:        #7a3a1f;   /* secondary accent — hover only */

/* Rules */
--rule:         rgba(31, 28, 20, 0.18);
--rule-strong:  rgba(31, 28, 20, 0.55);
```

```css
/* Type */
--serif: 'Fraunces', 'EB Garamond', Georgia, serif;
--mono:  'JetBrains Mono', ui-monospace, 'SF Mono', Menlo, monospace;

/* Container */
--col:        1100px;
--col-narrow: 720px;
```

**Type scale (used in design):**
- Hero headline: clamp(56px, 7.6vw, 104px) / 0.92 / -0.025em
- Section title (italic): 36px / 1.0 / -0.01em
- Project title: 56px / 1.0 / -0.02em
- Project expansion: 22px italic
- Project abstract: 22px / 1.45
- Body large: 19px / 1.55
- Body: 17px / 1.6
- Body small: 16px / 1.6
- Eyebrow / labels (mono): 10–11px / 0.16–0.22em letter-spacing / uppercase

**Image treatments:**
- Hero plate: `sepia(0.10) saturate(0.92) contrast(0.98) brightness(1.02)`, gradient overlay at bottom blending to `--paper`.
- Project images: `sepia(0.08) saturate(0.95) contrast(1.0)`.
- Portrait: `sepia(0.05) saturate(0.95) contrast(1.0)`.

## Assets

All images are in the `images/` folder of this handoff:

- `images/hero_bird.jpg` — Bird perched on a stack of books (frontispiece). 1024×1024. Crop with `object-position: center 22%`.
- `images/ddr_laser.jpg` — Light/laser reference for DDR.
- `images/candor_courtroom.jpg` — Courtroom interior for CANDOR.
- `images/sam_ryan_headshot.jpg` — Founder portrait.

If the production site needs higher-resolution sources, request originals from the user — these are the proof crops.

## Fonts

Both fonts are on Google Fonts. Use a `<link>` to `https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,300..700;1,9..144,300..600&family=JetBrains+Mono:wght@400;500;600&display=swap` or equivalent self-host. Fraunces uses optical sizing — the variable axis is in use; do not pin a static weight at the headline scale.

## Files

- `Novel Systems.html` — the high-fidelity reference. Open it directly in a browser to see the target. All CSS is inline in `<style>`; copy/adapt into the target codebase's styling solution (CSS Modules, Tailwind, vanilla CSS — whatever the project uses).
- `images/` — production-candidate imagery (see above).

## Notes / Caveats

- **No iconography.** Resist adding it. The design relies on type, rules, numerals, and a few photos.
- **No gradients beyond the hero fade.** Backgrounds are flat parchment with very subtle radial gradients (already in the reference) for paper depth.
- **Numerals (`i.` `ii.`) are italic Fraunces** — not roman numerals in monospace. Match exactly.
- The dropcap is a serif italic *first-letter* style; do not use a custom span unless your CMS strips `::first-letter`.
- Project detail pages (DDR, CANDOR) are out of scope here. The codex-spread wireframe in `Novel Systems Wireframes.html` is the agreed direction for those when built.
