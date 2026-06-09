# Design system — rishibhatia.io

Extracted from the live ceroh.ai site (computed styles + stylesheet, 2026-06-09) and
reproduced in Jekyll/SCSS. Source of truth for values: `_sass/_tokens.scss`.

## Color

| Token | Value | Use |
|---|---|---|
| ink | `#1a1a1a` | Headings, body text, dark sections, dark buttons |
| muted | `#666666` | Secondary text, nav links, captions |
| bg | `#ffffff` | Page background |
| bg-alt | `#f5f5f5` | Alternating section background |
| accent | `#f5d04e` | Yellow accent: buttons, step circles, link underlines, dark-section stat numbers |
| accent-hover | `#eec33a` | Button hover (ceroh's `accent-hover`; exact value not exposed, chosen one step deeper) |
| border | `rgba(0,0,0,0.05)` | Header hairline |
| border-strong | `rgba(0,0,0,0.1)` | Card borders, dividers |
| on-dark-muted | `rgba(255,255,255,0.75)` | Body text on dark sections |

## Typography

- **Display:** DM Serif Display 400, letter-spacing −0.025em, line-height 1.1.
  Used for h1/hero (42→64px via clamp), page titles, stat numbers, the wordmark.
- **Sans:** Inter (variable, self-hosted woff2), system fallback.
  h2 32px/700 · h3 20px/700 · body 17px/1.65 · lead 20px muted · labels 13–14px.
- Eyebrow labels: 13px, 600, uppercase, 0.12em tracking, muted.

## Layout & spacing

- Containers: 1000px outer · 780px mid · 680px prose. Gutter 24px.
- Section rhythm: 96px top/bottom on desktop (ceroh `py-24`), 64px mobile.
- Section variants: white → `#f5f5f5` → dark (`#1a1a1a` + 4px accent top border) → full accent CTA.

## Components

- **Buttons:** pill radius; accent bg + ink text, 600 weight; sm `12px 24px / 14px`,
  lg `16px 40px / 16px`; dark variant ink bg + white text.
- **Header:** fixed, `rgba(255,255,255,0.9)` + backdrop blur, 1px `rgba(0,0,0,0.05)` bottom border;
  wordmark in DM Serif; 14px muted links → ink on hover; pill CTA; hamburger under 768px.
- **Numbered steps:** 40px accent circles ("01" 14px/700) + title, kicker, muted body.
- **Cards:** 1px `rgba(0,0,0,0.1)` border, 12px radius, 32px padding, border darkens on hover.
- **Stats:** 3-up grid, DM Serif 48px numbers, 14px muted labels; accent numbers on dark.
- **Bio block:** round 160px photo, name, "Previously: …" line, muted body.
- **Footer:** 1px top border, wordmark + tagline left, muted links right.

## Motion

- `.reveal` on scroll: opacity 0 + translateY(28px) → none, 0.65s `cubic-bezier(0.16,1,0.3,1)`,
  triggered by IntersectionObserver. Fully disabled under `prefers-reduced-motion` and without JS.
- Hovers: 0.2s color/border transitions. Nothing bouncy.

## Decisions / deviations from ceroh.ai

- Body text is ink `#1a1a1a` at 17px (ceroh's 20px muted body suits a sales page; long-form
  reading here wants higher contrast and a tighter measure).
- No dark mode: doubles the QA surface for a site this small; the brand is light.
- `accent-hover` value approximated (not exposed in ceroh's compiled CSS).
- Fonts self-hosted (66KB woff2 total) instead of next/font — faster, no third-party request.
