## So I Built a Portfolio. Here's How It Works.

Look, every developer needs a corner of the internet that's theirs. And most portfolio sites out there look exactly the same — Tailwind gradient hero, circular headshot, "I'm passionate about building things" boilerplate, smooth scroll that feels like you're gliding through butter you didn't ask for.

I wanted something that felt like *me*. Something that looked like a terminal, felt like a CRT monitor, and didn't pretend to be a SaaS landing page. So I built it.

This is the technical write-up of that thing. Grab a coffee.

---

### The Stack

**Astro 5.x**. That's it. That's the stack.

No React. No Vue. No Svelte. No framework-du-jour. Astro compiles to static HTML at build time and ships zero JavaScript by default. For a portfolio site — a few components, three blog posts, some CSS animations — that's exactly what I need. I don't need a runtime. I don't need hydration. I don't need `useEffect` to make a div move.

The only node dependency is `astro`. One `package.json` line. That's kind of beautiful.

Google Fonts via `@import` in the CSS because I'm not self-hosting font files for a portfolio. Fragment Mono for body text (it's that monospace terminal vibe) and Syne for headings (geometric, bold, not-Inter). Both chosen for character, not safety.

Vanilla CSS. No Tailwind, no Sass, no PostCSS plugins. Just CSS custom properties, a reset, and some `@media` queries. The whole style system is five variables on `:root`:

```css
--bg: #0d0d0b;
--fg: #e8e6e1;
--accent: #20c997;
--dim: #1c1c18;
--border: 3px solid var(--fg);
```

Change those five numbers and the entire site rethemes. No component hardcodes a hex value. That's not a flex — it's just good CSS architecture.

---

### Architecture: What Goes Where

The project is boringly simple, and that's the point.

```
src/
├── layouts/
│   └── Layout.astro        # HTML shell, nav, cursor, CRT overlays
├── pages/
│   ├── index.astro          # Landing page — imports all sections
│   └── blog/
│       ├── index.astro      # Blog archive
│       └── [slug].astro     # Individual post page
├── components/
│   ├── Hero.astro           # Full-viewport intro
│   ├── About.astro          # Bio + CV download
│   ├── Skills.astro         # Language & DevOps tags
│   ├── Projects.astro       # Three project cards
│   ├── BlogPreviews.astro   # Three latest posts from content collection
│   └── Footer.astro         # Terminal-style contact links
├── content/
│   └── blog/                # Markdown files with frontmatter
└── styles/
    └── global.css           # Reset, custom properties, CRT effects
```

Every component is a `.astro` file — Astro's templating language. It's HTML with a frontmatter block (the `---` thing at the top) for any server-side logic, then a `<style>` tag that's automatically scoped. No prop drilling, no state management, no lifecycle hooks. Just content in, HTML out.

The landing page (`index.astro`) literally just imports the six section components and renders them one after another. That's it.

---

### The Brutalist Thing

The design philosophy is documented in the PRD, but here's the short version: **structure is the ornament**.

Everything has a `3px solid` border because borders are honest. They define space explicitly. The grid isn't a hidden layout tool — it's visible, it's structural, and it looks like it could've been drawn with a ruler and a sharpie.

Typography choices are intentional. Fragment Mono reads like code. Syne reads like a poster. There's no rounded corner anywhere on the site. No gradient. No box-shadow. No pretending this is a polished corporate product.

I wrote an entire "Design Philosophy" section in the PRD about this, but the tl;dr is: if it doesn't serve a purpose, remove it. The original design reference had an SVG noise filter for film grain. It tanked performance. Gone. The glitch animation on the last name originally played on loop. CPU hog. Now it's hover-only.

---

### The CRT Effect: How It Works

One of the first things you'll notice is the CRT monitor effect. Three layers, all CSS-only:

**Layer 1 — Scanlines.** A `repeating-linear-gradient` on `body::before` creates horizontal lines every 4 pixels. It's subtle — 45% opacity, black lines 1px thick. Gives the whole page that phosphor display feel.

**Layer 2 — Vignette.** `body::after` has a `radial-gradient` from transparent center to dark edges. Simulates screen curvature. You barely notice it, but without it the page feels flat.

**Layer 3 — Flicker.** A fixed div with an animation that oscillates opacity between 97% and 100% every 150ms. It's nearly imperceptible, but your brain registers it. That's the part that makes it feel like a real CRT that's been running since the '90s.

All three layers are hidden on touch devices because mobile screens don't need simulated CRT artifacts and, frankly, the performance cost isn't worth it on a phone.

---

### The Custom Cursor

Desktop only (hidden on `@media (hover: none)`). A red square (well, teal — the accent color) that follows the mouse with a smaller trailing square that lags behind via a lerp function.

The lerp is `+= (target - current) * 0.15` in a `requestAnimationFrame` loop. Smooth, cheap, no JavaScript animation library needed.

When you hover over links, buttons, project cards, or role tags, the cursor scales up 2x and changes color. The trail does its own thing with a different lerp factor, creating a nice delayed follow effect.

It's the kind of micro-interaction that makes the site feel alive without being distracting. And it's about 30 lines of vanilla JS.

---

### The Glitch Effect (That Doesn't Kill Performance)

The last name "Gonzalez Secadas" has a glitch effect on hover. It works via CSS pseudo-elements:

```css
.hero-name h1 .last::before,
.hero-name h1 .last::after {
  content: attr(data-text);
  /* One slices top, one slices bottom */
  clip-path: polygon(0 0, 100% 0, 100% 35%, 0 35%);
  clip-path: polygon(0 65%, 100% 65%, 100% 100%, 0 100%);
}
```

These pseudo-elements are layered on top of the actual text (which is rendered with `-webkit-text-stroke` for that hollow outline look). On hover, they shift position slightly — a few pixels left, right, up, down — creating that classic digital glitch aesthetic.

The key decision was **hover-only activation**. The original design had it looping continuously. That means the browser recalculates paint every frame for nothing. By triggering it only on hover, the performance cost drops to near zero.

---

### Content Collections: The Blog Engine

Blog posts live in `src/content/blog/` as plain Markdown files with YAML frontmatter. Astro's content collections validate the schema at build time — `title`, `date`, `description` are required, `tags` is optional.

The config file (`src/content.config.ts`) defines the schema once:

```ts
const blog = defineCollection({
  loader: glob({ pattern: '**/*.md', base: './src/content/blog' }),
  schema: z.object({
    title: z.string(),
    date: z.date(),
    description: z.string(),
    tags: z.array(z.string()).optional(),
  }),
});
```

If I publish a post with a missing date, the build fails. No silent bugs, no broken pages in production.

The blog index page fetches all posts and sorts them by date. The landing page previews fetch only the top 3. Individual posts are rendered at build time via `getStaticPaths()`, which generates a static HTML file for each `.md` file.

That means the blog is fully static. No database. No CMS. No API calls. Just Markdown → HTML at build time. The workflow is: write a file, push to GitHub, site updates.

---

### The Three Components That Deserve Mention

**Hero.astro** — Full viewport, CSS grid layout with a label bar at the top, the name in the center-left, role tags on the right, and a footer bar. The role tags have staggered entrance animations (opacity + translateX with `animation-delay`). The "Scroll down" link uses `href="#about"` with `scroll-behavior: smooth` on the HTML element. No JavaScript needed for that.

**About.astro** — Two-column grid. Left column has the "About" label (sticky) and a CV download link. Right column has the headline and paragraphs with scroll-reveal animations. The CV link is always visible while scrolling — it's in the left column with `position: sticky`. Simple, effective.

**Projects.astro** — Three cards in a single-column list. Each has a big number, a name, a description, and technology tags. On hover, the entire card inverts colors (background becomes foreground) and the accent bar reveals. The WIP project ("STime") has an "In Progress" tag in the accent color that survives the hover inversion. The cards use `grid-template-columns: 80px 1fr auto` to align the number, info, and tags.

---

### The JavaScript Budget

Total JS shipped to the browser: under 2KB (gzipped). Three features:

1. **Custom cursor tracking** — `mousemove` event listener + `requestAnimationFrame` lerp loop
2. **Scroll reveal** — One-shot `IntersectionObserver` that adds `.visible` class and unobserves
3. **Active nav highlighting** — Scroll listener that checks section positions and toggles `.active` on nav links

That's it. No jQuery. No GSAP. No Framer Motion. No `npm install animate-on-scroll`. The scroll reveal is literally:

```js
const observer = new IntersectionObserver((entries) => {
  entries.forEach((entry) => {
    if (entry.isIntersecting) {
      entry.target.classList.add('visible');
      observer.unobserve(entry.target);
    }
  });
}, { threshold: 0.15 });
```

One-shot, lightweight, framework-agnostic. Every element with the `.reveal` class gets an opacity + translateY transition. Once visible, it stays visible.

---

### Deployment Pipeline

GitHub Actions. Push to `main`, and the `deploy.yml` workflow kicks off:

1. Checkout the repo
2. Run `withastro/action@v3` — which does `npm ci`, `npm run build`, and uploads the `dist/` folder
3. Deploy to GitHub Pages via `actions/deploy-pages@v4`

The whole thing takes about 30 seconds. The site lives at `username.github.io`. No custom domain, no Cloudflare, no Vercel. Free, fast, done.

```yaml
on:
  push:
    branches: [main]
```

That's the trigger. Simple.

---

### Performance Decisions

I made a few deliberate trade-offs:

- **Removed SVG noise filter.** The original design had a film grain effect via SVG `<filter>`. It caused constant repaints. Removed entirely.
- **Hover-only glitch.** The name glitch animation only runs when you actually hover over the last name. Otherwise it's just a styled element.
- **One-shot scroll reveals.** The `IntersectionObserver` unobserves after the first trigger. No repeated animations.
- **Touch device cutoffs.** CRT overlays, custom cursor, hover effects — all disabled on touch devices via `@media (hover: none)` and `@media (max-width: 768px)`.
- **No images.** The entire site is typography and borders. No hero image, no headshot, no project screenshots. This keeps the initial load to ~30KB of HTML/CSS and a couple of font requests.

The result: the site loads in under a second on 3G. Lighthouse scores are in the high 90s across the board.

---

### What I'd Do Differently

Honestly? Not much. The site does what it needs to do and nothing more. But if I were to iterate:

- **RSS feed** for the blog. Astro has a built-in RSS endpoint. Should add it.
- **Project detail pages.** Right now projects are just cards on the landing page. They deserve standalone write-ups.
- **Better blog prose styles.** The current post content looks decent but could use better spacing for long-form reading.
- **Open Graph images.** Social preview cards would be nice for sharing posts.

But here's the thing — the site is a portfolio, not a product. It doesn't need feature creep. It needs to load fast, look distinctive, and make it easy to see my work and contact me. It does all three.

---

### Final Thoughts

I built this site because I wanted something that felt like it came from a developer, not from a Squarespace template. Brutalism as a design language matched that instinct — honest, structural, unpolished on purpose.

Astro made the implementation trivial. Content collections gave me type-safe Markdown. Vanilla CSS kept the bundle tiny. About 30 lines of JavaScript handle all the interactivity.

If you're a developer reading this and your portfolio is a React SPA that takes 5 seconds to load, consider throwing it away and writing some static HTML. You might enjoy it.

---

*Ignacio Gonzalez Secadas — May 2026*
