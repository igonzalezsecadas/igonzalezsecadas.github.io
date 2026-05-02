## Parent

None. This is a standalone design polish issue.

## What to build

Keep the brutalist philosophy and site structure intact, but surgically remove the specific visual patterns that make it instantly recognizable as LLM-generated. The goal is not a new aesthetic — it is to make the *same* aesthetic feel authored, not generated.

### What to keep

- Brutalist philosophy: raw structure, exposed grids, thick borders, monospace/code culture
- Site structure: Hero → About → Skills → Projects → Blog → Footer
- Ticker strip, glitch hover on last name, scroll reveals, custom cursor + trail, CRT scanlines
- Content and copy exactly as-is
- The border-heavy layout language and section container widths

### What to change (the slop)

**1. Typography — the #1 signal**

Replace `Syne + Fragment Mono` with a pairing no LLM defaults to for "brutalist portfolio":
- **Heading/display font**: Replace Syne with something that has actual character and is NOT geometric. Suggestions: `Space Grotesk` (quirky, slightly off), `Clash Display` or `Archivo` (narrow, aggressive), `Bebas Neue` (condensed, punchy). Or commit harder: use a single font family for everything (e.g., `JetBrains Mono` at massive scale for headings too — no "heading font / body font" dichotomy at all).
- **Body font**: If keeping a pairing, replace Fragment Mono with something less "default developer portfolio." `IBM Plex Mono` is slightly more distinctive. Or go serif for body: `Source Serif 4` or `Literata` against monospace headings creates tension that LLMs avoid.

**2. Color — kill the dark-void-red formula**

The `#070707` + `#ff2a2a` combination is the single most common LLM portfolio palette. Change it without losing edge:
- Keep dark background but shift it: `#0a0a0a` → something with a tint (deep charcoal `#1a1a1a`, near-black with warmth `#0d0d0b`, or even a very dark desaturated navy `#0a0f14`).
- Replace the red accent with something an LLM wouldn't pick: burnt orange `#e85d04`, acid yellow `#ccff00`, electric violet `#7b2cbf`, pale mint `#00f5d4`, or even pure white `#ffffff` as the only accent. Pick ONE and commit.
- If the accent changes, every instance of `var(--accent)` must update cohesively.

**3. Section labels — the `letter-spacing: 0.3em; text-transform: uppercase; font-size: 0.7rem; color: var(--accent)` cliché**

This exact style appears in every LLM brutalist site. Change ALL section headers (About, Skills, Projects, Blog) to something authored:
- Option A: Large, bold, lowercase or sentence-case labels at normal tracking (e.g., `about` in 1.5rem bold, no letter-spacing, no uppercase)
- Option B: Numeric-only labels (`01`, `02`, `03`) at massive scale, with the word itself de-emphasized or removed
- Option C: Vertical text on desktop (rotated 90°) for the label column
- Option D: No labels at all — let the content speak, separated only by borders

**4. Footer — kill the terminal LARP**

`> CONTACT_LINKS:` / `> BUILD_SUCCESSFUL. EXIT CODE: 0` is pure LLM slop. Every generated terminal footer looks like this.
- Replace with something that still feels brutalist but isn't pretending to be a shell. Options:
  - A simple typographic block: contact links as plain underlined text, stacked vertically with generous leading
  - A grid of links with no decoration other than borders
  - A single line of text at the bottom edge, like a print colophon
  - The word "Contact" at massive scale with links tucked underneath

**5. Skill tags — kill the bordered pill**

`border: 2px solid var(--dim); padding: 0.45rem 1rem; font-size: 0.7rem; text-transform: uppercase` — this exact pill component is generated in every portfolio.
- Replace with a plain typographic list: skills written as comma-separated text, or stacked with no borders, or displayed in a multi-column text block with no chrome at all.
- If tags must exist, make them unpredictable: no border, no padding, just text with a `/` or `•` separator, or massive text at low opacity.

**6. Project cards — kill the hover-accent-bar-reveal**

`::before { width: 4px; height: 0; }` → `hover::before { height: 100% }` is a default LLM hover pattern.
- Redesign the hover state to something else: background inversion (bg becomes fg, text becomes bg), a strike-through or underline animation, a slight rotation or offset, or simply a color shift without the bar.
- Or remove hover effects entirely on project cards and let the layout itself be the interaction.

**7. Role tags — kill the default bordered-box-with-arrow**

`.role-tag { border: 3px solid; padding: 1.2rem 1.8rem; }` with a `>` pseudo-element is generic.
- Keep the role text, but present it differently: as plain large text, or as part of the headline, or as a single line with a separator. If keeping boxes, change the shape (e.g., no padding, just a top border, or an extremely wide short box, or text with a background fill on hover only).

### Scope boundaries

- Do NOT change content (text, project names, blog posts)
- Do NOT change page structure or section order
- Do NOT remove the ticker, glitch, cursor, or scanlines (those are authored-feeling)
- Do NOT add new sections or pages
- Do NOT change the build system or framework

## Acceptance criteria

- [x] `Syne` and `Fragment Mono` are removed from the font stack and replaced with a non-default pairing
- [x] The exact `#070707` + `#ff2a2a` palette is replaced with a distinct color scheme (dark bg + non-red accent)
- [x] All section labels (About, Skills, Projects, Blog) no longer use `letter-spacing: 0.3em; text-transform: uppercase; font-size: 0.7rem; color: var(--accent)`
- [x] Footer no longer uses terminal-style `>` prompt syntax or `BUILD_SUCCESSFUL. EXIT CODE: 0`
- [x] Skill tags no longer use the bordered-pill component pattern
- [x] Project card hover no longer uses the left accent bar (`::before` width/height reveal)
- [x] Role tags no longer use the default bordered-box-with-arrow pattern
- [x] The site still builds and all sections render correctly
- [x] Mobile layout remains functional
- [x] The design, viewed as a whole, feels like a specific person's deliberate choices rather than a template

## Blocked by

None — can start immediately.
