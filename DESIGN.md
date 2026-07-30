# Normie CSS - Design

An extremely pure and simple classless CSS framework that makes semantic HTML look like a well-typeset printed document.

## Core principles

- **Classless**: drop in one stylesheet, semantic HTML looks right. Zero markup changes.
- **Paper metaphor as boundary**: if it can't appear on a sheet of paper, it's out of scope. This excludes overlays, modals, tooltips, sticky/fixed positioning, parallax, and animations by default.
- **Fixed opinionated design**: no theming API, no customization surface. Fork and edit if you want different values.
- **Readable source**: the CSS source is extensively commented and serves as the primary reference. Every line must be justifiable.
- **Minimal by default**: no published size budget, but every addition must earn its bytes.

## Aesthetic

Typographic homage to print, not skeuomorphism.

- No shadows, no gradients, no textures, no fake page.
- Flat colors, high contrast, hard solid borders (1-2px).
- Serif body and headings (same family, as in print), monospace code.
- Single centered column, `max-width` in `ch` (~66 characters measure).
- Fluid type via `clamp()`, scales smoothly with viewport. No breakpoint jumps.
- Responsive and readable on any device.
- Keyboard focus: hard solid outline, accent color, `:focus-visible`.
- Target WCAG AA contrast ratios on every text/background pair.
- Respects `prefers-reduced-motion` (no animations to disable).

## V1 scope: document-complete

Styled out of the box (unclassed, semantic HTML only):

- Typography: `h1`-`h6`, `p`, `a`, lists, `blockquote`, `hr`, `abbr`, `small`, `mark`, `sup`/`sub`
- Code: `code`, `kbd`, `pre`, `samp`
- Tables, figures with captions, images/media constrained to column
- Forms: inputs, selects, textarea, buttons, fieldset/legend, labels; validation states (`:invalid`, `:user-invalid`, `:required`)
- `details`/`summary`

Out of scope for V1: `<dialog>`, nav components, cards, modals, grids, alerts, any UI-kit patterns.

## Technical decisions

| Decision | Resolution |
|---|---|
| Classes | Classless core. **Zero modifiers ship in V1**. A modifier is added only when a document-idiomatic need can't be met semantically. |
| Build | None locally. Single hand-written `normie.css`. `normie.min.css` produced in CI (e.g., GitHub Actions via a minifier). Not a dev dependency. |
| Fonts | System serif stack, system monospace. No webfont, no `@font-face`. |
| Customization | No official theming API. `ink` / `paper` / `accent` are defined as CSS variables scoped within the framework to prevent casual override; they exist purely so a future dark mode can swap values without rewriting selectors. |
| Dark mode | Not in V1. Planned. `color-scheme: light` set explicitly — will need to change to `light dark` or equivalent when dark mode ships. |
| Reset | Minimal hand-written targeted reset (~15-25 lines): `box-sizing`, body margin, media constraints, form controls inherit font, margin normalization on styled elements only. No normalize library. |
| Print | Prints well out of the box by design. Small `@media print` block only where strictly necessary (`break-inside: avoid` on figures, tables, blockquotes, `pre`). |
| Browser support | Modern evergreen only. Any modern CSS allowed (nesting, `:where()`, `:is()`, logical properties). No prefixes, no fallbacks, no legacy. |
| Demo page | `index.html` exercising every in-scope element, unclassed. Serves as documentation, manual regression test, and marketing. Very important. |

## Repo contents

- `normie.css` - the framework, hand-written
- `normie.min.css` - minified (CI)
- `index.html` - demo page
- `README.md`
- `DESIGN.md` - this file
- `LICENSE` - MIT

## Versioning

Semver, starting at `0.1.0`. Promote to `1.0.0` once the document-complete scope survives real-world use.

## Roadmap (post-V1, not committed)

- Dark mode (additive via internal color variables)
- Full UI kit (nav, cards, modals, grid) as an optional layer, never compromising the classless core
- Modifier classes, added one at a time against proven needs
