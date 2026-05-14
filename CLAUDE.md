# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

Personal homepage for stuettgen.eu — a static start page with linked sub-pages. No build step, no server required. Open any `.html` file directly in a browser.

**Public URL:** https://gegenpapst.github.io

## Pages

- **[index.html](index.html)** — Landing page with filterable category cards linking to external sites
- **[musik.html](musik.html)** — Music sub-page with filterable/searchable YouTube video grid

## Tech stack

Both pages load from CDN — no local dependencies:

- **Tailwind CSS** (`cdn.tailwindcss.com`) — utility classes for layout and spacing
- **Alpine.js** (`alpinejs@3.x.x`) — reactive data and filtering, via `x-data` on the root `<div>`
- **`Courier New` monospace** — applied via `<style>` tag (not Tailwind), sitewide

## Design system

| Token | Value |
|---|---|
| Background | `#0d0d0d` |
| Text | `#e0e0e0` |
| Accent (gold) | `#e0c86c` — used in musik.html and hover states |
| Card background | `#1a1a1a` |
| Card border (default) | `#2a2a2a` |

Category colors in index.html are per-category inline values (`cat.color`, `cat.border`) — not CSS classes. Hover effects swap border color via Alpine `@mouseenter`/`@mouseleave`.

## Data structures

### index.html — category object

```js
{ id: 'tech', icon: '💻', label: 'Technologie', color: '#6cb8e0', border: '#20303a',
  items: [
    { label: 'Heise', href: 'https://www.heise.de' },
  ],
  links: [                          // optional: internal page links shown below items
    { href: 'musik.html', label: '▶ Videos' },
  ]
}
```

Categories with the same `id` are grouped under the same filter button. Multiple categories can share an `id` (e.g. three separate news cards all use `id: 'news'`).

### musik.html — video object

```js
{ artist: 'Interpol', title: 'Obstacle 1', id: 'DG--dQMdiQI',
  tab: 'https://drive.google.com/...' }  // optional: overrides default Ultimate Guitar search link
```

Videos sort by descending artist video count, then alphabetically by artist.

## Adding content

**New category card** (index.html): Add a new object to the `categories` array. Reuse an existing `id` to merge into an existing filter, or introduce a new one for a new filter button.

**New video** (musik.html): Add an object to the `videos` array with `artist`, `title`, and the YouTube video ID (`id`). Optionally add `tab` with a direct tab/chord URL.

## Navigation

Sub-pages link back to `index.html` (not `struktur.html`). The back link appears as `← zurück` in a top nav bar, using gold on hover (`text-[#e0c86c]`).
