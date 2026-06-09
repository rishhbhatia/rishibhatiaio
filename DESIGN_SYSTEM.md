# Design system — rishibhatia.io

Originally extracted from the live ceroh.ai site (computed styles, 2026-06-09), then
deliberately diverged (same day, on request) into a quieter, editorial personal-site
look. Kept from ceroh: the type pairing, spacing rhythm, containers, fixed blurred
header, and reveal motion. Dropped: the yellow accent, pill buttons, alternating
grey/dark marketing sections, and boxed cards. Source of truth: `_sass/_tokens.scss`.

## Color

| Token | Value | Use |
|---|---|---|
| ink | `#1a1a1a` | Headings, body text, button hover fill |
| muted | `#666666` | Secondary text, nav links, captions |
| bg | `#ffffff` | Page background (the whole site is white) |
| bg-alt | `#f5f5f5` | Code blocks only |
| accent | `#b85c38` | Terracotta: link underlines, step numerals, selection, blockquote rule, OG bar, favicon |
| accent-hover | `#9e4a2b` | Accent hover |
| border | `rgba(0,0,0,0.05)` | Header hairline |
| border-strong | `rgba(0,0,0,0.1)` | Section/row dividers, glance table rules |

## Typography

- **Display:** DM Serif Display 400, letter-spacing −0.025em, line-height 1.1.
  Used for h1/hero (42→64px clamp), page titles, work-entry titles (26→34px clamp),
  stat numbers, step numerals, the wordmark.
- **Sans:** Inter (variable, self-hosted woff2), system fallback.
  h2 32px/700 · h3 20px/700 · body 17px/1.65 · lead 20px muted · labels 13–14px.
- Eyebrow labels: 13px, 600, uppercase, 0.12em tracking, muted.

## Layout & spacing

- Containers: 1000px outer · 780px mid · 680px prose. Gutter 24px.
- Section rhythm: 96px top/bottom desktop, 64px mobile.
- Sections are all white, separated by full-width 1px `rgba(0,0,0,0.1)` hairlines
  (`.section--line`) — editorial page, not marketing bands.

## Components

- **Links:** `.text-link` — 600 weight ink with 2px terracotta underline, ink on hover.
  Primary actions are arrow text-links, not buttons.
- **Button** (`.btn`, used sparingly — 404): 1px ink border, 8px radius, transparent;
  inverts to ink/white on hover.
- **Header:** fixed, `rgba(255,255,255,0.9)` + backdrop blur, hairline bottom border;
  DM Serif wordmark; 14px muted links (Work / Writing / About / Contact) → ink on
  hover; hamburger under 768px. No CTA button.
- **Work entries:** borderless editorial rows in `.work-list` (hairline between rows):
  uppercase tag, DM Serif title (accent underline on hover), muted outcome, arrow.
- **Numbered steps:** typographic DM Serif numerals ("01") in terracotta + title and
  muted body. No badges or circles.
- **Stats:** 3-up grid, DM Serif 48px ink numbers, 14px muted labels.
- **Bio block:** round 160px photo, name, "Previously: …" line, muted body.
- **Footer:** hairline top border, wordmark + tagline left, muted links right.

## Motion

- `.reveal` on scroll: opacity 0 + translateY(28px) → none, 0.65s `cubic-bezier(0.16,1,0.3,1)`,
  IntersectionObserver. Fully disabled under `prefers-reduced-motion` and without JS.
- Hovers: 0.2s color/border transitions. Nothing bouncy.

## Decisions

- Terracotta `#b85c38` replaced ceroh's yellow `#f5d04e` as the single accent —
  warmer and personal, and the strongest visual separator from ceroh.ai.
- Body text is ink at 17px (long-form reading wants contrast and a tight measure).
- No dark mode: doubles the QA surface for a site this small; the brand is light.
- Fonts self-hosted (66KB woff2 total) — faster, no third-party request.
