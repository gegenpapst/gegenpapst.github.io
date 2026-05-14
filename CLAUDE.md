# CLAUDE.md

This file provides guidance to Claude Code when working in this repository.

## Project overview

Personal homepage for stuettgen.eu — a static, single-page start page with linked sub-pages. No build tools, no dependencies, no server required.

Open any `.html` file directly in a browser.

## Structure

```
homepage/
├── struktur.html   # Landing page — visual overview of stuettgen.eu/a categories
└── musik.html      # Music sub-page — embedded YouTube videos
```

## Design system

- **Background**: `#0d0d0d`
- **Text**: `#e0e0e0` / `#fff` for headings
- **Accent**: `#e0c86c` (gold) for music, links, hover states
- **Font**: `Courier New`, monospace throughout
- **Cards**: `#1a1a1a` background, `1px solid #2a2a2a` border, hover highlights border in accent color
- **Layout**: CSS Grid with `auto-fill / minmax` — no frameworks

## Conventions

- Pure vanilla HTML + CSS, no JavaScript unless needed
- All pages share the same dark theme and Courier New font
- Navigation: each sub-page links back to `struktur.html` in the header
- Video embeds use 16:9 aspect ratio via `padding-bottom: 56.25%` wrapper
- Category color coding in `struktur.html` uses CSS classes like `.cat-music`, `.cat-news` etc.

## Adding videos to musik.html

Copy an existing `.video-card` block and replace the artist, title, and YouTube embed ID (`youtube.com/embed/VIDEO_ID`).
