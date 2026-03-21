# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Wedding website for Julia & Franz (August 7, 2026) hosted on GitHub Pages at juliaundfranz.info. Static site with no build system, framework, or package manager.

## Architecture

- **Single-page static site**: `index.html` + `style.css`, no JavaScript framework
- **No build step**: Edit files directly, push to `main` to deploy via GitHub Pages
- **Bilingual (DE/EN)**: Client-side i18n using `data-i18n` / `data-i18n-html` attributes with a `translations` object in the inline `<script>` block. Language preference stored in `localStorage`.
- **All JS is inline**: Countdown timer, scroll animations (IntersectionObserver), nav toggle, FAQ accordion, and language switching all live in a single `<script>` at the bottom of `index.html`

## Key Patterns

- **Translations**: Text content uses `data-i18n="key"` for textContent and `data-i18n-html="key"` for innerHTML. Both `de` and `en` translation objects must be kept in sync when adding/changing text.
- **CSS design tokens**: Colors, fonts, and spacing are defined as CSS custom properties in `:root` in `style.css`
- **Scroll animations**: Elements with class `animate-on-scroll` fade in via IntersectionObserver
- **FAQ items**: Use `<details>` elements with a CSS grid-based smooth open/close animation

## Development

Open `index.html` in a browser. No server required (though a local server avoids CORS issues with fonts):

```
python3 -m http.server 8000
```

## Deployment

Push to `main` branch. GitHub Pages serves from root. Custom domain configured via `CNAME` file.
