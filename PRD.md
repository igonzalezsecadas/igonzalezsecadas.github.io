# PRD: Brutalist Portfolio with Astro + GitHub Pages

## Problem Statement

Ignacio needs a personal portfolio website to present himself to recruiters. The site must showcase his skills, projects, and writing in a distinctive visual style (brutalist aesthetic) while being performant, easy to maintain, and hosted for free on GitHub Pages.

Currently, the repo contains only HTML design reference files (`01-brutalist.html`, etc.) that define the visual direction. There is no actual site — no framework, no content, no deployment pipeline.

## Solution

Build a static portfolio site using **Astro 5.x** that translates the `01-brutalist.html` design reference into a production site. The site will be a single scrolling landing page (Hero → About → Skills → Projects → Blog Previews → Contact) plus a blog with Markdown-based content. It will be deployed to GitHub Pages via GitHub Actions.

## User Stories

### Landing Page

1. As a recruiter, I want to see Ignacio's name and role tags immediately on landing, so that I can identify who he is within 3 seconds.
2. As a recruiter, I want to see a scrolling ticker with his name and roles, so that the page feels alive and memorable.
3. As a recruiter, I want the last name to have a glitch effect on hover, so that the brutalist aesthetic is communicated through interaction.
4. As a visitor, I want a custom cursor (red square with trail) on desktop, so that the brutalist identity is consistent across the whole experience.
5. As a mobile visitor, I want the custom cursor disabled on touch devices, so that the site is usable on phones and tablets.
6. As a visitor, I want CRT scanline overlays on the page, so that the brutalist/terminal aesthetic is present without hurting performance.
7. As a visitor, I want smooth scroll navigation from the nav links to each section, so that I can jump to content I care about.
8. As a visitor, I want a fixed navigation bar with links to Home, About, Projects, and Blog, so that I can navigate the page at any scroll position.

### About Section

9. As a recruiter, I want to read a short "About" section with 1-2 paragraphs, so that I understand Ignacio's background and mindset.
10. As a recruiter, I want a visible CV/resume download link in the About section's left label column, so that I can download his CV without hunting for it.
11. As a recruiter, I want the CV link to open a PDF in a new tab, so that I can review it without leaving the site.
12. As a visitor, I want the About section to have the headline "Code. Math. Markets. Always learning.", so that the brutalist punchy tone is established.
13. As a visitor, I want the About text to mention his Associate Degree in Software Development in Spain, so that his current educational status is clear.

### Skills Section

14. As a recruiter, I want to see a Skills section with clearly categorized skills, so that I can quickly assess his technical stack.
15. As a recruiter, I want to see "Languages: Python, C++, Java, SQL" in the skills section, so that I know his programming language proficiency.
16. As a recruiter, I want to see "DevOps: Linux, Docker, Kubernetes, AWS, VPS Hosting, GitHub Workflows, Git" in the skills section, so that I know his infrastructure capabilities.
17. As a visitor, I want the skills displayed as brutalist-styled tags or boxes, so that the visual identity is consistent.

### Projects Section

18. As a recruiter, I want to see 3 project cards, so that I can evaluate the breadth and depth of his work.
19. As a recruiter, I want each project card to show a name, one-line description, and technology tags, so that I can scan projects quickly.
20. As a recruiter, I want to see the "Face Detection System" project — a distributed face recognition service using Docker, AI/ML, and DevOps, so that I understand his AI/infra capabilities.
21. As a recruiter, I want to see the "FPMaxxing" project — a website for FP students in Spain using Full Stack and DevOps, so that I see his ability to build products for real users.
22. As a recruiter, I want to see the "STime" project marked as WIP — a .NET MAUI mobile app port, so that I know he's actively building and has internship experience.
23. As a visitor, I want WIP projects to be visually distinguished (e.g. "In Progress" tag), so that I can differentiate completed work from ongoing work.
24. As a visitor, I want project cards to have hover interactions (accent bar reveal, tag color change), so that the brutalist interactivity is maintained.

### Blog Previews

25. As a recruiter, I want to see previews of the 3 latest blog posts on the landing page, so that I can gauge his technical writing ability.
26. As a recruiter, I want each blog preview to show title, date, and tags, so that I can assess relevance without clicking through.
27. As a visitor, I want the blog previews to link to the full post, so that I can read the content.
28. As a visitor, I want a "View all posts" link that goes to `/blog`, so that I can see the full archive.
29. As a visitor, I want the blog section to use placeholder posts at launch ("Why I Built This Site", "Learning Machine Learning", "Docker for Developers"), so that the section looks complete from day one.

### Blog Pages

30. As a reader, I want a blog index page at `/blog` that lists all posts with title, date, and tags, so that I can browse the full archive.
31. As a reader, I want individual blog post pages at `/blog/[slug]` with brutalist styling, so that the reading experience is cohesive with the rest of the site.
32. As a reader, I want blog posts to be written in Markdown with frontmatter (title, date, description, tags), so that publishing is frictionless.
33. As a reader, I want a "Back to home" link on blog pages, so that I can return to the portfolio easily.
34. As a reader, I want blog post content to have brutalist typography (Fragment Mono body, Syne headings), so that the aesthetic is consistent.

### Contact / Footer

35. As a recruiter, I want terminal-style contact links in the footer (GitHub, LinkedIn, Email), so that I can reach out through my preferred channel.
36. As a recruiter, I want a resume PDF download link in the footer, so that I have a second access point for the CV.
37. As a visitor, I want the footer to look like terminal output (e.g. `> GITHUB: github.com/...`), so that the brutalist aesthetic is maintained to the bottom of the page.

### Performance

38. As a visitor, I want the page to load fast despite the visual effects, so that the experience is smooth on all devices.
39. As a visitor, I want the SVG noise filter (film grain) removed, so that rendering performance is not degraded.
40. As a visitor, I want the glitch animation to only trigger on hover, so that the CPU is not constantly animating.
41. As a visitor, I want scroll-triggered reveal animations to fire once (not loop), so that performance stays consistent as I scroll.
42. As a mobile visitor, I want all performance-heavy effects disabled, so that the site is fast on lower-end devices.

### Deployment

43. As a developer, I want the site deployed to GitHub Pages automatically on push to `main`, so that I don't need to manually deploy.
44. As a developer, I want a GitHub Actions workflow using Astro's official action, so that deployment is reliable and maintained.
45. As a developer, I want the site at `username.github.io` (root URL), so that the URL is clean and memorable.
46. As a developer, I want Google Fonts (Fragment Mono + Syne) loaded via `@import`, so that there's no font file management.

### Blog Content Management

47. As a writer, I want blog posts as `.md` files in `src/content/blog/`, so that I can write in any text editor.
48. As a writer, I want a content collection schema that validates title, date, description, and tags, so that frontmatter errors are caught at build time.
49. As a writer, I want to add new posts by creating a new `.md` file and pushing to git, so that the workflow is git-native.

## Implementation Decisions

### Modules

1. **Layout** — Base Astro layout (`Layout.astro`). Contains HTML head (meta, fonts, favicon), navigation bar, custom cursor elements, CRT scanline overlay, and slot for page content. All pages inherit from this layout.

2. **Global CSS** (`global.css`) — Brutalist theme: CSS custom properties (`--bg`, `--fg`, `--accent`, `--dim`, `--border`), resets, CRT scanline effect, custom cursor styles, ticker animation, glitch keyframes, scroll reveal transitions, responsive breakpoints. Shared across all pages.

3. **Hero Component** (`Hero.astro`) — Full-viewport hero grid. Contains: label bar with typing cursor, name (Syne 800, huge uppercase), last name with glitch pseudo-elements (hover-only), two role tags ("Software Developer", "AI Engineer") with staggered entrance animations, footer bar with location and scroll link, ASCII decoration.

4. **About Component** (`About.astro`) — Two-column grid: left label column ("About" + CV download link), right content column (headline in Syne, two paragraphs in Fragment Mono). CV link is always visible in the left column, persistent while scrolling the about text.

5. **Skills Component** (`Skills.astro`) — Two-column display: "Languages" (Python, C++, Java, SQL) and "DevOps" (Linux, Docker, Kubernetes, AWS, VPS Hosting, GitHub Workflows, Git). Brutalist-styled tags or boxes. Section header styled like other section labels.

6. **Projects Component** (`Projects.astro`) — Section header with project count. Three project cards in a grid: number, name, description, technology tags. Cards have hover interactions (left accent bar reveal, background shift, tag color change). WIP project has an "In Progress" indicator.

7. **BlogPreviews Component** (`BlogPreviews.astro`) — Fetches 3 latest posts from the blog content collection, sorted by date descending. Renders each as a card with title, date, and tags. Includes "View all posts" link to `/blog`. If no posts exist, section is hidden.

8. **Footer Component** (`Footer.astro`) — Terminal-style output: each contact link on its own line prefixed with `>`. Links for GitHub, LinkedIn, Email, Resume PDF. Bottom bar with copyright.

9. **Blog Index Page** (`/blog/index.astro`) — Lists all blog posts from the content collection, sorted by date descending. Each entry shows title, date, and tags. Brutalist styling consistent with the main page.

10. **Blog Post Page** (`/blog/[slug].astro`) — Renders individual blog posts. Uses the Layout component. Displays frontmatter (title, date, tags) above the rendered Markdown content. Brutalist typography for prose (Fragment Mono body, Syne headings). "Back to home" link.

11. **Content Collection Config** (`src/content.config.ts`) — Defines the `blog` collection with a schema: `title` (string, required), `date` (date, required), `description` (string, required), `tags` (array of strings, optional). Astro validates this at build time.

12. **Placeholder Posts** — Three Markdown files in `src/content/blog/`:
    - `why-i-built-this-site.md` — Tags: `Astro`, `Web`
    - `learning-ml.md` — Tags: `AI`, `Python`
    - `docker-for-developers.md` — Tags: `DevOps`, `Docker`

### Design Decisions

- **Color scheme**: Defined as CSS custom properties on `:root` (`--bg`, `--fg`, `--accent`, `--dim`). Changing these 5 values rethemes the entire site. No component hardcodes colors. See 'Color Theming' in Design Philosophy.
- **Default palette**: `--bg: #070707`, `--fg: #e8e6e1`, `--accent: #ff2a2a`, `--dim: #1a1a1a`
- **Typography**: Fragment Mono (body/monospace), Syne (headings/display). Chosen for character, not safety.
- **Borders**: `3px solid var(--fg)` throughout (brutalist signature)
- **Effects**: CRT scanlines (CSS repeating-linear-gradient), custom cursor with trail, glitch on hover only, scroll reveal via IntersectionObserver (one-shot)
- **Responsive**: Single-column layout on mobile, effects disabled on touch devices, cursor hidden on mobile
- **No film grain**: SVG noise filter removed for performance

### Architecture Decisions

- **Static site generation only** — No SSR, no server-side logic. Astro builds to plain HTML/CSS/JS.
- **Content collections** — Blog posts use Astro's content collections for type-safe frontmatter and build-time validation.
- **Vanilla CSS** — No Tailwind, no Sass. All styles in `global.css` + scoped `<style>` tags in components.
- **Minimal JavaScript** — Only for: cursor tracking, scroll reveal (IntersectionObserver), nav scroll behavior. No framework JS shipped to the client.
- **Google Fonts via @import** — No self-hosting. Simple, works on GitHub Pages.

### Deployment

- **Repo**: `username.github.io` on GitHub
- **CI**: GitHub Actions with `withastro/action@v3`
- **Trigger**: Push to `main` branch
- **Output**: Static files in `dist/`, deployed to GitHub Pages
- **Base**: `/` (root URL)

## Testing Decisions

This is a static portfolio site with no runtime logic, so testing is focused on **build correctness** and **content integrity** rather than unit tests.

### What makes a good test here

- A good test verifies that the site builds without errors and that content renders correctly.
- We do NOT test CSS styling, visual appearance, or animation behavior — those are verified by opening the site in a browser.
- We do NOT test component internals — only that the build produces valid HTML.

### Testing approach

1. **Build test** — `npm run build` succeeds without errors. This validates:
   - Content collection schema is satisfied by all blog posts
   - All components render without runtime errors
   - All pages generate correctly

2. **No unit tests for components** — The components are Astro templates with no business logic. Testing them would be testing Astro's template engine, not our code.

3. **Manual verification** — After build, open `dist/index.html` in a browser to verify:
   - All sections render
   - Blog posts appear in previews
   - Links work (blog, CV, contact)
   - Responsive layout works on mobile viewport

### Prior art

- This is a greenfield project. No existing test infrastructure.
- The HTML design reference files (`01-brutalist.html`, etc.) serve as the visual specification.

## Out of Scope

- **CMS integration** — No headless CMS (Notion, Sanity, etc.). Posts are Markdown files committed to git.
- **Analytics** — No Google Analytics, Plausible, or similar. Can be added later.
- **SEO beyond basics** — No sitemap generation, no structured data, no Open Graph images. Astro handles basic meta tags.
- **Dark/light mode toggle** — The site uses a single dark theme. No light mode. Palette experimentation is done by editing CSS custom properties, not via a runtime toggle.
- **Internationalization** — English only. No i18n support.
- **Contact form** — No serverless function or form handler. Contact is via direct links (email, LinkedIn).
- **Project detail pages** — Projects are single cards on the landing page. No individual project pages with writeups.
- **Image optimization** — No images in v1. If added later, Astro's built-in `<Image />` component handles optimization.
- **Custom domain** — Staying on `username.github.io`. No CNAME or domain purchase.
- **Accessibility audit** — We'll use semantic HTML and reasonable contrast, but no formal WCAG audit in v1.

## Further Notes

### Design Philosophy

This site follows the **brutalist** aesthetic — a design language rooted in rawness, structural honesty, and deliberate anti-polish. Every design decision must serve this philosophy. If a choice feels 'safe' or 'generic', it's wrong.

#### Core Principles

1. **Intentionality over intensity.** Brutalism doesn't mean 'make it ugly.' It means every element is deliberately exposed — structure is the ornament. Borders are visible because structure matters. Monospace fonts are used because code is the medium. Nothing is hidden behind polish.

2. **Typography as identity.** Fragment Mono and Syne are not default choices. They were selected because Fragment Mono evokes terminal/code culture (brutalist) and Syne is geometric, bold, and uncommon (not Inter, not Roboto, not Arial). Typography should feel chosen, not inherited.

3. **Color as signal, not decoration.** The accent color (`--accent`) exists to draw attention to interactive elements and key information — not to look pretty. It should appear sparingly: role tags, hover states, links, the ticker. The dominant palette is dark (`--bg`) with near-white text (`--fg`). The accent is a scalpel, not a paintbrush.

4. **Motion with purpose.** Animations exist for two reasons: (a) entrance — staggered reveals create rhythm as you scroll, and (b) interaction — hover effects communicate clickability. No animation should loop forever (except the ticker, which is content, not decoration). No animation should exist 'because it looks cool.' If removing it doesn't lose something, remove it.

5. **Spatial composition is content.** The grid isn't a container — it's part of the design. Thick borders (`3px solid`) define space explicitly. The left label column in the About section isn't decorative — it anchors the reader. White space is not empty; it's a decision to let content breathe.

6. **Interaction is texture.** The custom cursor, the glitch on hover, the accent bar reveal on project cards — these aren't gimmicks. They're the tactile layer that makes the brutalist feel alive. Without them, the page is just a dark monospace document. With them, it's an experience.

7. **Performance is respect.** Heavy effects that slow the page down are disrespectful to the visitor. The original design had SVG noise filters and constant glitch animations that tanked performance. We removed them. Brutalism is honest — and honest design doesn't waste the visitor's CPU.

#### What Brutalism Is NOT

- **Not 'ugly on purpose.'** The site should look striking, not broken.
- **Not 'no design.'** Brutalism is a highly intentional design system. Every border, every spacing choice, every font weight is deliberate.
- **Not 'dark mode + monospace.'** Those are surface traits. The philosophy is about structural honesty — showing the skeleton, not hiding it behind rounded corners and gradients.
- **Not fixed.** The palette can be changed. The fonts can be swapped. But the principles (intentionality, structural visibility, purposeful motion) must persist.

#### Color Theming

All colors are CSS custom properties on `:root`:

```css
:root {
  --bg: #070707;     /* Background — the void */
  --fg: #e8e6e1;     /* Foreground — near-white text */
  --accent: #ff2a2a;  /* Signal color — red, used sparingly */
  --dim: #1a1a1a;     /* Subtle surfaces — borders, muted areas */
}
```

No component hardcodes hex values. To change the palette, edit these 4 variables and the entire site rethemes. Examples:

- **Green terminal**: `--accent: #00ff41` (matrix green)
- **Amber CRT**: `--accent: #ffb000` (warm amber)
- **Electric blue**: `--accent: #00b4d8` (cold, technical)
- **High contrast**: `--bg: #000000`, `--fg: #ffffff` (maximum punch)

This is a developer's site. Editing CSS variables to experiment with palettes is the intended workflow — not a UI toggle.

### Design Reference

The `01-brutalist.html` file in the repo is the **authoritative visual specification**. Every design decision (colors, fonts, spacing, animations, layout) should be derived from that file. The other HTML files (`03-editorial.html`, `10-swiss.html`, etc.) are alternative explorations and should NOT be referenced during implementation.

### Performance Budget

The original HTML reference had performance issues due to:
- SVG noise filter (film grain) — **removed**
- Constant glitch animations — **changed to hover-only**
- Multiple `position: fixed` overlays — **reduced to scanlines only**

The final site should load in under 2 seconds on a 3G connection. Total JS shipped should be under 10KB (just cursor + IntersectionObserver + nav behavior).

### Content Ownership

Ignacio owns all content (project descriptions, about text, blog posts). The placeholder blog posts are seeds that he will replace with real content over time.

### Future Enhancements (Not in this PRD)

- Project detail pages with technical writeups
- Blog tags filter/archive page
- Dark/light mode toggle (runtime switch, not just CSS variable edit)
- Analytics integration
- Custom domain migration
- RSS feed for the blog
- Palette presets shipped as CSS classes (e.g. `.theme-green`, `.theme-amber`) for quick switching without editing CSS
