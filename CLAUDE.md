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

## Key Conventions

- No frameworks or libraries — keep it vanilla HTML/CSS/JS.
- All styles and scripts are inline in `index.html`; do not split into separate files unless explicitly asked.
- Responsive design uses CSS Grid and Flexbox; breakpoints at 900px and 640px.
- Scroll animations use the Intersection Observer API with the `.fade-in` / `.visible` class pattern.
- Follow DRY principles — review existing CSS classes and JS before adding new ones.
