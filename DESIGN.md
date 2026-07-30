# Normie CSS - Design

An extremely pure and simple classless CSS framework that makes semantic HTML look like a well-typeset printed document.

## Core principles

- **Classless**: drop in one stylesheet, semantic HTML looks right. Zero markup changes.
- **Paper metaphor as boundary**: if it can't appear on a sheet of paper, it's out of scope.
- **Fixed opinionated design**: no theming API, no customization surface. Fork and edit if you want different values.
- **Readable source**: the single file is the documentation. Every line must be justifiable.
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

## V1 scope: document-complete

Styled out of the box (unclassed, semantic HTML only):

- Typography: `h1`-`h6`, `p`, `a`, lists, `blockquote`, `hr`, `abbr`, `small`, `mark`, `sup`/`sub`
- Code: `code`, `kbd`, `pre`, `samp`
- Tables, figures with captions, images/media constrained to column
- Forms: inputs, selects, textarea, buttons, fieldset/legend, labels
- `details`/`summary`

Out of scope for V1: nav components, cards, modals, grids, alerts, any UI-kit patterns.

## Technical decisions

| Decision | Resolution |
|---|---|
| Classes | Classless core. Modifier-class naming convention documented, but **zero modifiers ship in V1**. A modifier is added only when a document-idiomatic need can't be met semantically. |
| Build | None. Single hand-written `normie.css`. `normie.min.css` produced in CI, not a dev dependency. |
| Fonts | System serif stack, system monospace. No webfont, no `@font-face`. |
| Customization | None public. Internal variables only for `ink` / `paper` / `accent` colors so a future dark mode is purely additive. |
| Dark mode | Not in V1. Planned. `color-scheme: light` set explicitly. |
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
- `package.json` - published as `normiecss` on npm

## Versioning

Semver, starting at `0.1.0`. Promote to `1.0.0` once the document-complete scope survives real-world use.

## Roadmap (post-V1, not committed)

- Dark mode (additive via internal color variables)
- Full UI kit (nav, cards, modals, grid) as an optional layer, never compromising the classless core
- Modifier classes, added one at a time against proven needs
