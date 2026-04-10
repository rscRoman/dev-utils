# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

`dev-utils` is a static developer-utility web app hosted on GitHub Pages at `https://rscRoman.github.io/dev-utils`.  
Pure HTML/CSS/vanilla JS — no frameworks, no build tools, no package manager.

## Structure

```
index.html              overview page with utility cards
css/style.css           shared design system (tokens, layout, components)
js/theme.js             dark/light theme logic (localStorage + prefers-color-scheme)
utils/
  base64.html           Base64 encode & decode
  base64-image.html     Base64 string → image preview
  image-base64.html     Image file (drop/browse) → raw Base64 + data URI
  ascii.html            String → per-character ASCII/codepoint table (dec, hex, Unicode)
  decimal-hex.html      Decimal → uppercase hex; takes last 10 digits of input
  timestamp.html        Unix timestamp ↔ date; live clock, auto-detects seconds vs ms
  json.html             JSON pretty-print / minify with syntax highlighting; indent toggle (tab/2/4)
  filesize.html         Bit/Byte/KB…PB converter; shows decimal (×1000) and binary (×1024) side by side
favicon.svg             >_ icon in accent color — referenced by all pages
```

## Design system

CSS custom properties live in `:root` (dark, default) and `[data-theme="light"]`. All components use these tokens — never hardcode colors.

| Token | Role |
|---|---|
| `--bg`, `--surface`, `--surface-2` | Background layers |
| `--border` | All borders and dividers |
| `--text`, `--muted` | Text hierarchy |
| `--accent` / `--accent-fg` | Primary accent (`#e8ff47` dark, `#1a1a1c` light) and its foreground |
| `--ui` | Syne (headings, UI labels, buttons) |
| `--mono` | JetBrains Mono (code values, input/output, site name) |

## Theme

`js/theme.js` runs synchronously in `<head>` to prevent theme flash. It reads `localStorage` key `dev-utils-theme`; on first visit it falls back to `prefers-color-scheme`. All pages load it the same way — no modules, no defer.

## Adding a new utility

1. Create `utils/<name>.html` — copy an existing util page as a template.
2. The header breadcrumb pattern: `site-name / page-label` (see `.hd-left` in any util page).
3. Asset paths from `utils/` are `../favicon.svg`, `../css/style.css` and `../js/theme.js`.
4. Add a card to the grid in `index.html`.
5. Add a footer: `<footer>// <a href="https://github.com/rscRoman" ...>Roman</a></footer>`.

## Conventions

- Indentation: tabs, displayed at width 4.
- Auto-convert on paste (`inputEl.addEventListener('paste', () => setTimeout(fn, 0))`) — all util pages do this.
- Copy buttons copy raw values (no formatting/separators), display values may be formatted for readability.

## Deployment

Push to `main` — GitHub Pages serves the repo root directly. No build step.
