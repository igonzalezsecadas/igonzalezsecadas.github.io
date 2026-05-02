# 05 — Projects section

## What to build

Create the projects component (`src/components/Projects.astro`) that displays three project cards on the landing page.

**Section header**: "Projects" label with project count ("03").

**Project cards** (grid layout, one per row or responsive grid):
1. **Face Detection System** — Distributed face recognition service. Tags: Docker, AI/ML, DevOps
2. **FPMaxxing** — Website for FP students in Spain. Tags: Full Stack, DevOps
3. **STime** — .NET MAUI mobile app port. Tags: .NET MAUI, Mobile. **Marked as WIP** with an "In Progress" indicator

**Card structure**: Number (01, 02, 03), project name, one-line description, technology tags as styled pills/boxes.

**Hover interactions**: Left accent bar slides in on hover, background shifts slightly, tag colors change to accent. All CSS transitions, no JS.

**WIP indicator**: STime card has a visual "In Progress" tag or badge to distinguish it from completed projects.

## Acceptance criteria

- [x] Section header shows "Projects" with count "03"
- [x] Three project cards render: Face Detection System, FPMaxxing, STime
- [x] Each card shows number, name, description, and technology tags
- [x] Technology tags are: Docker/AI/ML/DevOps, Full Stack/DevOps, .NET MAUI/Mobile respectively
- [x] STime card has a visible "In Progress" / WIP indicator
- [x] Hover: left accent bar slides in, background shifts, tag colors change
- [x] All hover effects are CSS transitions (no JS)
- [x] Section has one-shot scroll reveal animation
- [x] Section is responsive on mobile
- [x] Component is added to `index.astro` after Skills

## Blocked by

- 02 — Layout, global CSS, navigation & footer
