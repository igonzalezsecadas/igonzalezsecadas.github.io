---
title: "Why I Built This Site"
date: 2025-04-10
description: "A look at why I chose Astro and a brutalist design for my personal portfolio."
tags: ["Astro", "Web"]
---

I wanted a portfolio that felt like a terminal — something honest and functional, not wrapped in gradient overlays and stock photos. Brutalism as a web design philosophy strips away the unnecessary and puts content first. That matched how I think about code: solve the problem, skip the decoration.

Astro made sense because I don't need a runtime. My site is static content — projects, blog posts, a bit of text about myself. Shipping zero JavaScript by default and building everything at compile time felt right. The content collections API gives me type-safe markdown with frontmatter validation, so I can't accidentally publish a post with a missing date.

The whole thing ships under 10KB of JavaScript on most pages. The custom cursor and scroll-reveal animations are vanilla JS, no framework overhead. The design references `01-brutalist.html` as a single-file prototype I iterated on before splitting it into components.

Building it forced me to think carefully about every pixel. When you can't rely on a design system or component library, you actually understand your own CSS. That's worth the effort.
