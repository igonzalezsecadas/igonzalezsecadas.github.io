# 04 — About & Skills sections

## What to build

Create two content sections that sit below the hero on the landing page.

**About component** (`src/components/About.astro`):
- Two-column grid layout: left label column, right content column
- Left column: Section label "About" + a CV/resume download link (opens PDF in new tab). The label column is sticky or persistent — it stays visible while the content scrolls
- Right column: Headline "Code. Math. Markets. Always learning." in Syne, followed by 1–2 paragraphs in Fragment Mono describing Ignacio's background. Must mention his Associate Degree in Software Development in Spain
- Styled with thick borders, brutalist spacing, scroll-triggered reveal animation (one-shot)

**Skills component** (`src/components/Skills.astro`):
- Two-column display with section header "Skills"
- Left column: "Languages" — Python, C++, Java, SQL
- Right column: "DevOps" — Linux, Docker, Kubernetes, AWS, VPS Hosting, GitHub Workflows, Git
- Skills displayed as brutalist-styled tags or boxes with borders
- Scroll-triggered reveal animation (one-shot)

Both components should use the CSS custom properties from `global.css` and follow the brutalist design from `01-brutalist.html`.

## Acceptance criteria

- [x] About section has two-column grid: label + content
- [x] CV download link is visible in the About left column and opens a PDF in a new tab
- [x] About headline reads "Code. Math. Markets. Always learning."
- [x] About text mentions Associate Degree in Software Development in Spain
- [x] Skills section shows "Languages" and "DevOps" as two columns
- [x] Languages: Python, C++, Java, SQL
- [x] DevOps: Linux, Docker, Kubernetes, AWS, VPS Hosting, GitHub Workflows, Git
- [x] Skills are styled as bordered tags/boxes
- [x] Both sections have one-shot scroll reveal animations
- [x] Both sections are responsive (stack on mobile)
- [x] Both sections are added to `index.astro` in the correct order (Hero → About → Skills)

## Blocked by

- 02 — Layout, global CSS, navigation & footer
