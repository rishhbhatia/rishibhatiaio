# Redesign log — rishibhatia.io

Running record of decisions and changes for the 2026 redesign. Goal: turn the
2022 Jekyll blog into a clear, minimal, credible portfolio that reads as a
sibling of ceroh.ai. Built autonomously by Claude Code, 2026-06-09.

## Phase 0 — Audit

- Repo: this directory (`gh-pages` branch, GitHub Pages, CNAME `www.rishibhatia.io`).
- Old stack: Jekyll + `rishhbhatia/swiss` remote theme. Build worked locally (Ruby 2.7, github-pages ~225).
- URLs to preserve (all verified in new build):
  - `/` · `/about/` · `/writing/` · `/404.html` · `/feed.xml`
  - `/writing/2022/08/23/why-am-i-starting-my-website.html`
  - `/writing/2022/11/14/so-you-want-to-build-your-data-stack.html`
- Case studies found on disk at `~/Downloads/Case_Studies_Rishi_Bhatia.pdf`
  (Crisis Maps + Roblox Live-Ops); read in full before designing the template.
- There was an uncommitted edit to the 2022 "Why am I starting my website" post
  (removed a stray heading, added an image). Kept — the image URL still resolves (200).

## Phase 1 — Design system (see DESIGN_SYSTEM.md)

- Tokens extracted from the live ceroh.ai via headless browser (computed styles),
  not from memory: DM Serif Display + Inter, #1a1a1a / #666 / #fff / #f5d04e / #f5f5f5,
  pill buttons, 96px section rhythm, 1000/780/680px containers, 0.65s expo reveal.
- Fonts self-hosted (latin woff2, 66KB total).
- Decision: stayed on Jekyll per brief. Rebuilt the theme from scratch; removed
  `remote_theme` and `jekyll-remote-theme`.

## Phase 2 — Information architecture

- Home (hero → selected work → how I work → writing → about teaser → contact)
- Work `/work/` (collection `work`, two case studies at `/work/<name>/`)
- About `/about/` · Writing `/writing/` (unchanged URLs) · contact via footer + dark CTA section.

## Phases 3–5 — Build

- New layouts: `default`, `page`, `post`, `case-study`; `category-post` and
  `category_index` kept as names so existing post front matter is untouched.
- Posts migrated with content untouched, two exceptions (documented):
  - Fixed a malformed markdown link in the 2022 post (`]([https://` → `](https://`) — it rendered broken.
  - Added `image:` front matter to both posts for per-page OG images (metadata only).
- Case studies hand-built in HTML against the component system: stat row,
  at-a-glance table, numbered approach steps, prose sections. Copy taken from the
  PDFs nearly verbatim; no metrics invented.
- About rewritten first-person: ceroh narrative + career path + SF/human details.
  Mentions Ceroh by name (it's public on ceroh.ai).

## Phase 6 — Polish

- SEO: `jekyll-seo-tag` (titles, descriptions, canonical, OG, twitter cards,
  JSON-LD), `jekyll-sitemap`, `jekyll-feed` (RSS at /feed.xml, writing category).
- Canonical host set to `https://www.rishibhatia.io` to match CNAME (old config
  said apex; the served host is www).
- Per-page OG images generated from a branded template (tools/og-template.html)
  via headless Chromium: default, about, work, writing, both case studies, both posts.
- Favicon: SVG monogram; apple-touch-icon PNG generated from tools/icon.html.
- Motion: IntersectionObserver `.reveal` (ceroh's exact curve); fully disabled
  under `prefers-reduced-motion` and no-JS (content never hidden).
- A11y: skip link, focus-visible outlines, aria-current nav, aria-expanded on
  the mobile toggle, semantic landmarks, alt text.

## Deliberate choices / skipped items

- **No dark mode** — doubles QA surface for a tiny site; brand is light.
- **No analytics** — per brief, not added without approval. Recommendation if
  wanted: GoatCounter or Plausible (both privacy-respecting, no cookie banner).
- **No Jekyll→Next.js migration** — Jekyll reproduces the design fully and
  preserves URLs/hosting for free.
- `tools/` is excluded from the build; it holds the OG/icon generators.

## Open items

- (none blocking — see final summary)
