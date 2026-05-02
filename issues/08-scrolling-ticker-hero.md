# 08 — Add scrolling ticker to hero section

## What to build

Add a scrolling marquee ticker to the Hero component (`src/components/Hero.astro`) as defined in the `01-brutalist.html` design reference. The ticker is a horizontally-scrolling strip that displays "IGNACIO GONZALEZ SECADAS" repeated multiple times, separated by accent-colored markers. It scrolls continuously left using a CSS `@keyframes` animation.

The ticker sits inside the hero section (positioned at the bottom of the hero grid or as a full-width strip). It pauses on hover. Text is styled in Fragment Mono, uppercase, with accent color. The animation is CSS-only (infinite linear scroll) — this is content, not decoration, so the infinite loop exception in the performance rules applies here.

Reference: grep for `.ticker` in `01-brutalist.html` for the exact implementation pattern.

## Acceptance criteria

- [x] Hero section contains a scrolling ticker strip with the name "IGNACIO GONZALEZ SECADAS" repeated
- [x] Ticker scrolls continuously left via CSS animation (infinite, linear)
- [x] Ticker pauses on hover
- [x] Text is styled with Fragment Mono, uppercase, accent color
- [x] Ticker is CSS-only — no JavaScript
- [x] Ticker is responsive: visible on all viewport sizes
- [x] `npm run build` succeeds

## Blocked by

None — can start immediately
