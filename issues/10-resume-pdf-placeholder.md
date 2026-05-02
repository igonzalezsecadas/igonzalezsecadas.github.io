# 10 — Add resume PDF placeholder

## What to build

Both the About component (`src/components/About.astro`) and the Footer component (`src/components/Footer.astro`) link to `/resume.pdf` for CV download. This file doesn't exist, resulting in broken links. Create a placeholder `public/resume.pdf` file so the links work. This can be a minimal single-page PDF with placeholder text (e.g. "Resume — Ignacio Gonzalez Secadas" with a note that this is a placeholder). Ignacio will replace it with his real CV later.

## Acceptance criteria

- [x] `public/resume.pdf` exists
- [x] Clicking the CV link in the About section opens the PDF in a new tab
- [x] Clicking the Resume link in the Footer opens the PDF in a new tab
- [x] `npm run build` succeeds and `dist/resume.pdf` is present in output

## Blocked by

None — can start immediately
