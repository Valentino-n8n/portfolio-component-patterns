# Portfolio Component Patterns

A reference for building a personal developer portfolio in Next.js 15 —
without Framer Motion, without a UI library, without a CMS.

This repository documents the reusable component and hook patterns
behind [valentinoveljanovski.de](https://valentinoveljanovski.de). The
portfolio is itself a public site — what's documented here is the **why**
behind specific implementation choices, plus the generic,
copy-paste-ready versions of the components that aren't tied to my
content.

> The full source code of the portfolio website is not published here.
> This repository contains documentation and selected pattern snippets,
> not a clone-and-deploy template. The content (case studies, copy,
> project lists) is mine, lives at the live URL, and is not
> re-distributed.

---

## What this repo documents

A lot of "developer portfolio templates" lean hard on Framer Motion,
shadcn/ui, and one of a dozen template repos. The portfolio this repo
references deliberately does none of that. It uses:

- **Custom IntersectionObserver hook** instead of Framer Motion —
  lighter bundle, no animation library dependency, full control over
  timing.
- **Custom SVG architecture diagrams** instead of a charting library —
  every case study has a unique flow, generic chart components don't
  fit, drawing in SVG is faster than fighting a generic API.
- **State-machine typewriter** instead of a typewriter library — it's
  ~30 lines of TypeScript, supports cycling through multiple strings
  with typing/waiting/deleting phases.
- **Consistent 9-section case study layout** instead of a CMS — each
  case study is a `.tsx` file that imports a small set of primitives.
  New case studies copy the structure; deviations are intentional.

The patterns documented here are the parts that another developer might
want to lift for their own portfolio without dragging in the specific
content.

---

## Repository structure

```
.
├── README.md                              ← you are here
├── package.json                           ← dependency reference
├── tsconfig.json                          ← TypeScript config
├── .gitignore
├── docs/
│   ├── architecture.md                    ← Next.js 15 App Router shape
│   ├── intersection-observer-reveal.md    ← scroll-reveal without Framer
│   ├── case-study-layout-pattern.md       ← 9-section structure
│   └── svg-architecture-diagrams.md       ← custom flow diagrams in SVG
└── snippets/
    ├── README.md
    ├── use-scroll-reveal.ts               ← custom IntersectionObserver hook
    ├── scroll-reveal-wrapper.tsx          ← <ScrollReveal> wrapper component
    ├── typewriter-cycle.tsx               ← role-cycling typewriter
    └── architecture-diagram.tsx           ← SVG flow diagram component
```

---

## Tech stack

- **Framework:** Next.js 15 (App Router)
- **Language:** TypeScript
- **Styling:** Inline CSS variables (no Tailwind, no CSS-in-JS library) —
  uses CSS custom properties on `:root` and `style={{...}}` props
- **Animation:** Native IntersectionObserver + CSS transitions
- **Hosting:** Vercel

The "no Tailwind" choice surprises people. The reasoning: a portfolio is
mostly long-form text, not utility-heavy UI. Inline styles plus a small
set of CSS variables for the design tokens gives full type-safety with
zero build-tool friction. For a UI component library, Tailwind would be
the right answer; for a portfolio, it isn't.

---

## What this repo does NOT contain

Scope of this repository:

- **The case study content.** Every case study on the live site is a
  hand-written `.tsx` file with detailed architecture documentation.
  Those files live in the private portfolio repo and are not republished
  here. They link back to *other* public pattern repositories that
  contain code snippets and architecture documentation.
- **The Hero copy, About copy, contact form copy.** These are personal
  content.
- **CV PDF.** Lives at the live site under `/valentino-veljanovski-cv.pdf`.
- **Custom assets.** Logos, illustrations, fonts.

---

## About

Built by [Valentino Veljanovski](https://valentinoveljanovski.de),
automation developer based in München. The case study for this portfolio
is at
[valentinoveljanovski.de/projects/portfolio](https://valentinoveljanovski.de/projects/portfolio).

Companion repositories cover related patterns:

- [`Valentino-n8n/DISPO`](https://github.com/Valentino-n8n/DISPO) —
  Microsoft 365 + DocuSign + AI-assisted operations
- [`Valentino-n8n/Reklamation`](https://github.com/Valentino-n8n/Reklamation) —
  Slack-based case management
- [`Valentino-n8n/BauScope-Control-Center`](https://github.com/Valentino-n8n/BauScope-Control-Center) —
  Role-based Slack platform with DocuSign HMAC
- [`Valentino-n8n/BauScope-3D`](https://github.com/Valentino-n8n/BauScope-3D) —
  Next.js B2B landing page patterns
- [`Valentino-n8n/static-corporate-site-patterns`](https://github.com/Valentino-n8n/static-corporate-site-patterns) —
  PHP + Apache + service worker patterns

---

## Viewing Notice

This repository is published for portfolio demonstration and educational
viewing only.

All code, documentation, diagrams, and content in this repository remain
the intellectual property of the author. **All rights reserved.**

No license is granted, expressed or implied, for reuse, redistribution,
modification, or commercial use of any material in this repository
without prior written permission from the author.

For licensing or collaboration inquiries, contact: <valentinoveljanovski@outlook.com>