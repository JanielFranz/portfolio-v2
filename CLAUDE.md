# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static single-page portfolio for Janiel Franz. The **entire application lives in one file: `index.html`** (~1001 lines). No build system, no package manager, no compilation step — open `index.html` directly in a browser to develop.

## Development

No build or install step. To preview locally:
- Open `index.html` in a browser, or
- Serve it with any static file server (e.g., `npx serve .` or VS Code Live Server)

## Tech Stack

All dependencies are loaded from CDN — no local installs:
- **Tailwind CSS** (CDN) — utility-first styling
- **Iconify Design** (CDN) — icon system
- **Google Fonts** — Inter typeface
- **Spline** — embedded 3D background in the hero section
- **Vanilla JavaScript** — all interactivity, no frameworks

## Architecture

Everything is co-located in `index.html`:

### Sections (by anchor ID)
- `#start` — Hero with Spline 3D background and CTA buttons
- `#about` — Timeline tabs switching between Work Experience and Education
- `#services` — Accordion cards (SaaS, AI, Automation)
- `#projects` — Project showcase cards
- `#testimonials` — Carousel with directional fade/slide animations

### JavaScript Subsystems
- **Multilingual (EN/ES):** Translation dictionary at the bottom of the `<script>` block. Language preference persists via `localStorage`; first visit auto-detects `navigator.language`.
- **Testimonial carousel:** Tracks current index and slide direction to apply CSS animation classes (`fade-in-right`, `fade-in-left`).
- **Accordion:** Toggles `max-height` and rotates chevron icon per service card.
- **Mobile nav:** Toggles overlay menu and locks `document.body.overflow`.
- **Timeline tabs:** Swaps visible content between Work and Education entries.

### Adding Translations
When adding or editing visible text, update both `en` and `es` keys in the translation object inside `<script>`. Elements that need translation must have a `data-i18n="keyName"` attribute; the `applyTranslations()` function sets their `textContent` automatically.

### Custom Animations
Testimonial transition animations are defined in a `<style>` block (not Tailwind) near the top of the file — look for `@keyframes` definitions for `fadeInRight`, `fadeInLeft`, etc.

### Way to Contact me
- linkedin: https://www.linkedin.com/in/janiel-franz-escalante-baygorrea-a00ab6290/
- mail: janielfranz@outlook.com