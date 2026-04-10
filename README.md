# dev-utils

Small developer utilities — hosted on GitHub Pages, no dependencies, no build step.

**[rscRoman.github.io/dev-utils](https://rscRoman.github.io/dev-utils)**

## Tools

| Tool | Description |
|---|---|
| **Base64** | Encode & decode — auto-detects direction on paste |
| **Base64 → Image** | Paste a Base64 string and preview the image |
| **Image → Base64** | Drop or select an image file, get raw Base64 and data URI |
| **ASCII / Codepoints** | Inspect a string character by character — decimal, hex, Unicode |
| **Decimal → Hex** | Convert a decimal number to uppercase hex with byte-pair formatting |
| **Timestamp** | Live Unix clock, convert timestamp → date or date → timestamp |
| **JSON Formatter** | Pretty-print or minify JSON with syntax highlighting |
| **File Size** | Convert between bit, byte, KB/KiB, MB/MiB, GB/GiB… — decimal and binary |

## Stack

Pure HTML/CSS/vanilla JS. Fonts via Google Fonts (Syne + JetBrains Mono). Everything runs in the browser — no server, no framework, no package manager.

## Adding a tool

1. Copy any page in `utils/` as a starting point
2. Add a card to the grid in `index.html`
3. Push to `main` — GitHub Pages picks it up automatically
