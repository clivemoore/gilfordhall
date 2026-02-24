# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static single-page website for **Gilford Community Hall** (Ontario, Canada — "Neighbours Gathering Since 1873"). The entire site lives in one file: `index.html` (HTML + embedded CSS + embedded vanilla JavaScript). There are no dependencies, no build system, no package manager, and no tests.

## Running Locally

Serve `index.html` with any static HTTP server:
```
python3 -m http.server 8000
# or
npx serve .
```

## Architecture

Everything is in `index.html` (~1140 lines):
- **Lines 11–550**: `<style>` block — CSS custom properties, layout, responsive breakpoints (900px, 640px)
- **Lines 550–1090**: HTML markup — nav, hero, content sections, footer
- **Lines 1090–1140**: `<script>` block — Intersection Observer animations, smooth scroll, mobile menu toggle, newsletter form handler

## Design System

CSS custom properties defined on `:root`:
| Token | Value | Usage |
|---|---|---|
| `--barn-red` | `#8B2500` | Primary / brand |
| `--barn-red-dark` | `#6B1D00` | Hover states |
| `--cream` | `#FDF5E6` | Page background |
| `--charcoal` | `#333333` | Body text |
| `--gold` | `#DAA520` | Accent / highlights |
| `--forest-green` | `#2F4F4F` | Secondary backgrounds |

Fonts (Google Fonts): **Bitter** (headings, serif), **Source Sans 3** (body, sans-serif).

## Images

The `images/` directory holds all site images. The HTML references these files:
- `images/hero.jpg` — hero background (via CSS `background-image` on `.hero-bg`)
- `images/hall-main.jpg` — main hall photo (space grid)
- `images/kitchen.jpg` — kitchen (space grid)
- `images/stage.jpg` — stage (space grid)
- `images/exterior.jpg` — hall exterior (space grid)
- `images/yard.jpg` — outdoor yard/park (space grid)

Images are not yet committed — drop the actual files into `images/` when ready.

## Deployment (Netlify)

- Config lives in `netlify.toml` (publish dir `.`, www→apex redirect, security headers, image caching).
- The newsletter form uses **Netlify Forms** (`data-netlify="true"`, hidden `form-name` field). No JS handler needed — Netlify processes submissions automatically.
- Custom domain: `gilfordhall.ca` (configure DNS in Netlify dashboard).

## Key Conventions

- No frameworks or libraries — keep it vanilla HTML/CSS/JS.
- All styles and scripts are inline in `index.html`; do not split into separate files unless explicitly asked.
- Responsive design uses CSS Grid and Flexbox; breakpoints at 900px and 640px.
- Scroll animations use the Intersection Observer API with the `.fade-in` / `.visible` class pattern.
- Follow DRY principles — review existing CSS classes and JS before adding new ones.
