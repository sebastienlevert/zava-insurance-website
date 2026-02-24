# Copilot Instructions — Zava Insurance Website

## Build & Dev Commands

```bash
npm run dev       # Start dev server at localhost:4321
npm run build     # Build static site to ./dist
npm run preview   # Preview production build locally
```

There are no tests or linters configured. Validate changes by running `npm run build` to ensure the site compiles.

## Architecture

This is a static corporate website built with **Astro 5**. There are no client-side frameworks — pages are `.astro` components that render to static HTML.

- **`src/layouts/BaseLayout.astro`** — Single shared layout wrapping all pages. Provides the `<head>` (SEO meta, Open Graph, JSON-LD structured data), site header with nav, and footer. All pages pass `title` and optional `description`, `image`, `canonicalURL`, and `type` props.
- **`src/pages/`** — File-based routing. Each `.astro` file becomes a page. The `careers/[slug].astro` dynamic route generates individual job pages from the data layer.
- **`src/data/jobs.ts`** — Typed data store for job postings. Exports a `Record<string, Job>` keyed by URL slug. The `[slug].astro` page uses `getStaticPaths()` to generate a page per entry.
- **`src/styles/global.css`** — Single global stylesheet defining CSS custom properties (navy/teal/gold palette) and all component styles. No CSS modules or utility framework.

## Key Conventions

- **No JS frameworks**: All interactivity is vanilla `<script>` tags in Astro components. Do not add React, Vue, etc.
- **CSS custom properties**: Use the existing design tokens in `global.css` (e.g., `--color-navy`, `--color-teal`, `--color-gold`, `--radius-md`, `--shadow-lg`) rather than hardcoding values.
- **BEM-style class names**: CSS follows a loose BEM pattern (e.g., `.hero__content`, `.btn--primary`, `.icon-card__icon`).
- **SEO on every page**: All pages must use `BaseLayout` and provide a descriptive `title` prop. The layout handles meta tags, canonical URLs, and structured data automatically.
- **Data-driven dynamic pages**: To add a new career posting, add an entry to the `jobs` object in `src/data/jobs.ts` — no new page file is needed.
- **Static images**: Brand assets (logos, favicons) live in `public/images/`. Content images currently use external Unsplash URLs.

## Deployment

Auto-deploys to GitHub Pages on push to `main` via `.github/workflows/deploy.yml`. The site URL is configured as `https://zava-insurance.com` in `astro.config.mjs`.
