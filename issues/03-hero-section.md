# 03 — Hero section

## What to build

Create the full-viewport hero component (`src/components/Hero.astro`) as defined in `01-brutalist.html`. The hero is a grid layout containing:

- **Label bar** (top): "Portfolio / 2025" with a blinking typing cursor animation
- **Name display**: "IGNACIO" in Syne 800 weight, huge uppercase, with "GONZALEZ SECADAS" below it. The last name has a glitch effect (CSS `::before`/`::after` pseudo-elements with clip-path animation) that triggers **only on hover** — not constantly
- **Role tags**: Two tags ("Software Developer", "AI Engineer") with staggered entrance animations (slide in from left with delay)
- **Footer bar** (bottom): Location ("Spain / ES") on the left, scroll-down link on the right
- **ASCII decoration**: Decorative ASCII art element

The hero fills `100vh` and uses the grid from the design reference. All animations use CSS only (no JS). Entrance animations fire once on page load.

## Acceptance criteria

- [x] Hero fills the full viewport height
- [x] Name "IGNACIO GONZALEZ SECADAS" renders in Syne 800 at large size
- [x] Glitch effect activates on hover over the last name only — no constant animation
- [x] Role tags ("Software Developer", "AI Engineer") animate in with stagger on page load
- [x] Label bar shows "Portfolio / 2025" with blinking cursor
- [x] Footer bar shows location and scroll-down link
- [x] Section is responsive: stacks vertically on mobile
- [x] No JavaScript used — all animations are CSS

## Blocked by

- 02 — Layout, global CSS, navigation & footer
