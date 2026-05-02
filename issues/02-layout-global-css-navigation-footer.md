# 02 — Layout, global CSS, navigation & footer

## What to build

Create the foundational design layer that all pages and components will inherit.

**Global CSS** (`src/styles/global.css`): Define CSS custom properties on `:root` (`--bg: #070707`, `--fg: #e8e6e1`, `--accent: #ff2a2a`, `--dim: #1a1a1a`, `--border: 3px solid var(--fg)`). Add a full CSS reset. Import Google Fonts (Fragment Mono + Syne) via `@import`. Style the CRT scanline overlay (`body::before` with `repeating-linear-gradient`). Style the custom cursor (red square + trail) and hide it on touch devices via `@media (hover: none)`. Define scroll reveal transition classes. Set responsive breakpoints for single-column mobile layout.

**Layout component** (`src/layouts/Layout.astro`): HTML head with meta tags, favicon link, font import, and global CSS import. Render the fixed navigation bar with links to Home, About, Projects, Blog — styled with thick borders and Fragment Mono. Add smooth scroll behavior (`scroll-behavior: smooth` on `html`). Add the cursor elements (`.cursor` + `.cursor-trail` divs) and the CRT scanline overlay. Provide a `<slot />` for page content.

**Navigation JS**: Small vanilla script for cursor tracking (mousemove → position cursor + trail elements), hover state toggling on interactive elements, and active nav link highlighting based on scroll position.

**Footer component** (`src/components/Footer.astro`): Terminal-style output with contact links prefixed by `>`. Links: GitHub, LinkedIn, Email, Resume PDF. Bottom bar with copyright. All styled with Fragment Mono, thick borders, accent color on hover.

## Acceptance criteria

- [x] CSS custom properties are defined on `:root` and no component hardcodes hex values
- [x] Google Fonts (Fragment Mono + Syne) load correctly via `@import`
- [x] CRT scanline overlay renders as a fixed overlay without blocking interaction
- [x] Custom cursor (red square + trail) follows the mouse on desktop
- [x] Custom cursor is hidden on touch devices (`@media (hover: none)`)
- [x] Navigation bar is fixed, has links to Home / About / Projects / Blog, and smooth-scrolls to sections
- [x] Footer has terminal-style contact links (GitHub, LinkedIn, Email, Resume PDF)
- [x] Layout renders correctly on mobile (single column, no cursor, reduced effects)
- [x] Total JS shipped is under 10KB

## Blocked by

- 01 — Scaffold Astro project with GitHub Pages CI
