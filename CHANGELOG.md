# Changelog

All notable changes to this theme are documented here. The format follows
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and the theme follows
[Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.0.0] — 2026-09-23

### Added

- A ten-minute sample note with a figure in it, so the shelf shows a long piece and an
  illustrated one as well as the short notes. The figure is an inlined SVG drawn in the
  theme's own tokens, which is how a chart follows the palette into dark mode.
- Products and notes can be filed in folders. `notes/2026/04/one-tab.md` is
  `/notes/2026/04/one-tab`, which is what a site moving from dated addresses needs.
- Task lists are set with the square marker dropped and the checkbox in ink rather than
  the browser's blue, which would read as a fifth category colour.

### Fixed

- A product or note in a subfolder failed the build with `Missing parameter: slug`. Both
  routes are now rest parameters.
- A GFM task list wrote a checkbox with no label of its own, which an accessibility audit
  fails and which left the words beside the box outside the control. Each item's contents
  are now wrapped in a `<label>`.
- A paginated `/notes` carried no `rel="prev"` or `rel="next"`, so the pages read as
  unrelated documents with almost the same title.

### Changed

- The colour tokens are lifted out of the stylesheets in one place, `src/lib/palette.js`,
  rather than by a regular expression inside the contrast gate.
- The CI workflow runs the gates on every push and pull request and nothing else. The
  weekly Lighthouse schedule and the path filter it used to carry were ours, not yours.
- `CLAUDE.md`, which is a symlink to `AGENTS.md`, is no longer written into the release
  snapshot. An unzip that ignores the symlink bit left a broken file where the guide is.

## [0.9.0] — 2026-09-23

First snapshot of the free edition. The live demo and the screenshots follow in 1.0.0.

### Added

- The leader rule: one ruled row per item, the product or note on the left, its category
  on the right in that category's colour, a hairline joining them that thickens into the
  accent on hover. Every list on the site is that one row. Switch it off with
  `work.leaderRule: 'none'`.
- Categories as the one axis: four of them in `src/config.ts`, one accent each, carried
  from the index row to the product page to every note filed underneath.
- Pages: home, work shelf, product, notes with pagination, note, category, about,
  contact, privacy, terms, 404.
- Content collections for work and notes, typed with zod in `src/content.config.ts`, with
  eight sample products and twelve sample notes.
- Light and dark mode through `light-dark()` tokens and a three-state switcher (system,
  light, dark). Every token pair is checked against WCAG AA by `pnpm check:contrast`.
- RSS feed, sitemap, robots.txt, canonical URLs, Open Graph, Twitter cards and JSON-LD.
- Analytics slot (Plausible, GA4, Umami) and a contact form that posts to any static form
  service. Neither loads anything until it is configured.
- `AGENTS.md` for Claude Code, Cursor and other agents, with `CLAUDE.md` pointing at it.
