# 01 — Scaffold Astro project with GitHub Pages CI

## What to build

Set up the Astro 5.x project from scratch inside the existing repo. Initialize `package.json`, install Astro, configure `astro.config.mjs` for static output with `/` as the base path. Create the `src/` directory structure (`src/pages/`, `src/layouts/`, `src/components/`, `src/content/`, `src/styles/`). Add a minimal `src/pages/index.astro` that renders "Hello" to prove the build works. Set up a GitHub Actions workflow (`.github/workflows/deploy.yml`) using `withastro/action@v3` that builds and deploys to GitHub Pages on push to `main`. Copy the `01-brutalist.html` design reference into a `public/` or `docs/` folder so it remains accessible but doesn't interfere with the build.

## Acceptance criteria

- [x] `npm run build` produces static HTML in `dist/`
- [x] `npm run dev` starts a local dev server
- [x] `astro.config.mjs` sets `site` to `https://username.github.io` and `base` to `/`
- [x] `.github/workflows/deploy.yml` triggers on push to `main`, builds, and deploys to GitHub Pages
- [x] Directory structure matches: `src/pages/`, `src/layouts/`, `src/components/`, `src/content/`, `src/styles/`
- [x] `01-brutalist.html` is preserved in the repo (not deleted)

## Blocked by

None — can start immediately
