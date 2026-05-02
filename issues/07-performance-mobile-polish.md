# 07 — Performance & mobile polish

## What to build

Final performance pass across all components. This is not a new feature — it's ensuring the existing components perform well and degrade gracefully on mobile.

**Disable effects on touch devices**:
- Custom cursor hidden on mobile (already in layout CSS, verify it works)
- CRT scanline overlay opacity reduced or hidden on mobile
- Glitch effect disabled on touch devices
- Hover interactions on project cards disabled on touch (no accent bar animation)

**Scroll reveal optimization**:
- All IntersectionObserver-based reveal animations fire once and disconnect (no re-triggering on scroll back up)
- Verify no animation loops infinitely (except the ticker, which is content)

**Responsive verification**:
- All sections render correctly in a 375px viewport (iPhone SE)
- Navigation collapses or adapts for mobile
- Hero text scales down appropriately
- Project cards stack vertically
- Blog previews stack vertically
- Footer links wrap cleanly

**Performance verification**:
- `npm run build` produces a site that loads in under 2 seconds (verify with a local server)
- Total JS shipped is under 10KB
- No SVG noise filter / film grain present
- No constant animations — only hover-triggered or one-shot entrance

## Acceptance criteria

- [x] Custom cursor does not render on touch devices
- [x] CRT scanline overlay is reduced or hidden on mobile
- [x] No animations loop infinitely (except the hero ticker)
- [x] All scroll reveal animations fire once and disconnect
- [x] All sections render correctly at 375px viewport width
- [x] Navigation works on mobile
- [x] No SVG noise filter / film grain in the build output
- [x] Total JS shipped is under 10KB
- [x] `npm run build` succeeds with no errors
- [x] `npm run build` output can be served and loads cleanly

## Blocked by

- 02 — Layout, global CSS, navigation & footer
- 03 — Hero section
- 04 — About & Skills sections
- 05 — Projects section
- 06 — Blog system
