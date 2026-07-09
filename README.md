# UI Design Kit

**Hermes Agent skill** that kills AI-generic UI.

A free, installable design kit for people vibe-coding with AI agents (Hermes, Claude Code, Cursor, OpenCode, etc.). Fonts, colors, icons, stock assets, motion, copy tools, and an anti-slop checklist — so your product looks intentional, not like every purple-gradient landing page on the internet.

---

## The problem

Vibe coding ships fast.

It also ships **the same UI over and over**:

- Inter everywhere  
- Purple → blue gradients  
- Three identical feature cards  
- Fake AI blob illustrations  
- Copy full of “unleash / seamless / next-gen”

This skill gives your agent a **repeatable design system workflow** instead of guessing aesthetics every time.

---

## Install (Hermes)

```bash
# From the skills hub / direct GitHub
hermes skills install https://raw.githubusercontent.com/norbert351/ui-design-kit/main/SKILL.md

# Or clone + symlink into your profile
git clone https://github.com/norbert351/ui-design-kit.git ~/.hermes/skills/frontend/ui-design-kit
```

Then in chat:

> design a landing page for my product  
> use the design kit  
> professional UI for this dashboard

Hermes loads `ui-design-kit` and follows the workflow.

### Other agents (Claude Code / Cursor / etc.)

Drop `SKILL.md` (and optionally `references/`) into your agent skills folder, or paste the workflow into your project `AGENTS.md` / system instructions.

---

## What’s inside

| Step | What the kit locks |
|------|--------------------|
| 1 | Aesthetic direction (one bold sentence) |
| 2 | Typography — Fontshare / Typewolf (not Inter-only) |
| 3 | Color tokens + contrast (Coolors, Realtime Colors, WebAIM) |
| 4 | Icons — Lucide / Phosphor |
| 5 | Real images — Unsplash / Pexels / unDraw (no blobs) |
| 6 | Motion — Animista + premium easing |
| 7 | Components — restyle, don’t ship stock shadcn purple |
| 8 | Copy — Hemingway + human voice |
| 9 | Ship checks — PageSpeed, favicons, Vercel |

Full free-tool catalog: [`references/resource-catalog.md`](./references/resource-catalog.md)

---

## Default stack

- **Next.js** App Router + TypeScript  
- **Tailwind CSS** + CSS design tokens  
- **Framer Motion** or CSS scroll reveals  
- **Lucide** icons  
- **Recharts** for dashboards  
- Real stock photography  
- **Vercel** deploy  

---

## Anti-AI-slop checklist

Every build should pass:

- [ ] Not Inter-only  
- [ ] No purple-blue mesh default  
- [ ] Varied layout (not only 3-card rows)  
- [ ] Real photos / directed illustrations  
- [ ] Design tokens used  
- [ ] Purposeful motion  
- [ ] Specific product copy  
- [ ] Empty + loading + hover states  

---

## One-shot prompts

**Landing**

> Using ui-design-kit: build a dark luxury SaaS landing (Hero → Features → Showcase → CTA). Fontshare pair, orange accent, Unsplash hero, Lucide icons, scroll reveals. No AI-generic look.

**Dashboard panel**

> Using ui-design-kit: design a fully polished dashboard panel with header, status badges, loading + empty states, and tokenized dark surfaces. UI first — no API wiring yet.

---

## Structure

```
ui-design-kit/
├── SKILL.md                      # Agent skill (workflow + rules)
├── references/
│   └── resource-catalog.md       # Full free tool list (PRIMARY picks)
└── README.md
```

---

## Origin

Curated for production vibe-coding after auditing free resource directories (including [300 free resource websites](https://github.com/Moh4696/300-free-resource-websites) as a safe link catalog). Packaged as a Hermes skill so the stack loads automatically on design work.

---

## License

MIT — free to use, fork, and ship in your agents.

---

## Contributing

PRs welcome for:

- Better free commercial fonts  
- Stronger anti-slop rules  
- Stack notes for Vue / Svelte / pure HTML  
- Extra one-shot recipes  

Keep PRIMARY tools free (or generous free tier) and commercial-safe where possible.
