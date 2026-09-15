# Zava Insurance — Corporate Website

A modern, SEO-friendly corporate website for Zava Insurance, built with [Astro](https://astro.build) and deployed via GitHub Actions to GitHub Pages.

## Pages

- **Home** — Hero, stats, services overview, testimonials, community highlight
- **About** — Company story, mission, vision, core values, community impact, leadership team
- **Services** — Auto, home, life, business, health, and umbrella insurance details
- **Products** — Product lineup with features and pricing (AutoShield, HomeGuard, LifeSecure, BusinessPro, HealthPlus, UltraShield)
- **Branches** — 12 branch locations across the Northeast with contact details
- **Life at Zava** — Culture, values, employee testimonials, perks & benefits, ERGs
- **Careers** — 12 open job postings with full detail pages
- **Contact** — Contact form and company contact information
- **Privacy Policy** (`/privacy`) — Website information handling, hosting and external content, privacy choices, and contact options
- **Terms of Use** (`/terms`) — Website usage conditions, insurance disclaimers, intellectual property, and liability

Both legal pages are linked from the shared footer on every page. Internal links use
the configured `BASE_PATH`, so the default GitHub Pages URLs are
`/zava-insurance-website/privacy` and `/zava-insurance-website/terms`. With
`BASE_PATH=/`, the routes are `/privacy` and `/terms`.

### Legal content

The privacy and terms pages contain original template text tailored to the current
static website, last updated September 15, 2026. They are not legal advice or a
representation that the website complies with every applicable law. Have the
website owner and qualified counsel review them before relying on them for a
production insurance business. Confirm the operator identity, contact details,
jurisdictions, data practices, and any separate insurance privacy notices.

The privacy text reflects GitHub Pages hosting, externally loaded Unsplash images,
email links, and the absence of first-party analytics or a form-processing backend.
The existing contact form is not connected to a submission service; posting it may
still send entered data to the host. Revisit both pages before enabling form
processing, analytics, cookies, accounts, payments, or other data collection.
Provider references are linked in the Privacy Policy.

## Tech Stack

- **Astro** — Static site generator with markdown support
- **TypeScript** — Type-safe data and configuration
- **CSS** — Custom corporate theme (navy/teal palette, no framework dependency)
- **@astrojs/sitemap** — Auto-generated XML sitemap for SEO

## SEO Features

- Semantic HTML with proper heading hierarchy
- Open Graph and Twitter Card meta tags on every page
- JSON-LD structured data (InsuranceAgency schema)
- Auto-generated `sitemap-index.xml` and `robots.txt`
- Canonical URLs on all pages

## Getting Started

```bash
npm install
npm run dev      # Start dev server at localhost:4321
npm run build    # Build static site to ./dist
npm run preview  # Preview built site locally
```

## Deployment

This site auto-deploys to GitHub Pages on push to `main` via the workflow in `.github/workflows/deploy.yml`.

To set up:
1. Push this repo to GitHub
2. Go to **Settings → Pages → Source** and select **GitHub Actions**
3. Push to `main` — the site will build and deploy automatically

## Project Structure

```
├── .github/workflows/deploy.yml  # GitHub Actions CI/CD
├── public/                        # Static assets (robots.txt, favicon)
├── src/
│   ├── data/jobs.ts              # Job postings data
│   ├── layouts/BaseLayout.astro  # Base HTML layout with SEO
│   ├── pages/                    # All page routes
│   │   ├── index.astro           # Homepage
│   │   ├── about.astro
│   │   ├── services.astro
│   │   ├── products.astro
│   │   ├── branches.astro
│   │   ├── contact.astro
│   │   ├── privacy.astro
│   │   ├── terms.astro
│   │   ├── life-at-zava.astro
│   │   └── careers/
│   │       ├── index.astro       # Careers listing
│   │       └── [slug].astro      # Individual job pages
│   └── styles/global.css         # Corporate theme styles
├── astro.config.mjs
├── package.json
└── tsconfig.json
```
