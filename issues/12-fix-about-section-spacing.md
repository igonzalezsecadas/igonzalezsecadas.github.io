# 12 — Fix excessive spacing below About section

## What to build

The About section (`src/components/About.astro`) has too much empty space between its text content and the Skills section below. The root cause is the `min-height: 60vh` on `.about` — the actual content (headline + 2 paragraphs) doesn't fill that height, leaving a large dead zone.

Remove the `min-height: 60vh` constraint so the section sizes to its content. Also review the `.about-label` sticky column (`height: 100vh`) — it should only be as tall as the grid row, not the full viewport, to avoid stretching the section unnecessarily.

## Acceptance criteria

- [x] `.about` no longer has `min-height: 60vh`
- [x] About section height is determined by its content, not a fixed minimum
- [x] The gap between About text and the Skills section is tight and intentional
- [x] Sticky label column still works correctly on desktop (sticks while content scrolls)
- [x] Layout is not broken on mobile
- [x] `npm run build` succeeds

## Blocked by

None — can start immediately
