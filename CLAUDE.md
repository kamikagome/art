# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This repo contains a single-file HTML landing page for **Alma Retreat** — an art and yoga retreat in Andalucía, Spain. There is no build system or package manager; the file runs directly in a browser.

## Architecture

[Alma Retreat - Organic Flow.html](Alma%20Retreat%20-%20Organic%20Flow.html) is a fully self-contained React 18 app:

- React 18 + ReactDOM loaded via CDN (unpkg)
- JSX transpiled in-browser by `@babel/standalone`
- No external CSS framework — all styles are inline or in a `<style>` block in `<head>`
- Fonts: `Cormorant Garamond` and `DM Serif Display` from Google Fonts

### Key patterns

- **`TWEAK_DEFAULTS`** (marked `/*EDITMODE-BEGIN*/…/*EDITMODE-END*/`) — a JSON object of user-configurable values. An external parent frame can activate a "tweaks panel" by posting `{ type: '__activate_edit_mode' }` via `postMessage`, letting the user change accent color, blob color, card radius, and retreat date without touching code.
- **`Img` component** — placeholder image blocks rendered as CSS diagonal-stripe patterns with a centered label. Replace with `<img>` tags when real photography is available.
- **`col` object** — single source of truth for the color palette, derived from `tweaks` state. Always update colors through here.

## Development

Open the HTML file directly in a browser — no server required:

```
open "Alma Retreat - Organic Flow.html"
```

For live-reload during editing, any static file server works:

```
npx serve .
# or
python3 -m http.server
```
