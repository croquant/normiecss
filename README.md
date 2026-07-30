# Normie CSS

An extremely pure and simple **classless** CSS framework. Drop in one stylesheet and semantic HTML reads like a well-typeset printed document.

No classes. No build step. No webfonts. No JavaScript.

## Usage

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/croquant/normiecss@0.1.0/normie.min.css">
```

Or download `normie.css` from the [latest release](https://github.com/croquant/normiecss/releases/latest) and serve it yourself.

Write semantic HTML. That's the entire API. See the [demo page](https://croquant.github.io/normiecss/) for every supported element.

- `normie.css` — the framework. Hand-written and extensively commented; the source is the reference manual.
- `normie.min.css` — the minified build, generated in CI.
- `index.html` — the demo page: every supported element, zero classes. Open it locally; it doubles as documentation and a manual regression test.

## Design

See [DESIGN.md](DESIGN.md). The short version:

- **Paper metaphor as boundary** — if it can't appear on a printed sheet, it's out of scope.
- **Fixed, opinionated design** — no theming API. Fork and edit to customize.
- **Classless core** — zero modifiers; semantic HTML only.
- System serif stack, monospace code, one centered column at ~66ch, fluid type via `clamp()`, hard solid borders, WCAG AA contrast everywhere.

Dark mode is planned; it is not in V1.

## Versioning

Semver, starting at `0.1.0`. Promotion to `1.0.0` happens once the document-complete scope survives real-world use.

## License

MIT — see [LICENSE](LICENSE).
