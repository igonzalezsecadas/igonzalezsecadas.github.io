# 06 — Blog system

## What to build

Build the complete blog infrastructure: content collection, preview component, index page, and individual post page.

**Content collection config** (`src/content.config.ts`): Define a `blog` collection with schema — `title` (string, required), `date` (date, required), `description` (string, required), `tags` (array of strings, optional). Astro validates at build time.

**Placeholder posts** (`src/content/blog/`):
- `why-i-built-this-site.md` — Tags: Astro, Web
- `learning-ml.md` — Tags: AI, Python
- `docker-for-developers.md` — Tags: DevOps, Docker

Each placeholder has realistic frontmatter and 2–3 paragraphs of placeholder body content.

**Blog previews component** (`src/components/BlogPreviews.astro`): Fetches the 3 latest posts from the blog collection, sorted by date descending. Renders each as a card with title, date, and tags. Includes a "View all posts" link to `/blog`. If no posts exist, the section is hidden.

**Blog index page** (`src/pages/blog/index.astro`): Lists all blog posts from the collection, sorted by date descending. Each entry shows title, date, and tags. Brutalist styling consistent with the main page. Uses the Layout component.

**Blog post page** (`src/pages/blog/[slug].astro`): Renders individual blog posts using `getStaticPaths`. Displays frontmatter (title, date, tags) above the rendered Markdown content. Brutalist typography for prose (Fragment Mono body, Syne headings). "Back to home" link at the top. Uses the Layout component.

## Acceptance criteria

- [x] Content collection schema validates title, date, description, tags at build time
- [x] Three placeholder `.md` files exist in `src/content/blog/` with correct frontmatter
- [x] `npm run build` succeeds — all posts pass schema validation
- [x] Blog previews show the 3 latest posts on the landing page with title, date, tags
- [x] "View all posts" link navigates to `/blog`
- [x] `/blog` index page lists all posts with title, date, and tags
- [x] `/blog/[slug]` renders full post content with brutalist typography
- [x] Blog post pages have a "Back to home" link
- [x] Blog previews component is added to `index.astro` after Projects

## Blocked by

- 01 — Scaffold Astro project with GitHub Pages CI
