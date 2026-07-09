---
name: ui-design-kit
description: "Use when designing UIs, landings, dashboards, or product copy. Loads Zubbycrypt's free design kit — fonts, colors, icons, stock assets, motion, components, writing tools, and practice drills — so builds avoid AI-generic aesthetics."
version: 1.0.0
author: Hermes Agent + Zubbycrypt
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [ui, design, frontend, fonts, icons, motion, writing, assets]
    related_skills: [frontend-design, imagegen-frontend-web, humanizer]
---

# UI Design Kit (Zubbycrypt)

Personal design kit on this Hermes profile. Curated free professional resources so every UI build starts with the same high-quality stack — not AI-generic defaults.

**Source list:** Moh4696/300-free-resource-websites (safe link directory; no install). Full catalog: `references/resource-catalog.md`.

## When to Use

- Designing or redesigning any landing, dashboard, modal, marketing page
- Choosing fonts, palette, icons, stock photos, illustrations, motion
- Writing product/landing copy that shouldn't sound AI-dense
- Starting a new Next.js + Tailwind UI and needing the default stack
- User says "design kit", "use our UI resources", or "professional UI"

**Don't use for:** backend-only work, pure API design, non-UI infrastructure.

## Default Stack (this user)

| Layer | Default |
|---|---|
| Framework | Next.js App Router + TypeScript |
| Styling | Tailwind CSS v4 + CSS design tokens |
| Motion | Framer Motion **or** CSS + IntersectionObserver |
| Icons | Lucide first; Phosphor when multiple weights needed |
| Charts | Recharts (dark-friendly gradients) |
| Images | `next/image` + real stock (Unsplash/Pexels) |
| Deploy | Vercel Hobby |

## Design Kit Workflow

Follow in order. Done when each step's criterion is met.

### 1. Lock aesthetic direction

- Write one sentence: tone + audience + one memorable trait
  Example: *"Dark luxury DeFi dashboard, orange accent, editorial spacing."*
- Pick extreme intentionally: luxury / industrial / editorial / soft SaaS / crypto-terminal
- **Done when:** one sentence exists and palette direction is named (not "modern purple")

### 2. Typography

- Prefer **Fontshare** for distinctive free commercial fonts over Inter-only
- Pair: 1 display (H1 only) + 1 body
- Load via `next/font` (Google or local)
- Tools: [Fontshare](https://www.fontshare.com/), [Typewolf](https://www.typewolf.com/), [Google Fonts](https://fonts.google.com/), [Wordmark.it](https://wordmark.it/)
- **Avoid:** Inter + Roboto + Arial as the whole system
- **Done when:** display + body fonts named and applied in layout

### 3. Color tokens

- 1 primary, 1 secondary, 1 accent (sparing), full neutral scale
- Build with [Coolors](https://coolors.co/) → preview on [Realtime Colors](https://www.realtimecolors.com/)
- Check contrast: [WebAIM](https://webaim.org/resources/contrastchecker/) (AA minimum)
- Gradients: [cssgradient.io](https://cssgradient.io/) — low-chroma, palette-matched only
- **Banned:** purple→blue AI mesh, rainbow orbs, neon glow spam
- Ship CSS variables:

```css
:root {
  --bg: #0a0a0c;
  --surface: #121218;
  --border: rgba(255,255,255,0.08);
  --ink: #f4f4f5;
  --muted: #a1a1aa;
  --accent: /* brand — lock once */;
  --emerald: #22c55e;
  --rose: #f43f5e;
  --amber: #f59e0b;
  --radius: 10px;
}
```

- **Done when:** tokens in CSS/Tailwind theme; no hardcoded random hex in new components

### 4. Icons

- **Lucide** default: https://lucide.dev/
- **Phosphor** for multi-weight sets: https://phosphoricons.com/
- **Heroicons** OK for Tailwind-adjacent: https://heroicons.com/
- **Simple Icons** for brand marks: https://simpleicons.org/
- Logo pattern: small SVG icon **beside** brand text `[icon] BrandName` — never wordmark-only
- **Done when:** one icon family chosen; brand mark is icon + text

### 5. Real imagery (no AI blobs)

| Need | Source |
|---|---|
| Hero / lifestyle photos | [Unsplash](https://unsplash.com/), [Pexels](https://www.pexels.com/) |
| Stock video | [Coverr](https://coverr.co/), [Mixkit](https://mixkit.co/) |
| Recolorable illustrations | [unDraw](https://undraw.co/), [Storyset](https://storyset.com/) |
| Empty-state characters | [Open Doodles](https://www.opendoodles.com/), [Humaaans](https://www.humaaans.com/), [Open Peeps](https://www.openpeeps.com/) |
| Diverse people stock | [Nappy](https://www.nappy.co/) |
| Compress before ship | [Squoosh](https://squoosh.app/), [TinyPNG](https://tinypng.com/) |
| Quick edit / bg remove | [Photopea](https://www.photopea.com/), [remove.bg](https://www.remove.bg/) |

- Prefer full-bleed photo or strong product shot over floating orbs
- **Done when:** every major visual is a real asset URL or local file, not a placeholder blob

### 6. Motion

- High-impact moments only: page load, scroll reveal, hover, modal enter
- Easing: `cubic-bezier(0.16, 1, 0.3, 1)` ([easings.net](https://easings.net/))
- CSS animation recipes: [Animista](https://animista.net/)
- Framer Motion pattern: `initial` / `whileInView` / `viewport={{ once: true }}`
- Depth textures: [fffuel](https://www.fffuel.co/), [Hero Patterns](https://heropatterns.com/), [Shape Divider](https://www.shapedivider.app/)
- **Done when:** one orchestrated reveal system; no animation spam on every element

### 7. Components & layout

- Inspiration only: [UIVerse](https://uiverse.io/) — restyle heavily, never ship stock purple
- Design first in [Figma](https://www.figma.com/) when possible
- Layout flavors: bento, editorial split, full-bleed image, sticky nav — vary anchors
- Every panel ships with: header + subtitle, hover/focus/active, loading, empty state
- Optional primitives: shadcn/Radix for a11y **structure only** — own the visual system
- **Done when:** UI stands alone visually before API wiring

### 8. Writing / product copy

- Clarity: [Hemingway](https://hemingwayapp.com/)
- Grammar: [LanguageTool](https://languagetool.org/)
- Word choice: [Power Thesaurus](https://www.powerthesaurus.org/)
- Then humanize — load `humanizer` skill if copy still feels AI
- Avoid: unleash / elevate / seamless / next-gen / revolutionize
- Prefer specific product language (what it does + for whom)
- **Done when:** headlines are specific; body passes Hemingway denseness check

### 9. Ship quality checks

- [PageSpeed Insights](https://pagespeed.web.dev/)
- [Can I Use](https://caniuse.com/) for experimental CSS
- [Responsively](https://responsively.app/) multi-device
- [RealFaviconGenerator](https://realfavicongenerator.net/)
- Deploy: [Vercel](https://vercel.com/)
- **Done when:** LCP reasonable, contrast OK, mobile nav works, favicon set

## Practice Drills (skill growth)

When user wants to train UI skill (not ship a product):

1. [Frontend Mentor](https://www.frontendmentor.io/) — build from real briefs
2. [The Odin Project](https://www.theodinproject.com/) / [Full Stack Open](https://fullstackopen.com/)
3. [roadmap.sh](https://roadmap.sh/) frontend roadmap
4. Rebuild one Awwwards section weekly (structure only; original assets)

## Anti-AI-Slop Checklist (must pass)

- [ ] Not Inter-only / system-font-only
- [ ] No purple-blue mesh default
- [ ] No identical 3-card feature row as the only layout
- [ ] Real photos or directed illustrations, not blobs
- [ ] Tokens used; no random hex soup
- [ ] Motion restrained and purposeful
- [ ] Copy is specific, not startup-cliché
- [ ] Empty + loading + hover states present

## Related skills

- `frontend-design` — production UI implementation patterns (Next/Tailwind/DeFi dashboard)
- `imagegen-frontend-web` — per-section design reference images
- `humanizer` — strip AI-isms from copy

## Common Pitfalls

1. **Treating UIVerse/shadcn as final look** — structure/inspiration only; restyle to brand.
2. **Skipping contrast check** — pretty ≠ professional if text fails AA.
3. **Too many icon sets** — one family per product.
4. **DaFont / free novelty fonts** — many are personal-use only; prefer Fontshare/Google commercial-safe.
5. **Flaticon free tier** — attribution required; use Lucide/MIT for product UI.
6. **Animating everything** — one load sequence + scroll reveals beat 20 micro-motions.
7. **Functional skeleton first** — this user wants designed panels on first pass.

## Verification Checklist

- [ ] Aesthetic one-liner locked
- [ ] Fonts: display + body named and loaded
- [ ] CSS tokens present and used
- [ ] Icon family chosen
- [ ] Real image sources linked
- [ ] Motion easing set
- [ ] Copy humanized
- [ ] Anti-AI-slop checklist passed

## One-Shot: New landing page

1. Lock aesthetic one-liner
2. Fontshare pair + Coolors palette → tokens
3. Source Unsplash hero + Lucide icons
4. Build Hero → Features → Showcase → CTA with scroll reveals
5. Hemingway pass on all copy
6. PageSpeed + mobile check → Vercel

## One-Shot: Dashboard panel

1. Dark surface tokens + brand accent
2. Header title + subtitle + status badge
3. Card grid with border `var(--border)`, radius 10px
4. Hover lift / focus ring on controls
5. Loading spinner + intentional empty state
6. Wire API only after UI stands alone
