---
name: ui-design-kit
description: "One-prompt editorial landing page system. Load this skill, paste the bootstrap prompt, and get a complete Next.js + Tailwind landing page with locked typography, color slots, composition rules, anti-slop checks, and production gotchas covered."
version: 2.0.0
author: Hermes Agent + Zubbycrypt
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [ui, design, frontend, landing-page, editorial, tailwind, nextjs]
    related_skills: [frontend-design, imagegen-frontend-web, humanizer]
---

# UI Design Kit — Editorial Landing Page System

A single-prompt system for building marketing sites that feel **designed** — not AI-generated, not template-sourced.

## Bootstrap Prompt (paste into any new chat)

```
I'm building a landing page in Next.js 15 App Router + Tailwind v4 + TypeScript.
Use the UI Design Kit system:
- Dark theme by default with bg/surface/text slot system
- One accent color (precious — used 2-3x max), one secondary accent (emotional moment, rarer)
- Fonts: Syne 800 headlines + Space Grotesk 400 body + mono uppercase eyebrows
- Section wrapper is max-w-7xl mx-auto px-4/6
- Buttons shrink on hover (scale-95) and flip to accent — never grow
- No pure black or white. No overlays on images. No emojis. No exclamation marks
- Editorial > corporate. One idea per section
- Stroke text uses inline style (not Tailwind). Glow hover uses a React component (not CSS)
- OG image via next/og with fonts passed. Resend for email (lazy init inside handler)
- Strip any AI co-author trailers before pushing
```

## When to Use

- Starting a new marketing site or landing page
- Redesigning an existing page that looks generic
- User says "make it look premium / editorial / designed"
- Any project where you'd default to Inter + purple gradients

**Don't use for:** dashboards (use `frontend-design`), backend-only, pure API UI.

## Default Stack

| Layer | Choice |
|-------|--------|
| Framework | Next.js 15 App Router + TypeScript |
| Styling | Tailwind CSS v4 + CSS variables |
| Fonts | Syne (display) + Space Grotesk (body) + JetBrains Mono (eyebrows/data) |
| Motion | Framer Motion + CSS transitions |
| Icons | Lucide |
| Images | next/image + Unsplash/Pexels |
| Email | Resend (lazy init inside handler) |
| OG | next/og + font files in `public/fonts/` |
| Deploy | Vercel |

## Core Color Slots

| Slot | Dark default | Role |
|------|-------------|------|
| bg | `#0a0a0c` | Page background |
| surface | `#121218` | Cards, inputs, sections |
| surface-border | `rgba(255,255,255,0.06)` | Section dividers, card outlines |
| text-1 | `#f4f4f5` | Headlines |
| text-2 | `#a1a1aa` | Body |
| text-3 | `#71717a` | Eyebrow labels, captions |
| accent-primary | *project-specific* | CTAs, hover, emphasis (used 2-3x max) |
| accent-secondary | *project-specific* | Emotional accent — appears once, maybe twice per page |

### Palette rules
- 1 primary, 1 secondary, 1 accent (sparing), full neutral scale
- Build with [Coolors](https://coolors.co/) → preview on [Realtime Colors](https://www.realtimecolors.com/)
- Check contrast: [WebAIM](https://webaim.org/resources/contrastchecker/) (AA minimum)
- **No pure black** (`#000000`) or pure white (`#ffffff`) anywhere
- **Banned:** purple→blue AI mesh, rainbow orbs, neon glow spam

### CSS variables to ship

```css
:root {
  --bg: #0a0a0c;
  --surface: #121218;
  --surface-border: rgba(255, 255, 255, 0.06);
  --text-1: #f4f4f5;
  --text-2: #a1a1aa;
  --text-3: #71717a;
  --accent: /* lock once */;
  --accent-secondary: /* emotional accent */;
  --radius: 6px;
}
```

## Typography System

| Element | Font | Weight | Case |
|---------|------|--------|------|
| H1 (hero) | Syne | 800 | Normal |
| Section H2 | Syne | 800 | Normal |
| H3+ | Syne | 700 | Normal |
| Body | Space Grotesk | 400 | Normal |
| Small / caption | Space Grotesk | 400 | Normal |
| Eyebrow / label | JetBrains Mono | 500 | Uppercase |
| Data / stats | JetBrains Mono | 400 | Normal |

- Load via `next/font` (Google Fonts)
- **Fontshare** alternative: Cabinet Grotesk (display) + Satoshi (body) — same energy
- **Avoid:** Inter + Roboto + Arial as the whole system

## Composition & Section System

### Hero Composition Bias
**The left-text / right-image hero is the most overused AI pattern.** Default to one of these instead:

- Centered statement over full-bleed image (text in lower 40%)
- Bottom-left text over background image
- Bottom-right text over background image
- Stacked center (label / headline / sub / CTA all centered)
- Image-as-canvas with text overlaid
- Right-text / left-image (inverted classic)
- Mini Minimalist (tiny logo + short statement + thin CTA, mostly space)

### Background Modes (vary across sections)
Pick 1 per section, never repeat the same mode 3+ times in a row:
1. Solid surface + inline asset
2. Full-bleed image with tonal overlay
3. Editorial side-image (50/50 or 60/40 split)
4. Flat color block + accent detail
5. Cinematic tonal gradient (palette-matched, low-chroma)
6. Duotone treated image
7. Soft radial vignette + product crop
8. Micro-noise gradient over solid

### Section Rhythm
- Vary density: some sections large + art-directed, some mini + minimalist
- Vary background mode across sections
- Keep spacing generous and even between sections
- Never repeat the same composition anchor 3 sections in a row

### CTA Variation (not always primary pill)
- Classic primary pill
- Outline / ghost
- Underlined inline link with arrow
- Oversized headline + tiny CTA hint
- CTA as caption under a strong visual

## Component Laws

### Button Rule
- Shrink on hover: `transform: scale(0.95)` — never grow
- Flip to accent color on hover
- Transition: `transition-all duration-300`

### Stroke Text
- MUST use **inline style** with `WebkitTextStroke` / `WebkitTextFillColor`
- Tailwind classes won't work for stroke text
```tsx
<h1 style={{
  WebkitTextStroke: '1px var(--text-1)',
  WebkitTextFillColor: 'transparent',
}}>Headline</h1>
```

### Glow Hover
- MUST be a **React component** (CSS text-shadow hover classes won't apply)
- Use Framer Motion or a custom component

### Section Eyebrow Pattern
Every section gets an uppercase mono label above the headline:
```tsx
<p className="font-mono text-xs tracking-widest text-[var(--text-3)] uppercase mb-2">
  {label}
</p>
<h2 className="text-4xl font-bold">{headline}</h2>
```

### Phone Video Frame
When showing mobile video, frame it in a phone mockup:
```tsx
<div className="relative mx-auto w-[280px]">
  <div className="rounded-[3rem] border-4 border-[var(--surface-border)] overflow-hidden">
    <video ... />
  </div>
</div>
```

### Video — iOS Autoplay
All four attributes required or iOS Safari won't autoplay:
```tsx
<video autoPlay muted playsInline loop>
```
Also: WebM doesn't play in Chrome on iOS. Always convert to MP4 (H.264).

## Anti-AI-Slop Checklist (must pass)

### Layout
- [ ] Not all sections same centered-card layout
- [ ] Not endless left-text/right-image clones
- [ ] Background modes vary (not all solid-surface)
- [ ] Hero is NOT the default text-left/image-right
- [ ] Section rhythm varies (some big, some mini)

### Visual
- [ ] No purple-blue mesh default
- [ ] No floating meaningless blobs
- [ ] No glassmorphism without reason
- [ ] Real photos or illustrations, not AI blobs
- [ ] No gradient text as "premium" shortcut
- [ ] No neon edges / glow halos

### Typography
- [ ] Not Inter-only / system-font-only
- [ ] No gradient headlines
- [ ] No 6-line startup headings
- [ ] Font scale has real contrast (display ≠ body)

### Content
- [ ] Copy is specific, not startup-cliché
- [ ] Words banned: unleash, elevate, revolutionize, next-gen, seamless, powerful solution, transformative platform
- [ ] No fake brands (Acme, Nexus, Flowbit, NovaCore)
- [ ] No emojis in body copy
- [ ] No exclamation marks

### Density
- [ ] Not over-packed — page breathes
- [ ] No card overload in every block
- [ ] Even spacing between sections
- [ ] No carousel / marquee logo strips with 6 blobs
- [ ] No fake KPI columns unless explicitly asked

### States
- [ ] Empty + loading + hover states present on interactive elements

## Technical Gotchas

### OG Image (next/og / Satori)
- No gradients — use solid color fill
- No border-radius — Satori doesn't support it
- Must pass fonts array to `ImageResponse` options or text falls back to generic sans
- Store font files in `public/fonts/`

### Resend (email)
- Lazy init the Resend client **inside** the API route handler
- Never initialize at module scope (breaks serverless cold start)

### Git
- Strip AI co-author trailers from commit messages before pushing
- Common trailers to remove: `Co-authored-by:`, `Generated by`, `Built with`

### Images
- No overlays on images (editorial rule) — let images breathe
- next/image with real Unsplash/Pexels URLs
- Compress before ship: [Squoosh](https://squoosh.app/), [TinyPNG](https://tinypng.com/)

### Icons
- Lucide default: https://lucide.dev/
- Phosphor for multi-weight: https://phosphoricons.com/
- Simple Icons for brands: https://simpleicons.org/
- Logo pattern: `[icon] BrandName` — never wordmark-only

## Reference Sites (study before starting)

Linear, Stripe, Vercel, Cursor, Resend, Mercury, Pitch, Raycast
Inspo: dark.design, heroinspo.com, Mobbin, Awwwards

## Quick Workflow

### 1. Lock aesthetic
One sentence: tone + audience + memorable trait. Pick extreme intentionally.
*"Dark editorial DeFi landing, emerald accent, cinematic hero, industrial body type."*

### 2. Bootstrap
Paste the bootstrap prompt from the top of this skill.

### 3. Build sections (in order)
1. **Hero** — Giant Statement or Mid Editorial or Mini Minimalist
2. **Trust bar** — logo strip (if needed) or proof sentence
3. **Features** — vary layout (bento / staggered / editorial split)
4. **Showcase / product** — full-bleed or editorial side-image
5. **Testimonials / proof** — quote wall or metrics strip
6. **Pricing / CTA** — clean decisive close

### 4. Enforce system
- Color slots everywhere, no random hex
- Button law applied
- Stroke text uses inline style
- Section eyebrow pattern on every section
- No pure black/white, no overlays, no emojis, no exclamation marks

### 5. Ship checks
- [ ] Anti-AI-slop checklist passed
- [ ] OG image built (solid color, no gradients)
- [ ] iOS video autoplay attributes correct
- [ ] Email handler uses lazy init
- [ ] Git trailers stripped
- [ ] PageSpeed + mobile check → Vercel

## Full Resource Catalog

See `references/resource-catalog.md` for the complete free tool stack (fonts, colors, icons, stock assets, motion, illustrations, writing tools).

## Related Skills

- `frontend-design` — production UI implementation patterns (Next/Tailwind/DeFi)
- `imagegen-frontend-web` — per-section design reference images
- `humanizer` — strip AI-isms from copy
