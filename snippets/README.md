# Code Snippets

Selected reusable patterns from the portfolio source, sanitized
and generalized for reuse in any Next.js 15 project.

| File | Purpose |
|---|---|
| `use-scroll-reveal.ts` | Custom IntersectionObserver hook that flips a boolean when an element enters the viewport. |
| `scroll-reveal-wrapper.tsx` | `<ScrollReveal>` component using the hook, applies CSS transitions. |
| `typewriter-cycle.tsx` | Role-cycling typewriter (typing → waiting → deleting → next) with a state machine. |
| `architecture-diagram.tsx` | SVG flow diagram component — manual node placement on a row/col grid, straight edges. |

## How to use

Each snippet is self-contained with a doc-comment header. Drop
into a Next.js 15 App Router project, adjust styling tokens to
match your design, and import where needed.

## Conventions

- All snippets target Next.js 15 (App Router) with TypeScript.
- Components that use browser APIs are marked `"use client"`.
- Styling uses inline `style={{...}}` or scoped CSS via
  `dangerouslySetInnerHTML` — no Tailwind, no CSS-in-JS library.
- Color tokens (`var(--accent)` etc.) are referenced; define
  these on `:root` in your global stylesheet to match.

## Suggested CSS variables

The snippets reference a small set of design tokens. Add to your
global stylesheet:

```css
:root {
  --bg: #0a0e1a;
  --surface: #131826;
  --border: #1f2937;
  --text-1: #e5e7eb;
  --text-2: #9ca3af;
  --text-3: #6b7280;
  --accent: #00d4a1;
  --accent-dim: rgba(0, 212, 161, 0.1);
  --radius: 8px;
}
```

Adjust values to match your design. The snippets reference the
*names*, not specific colors, so customizing the palette is a
single-file edit.
