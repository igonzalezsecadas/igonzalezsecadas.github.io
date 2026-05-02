# 11 — Add article preview section

## Parent

This is a new feature not covered by the PRD.

## What to build

Add a dedicated article preview section to the landing page that surfaces the 3 latest blog posts. This section should sit between Projects and Footer (or wherever makes sense in the page flow). Each preview card shows the post title, a short excerpt or description, date, and tags. Cards link through to the full post at `/blog/[slug]`. Include a "View all posts" link that navigates to `/blog`.

The section follows the brutalist design language: thick borders, Fragment Mono body text, Syne headings, accent-colored hover interactions, one-shot scroll reveal animations. If no posts exist, the section is hidden.

## Acceptance criteria

- [x] Section displays the 3 latest blog posts as preview cards
- [x] Each card shows title, description/excerpt, date, and tags
- [x] Cards link to the full post at `/blog/[slug]`
- [x] "View all posts" link navigates to `/blog`
- [x] Section is hidden when no posts exist
- [x] Brutalist styling consistent with the rest of the site
- [x] One-shot scroll reveal animation
- [x] Responsive: stacks on mobile
- [x] `npm run build` succeeds

## Blocked by

None — can start immediately
