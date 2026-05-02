# 09 — Add favicon

## What to build

Create a `public/` directory and add a `favicon.svg` file. The Layout component (`src/layouts/Layout.astro`) already references `/favicon.svg` in the `<head>`, but no file exists. The favicon should be a simple brutalist-styled SVG — e.g. the initials "IG" in Syne-style letterforms on a dark background, or a minimal geometric mark using the accent color (`--accent: #ff2a2a`). Keep it under 1KB.

## Acceptance criteria

- [x] `public/favicon.svg` exists
- [x] Layout's `<link rel="icon" type="image/svg+xml" href="/favicon.svg" />` resolves correctly in the built site
- [x] Favicon renders in browser tab
- [x] `npm run build` succeeds and `dist/favicon.svg` is present in output

## Blocked by

None — can start immediately
