# Tru Nobility Web V1

A responsive one-page Astro site for Tru Nobility, designed from the approved editorial homepage mockup. It is a lightweight static build that can later be deployed with Cloudflare Workers Static Assets. Layout and visual design stay in code; editable copy, links, and image references live in one small content file.

## Local development

Requires Node.js 22.12.0 or newer.

```bash
npm install
npm run dev
```

Open the local address shown in the terminal (normally `http://localhost:4321`).

Create a production build:

```bash
npm run build
npm run preview
```

The static production site is written to `dist/`.

## Editing content

All page copy, navigation, products, calls to action, social links, and image paths are in:

```text
src/content/site.json
```

This file is intentionally simple so Pages CMS can manage it later without exposing layout or design controls.

Known direct links are already included for Etsy, Instagram, TikTok, Facebook, the two Medium essays, and the currently featured classroom download. YouTube, Pinterest, Share My Lesson, support, contact, privacy, and terms are left as clearly labeled empty values in `site.json`; add verified URLs there when available.

The revised homepage structure follows the approved mockup: hero, old-site wayfinding, Freedom Studies feature, four-product Etsy strip, featured teaching resource, three-item written archive, platform vision, social follow band, support appeal, and full footer. Every section's copy, links, and image paths remain managed in `src/content/site.json`.

## Icons

The site uses Font Awesome Free SVG icons through the reusable `src/components/Icon.astro` component. Icons are rendered into the static HTML during the Astro build, so the finished page does not load Font Awesome JavaScript in the browser.

Social and follow-card icons can be changed in Pages CMS by selecting a platform key. Supported keys include Instagram, TikTok, YouTube, Facebook, Pinterest, X/Twitter, Threads, LinkedIn, Medium, Etsy, email, and website. To add another icon later, import it and add its key to the `icons` map in `Icon.astro`, then add the same key to the relevant select fields in `.pages.yml`.

## Replacing images

Temporary editorial assets and existing approved project images are in `public/images/`. The two files most clearly marked for later replacement are:

- `hero-temporary.jpg` — large right-side hero photograph
- `founders-temporary.png` — temporary image used in the support appeal
- `article-freedom-studies-collage.png` — temporary visual for the forthcoming Freedom Schools archive piece

The Sun Ra feature, four product cards, article imagery, and teaching-resource image are also controlled by paths in `src/content/site.json`. Replace a file while keeping the same filename, or add a new optimized WebP/AVIF/JPEG and update its path in the content file. The layout uses intentional crops, so review both desktop and mobile after changing imagery.

## File structure

```text
public/
  brand/          Canonical Tru Nobility identity assets
  fonts/          Approved Source Serif 4 and Archivo webfonts
  images/         Temporary and approved project imagery
src/
  components/     Reusable header, footer, social, and product components
  content/        The single editable site.json content source
  layouts/        Shared document shell and metadata
  pages/          Astro route(s)
  styles/         Responsive visual system and layout
astro.config.mjs  Static-output configuration
```

## Cloudflare Workers Static Assets

This project builds to plain static files and does not require a server runtime or an Astro adapter.

For a future Cloudflare Workers Static Assets setup:

1. Connect the repository in Cloudflare.
2. Set the build command to `npm run build`.
3. Set the asset/output directory to `dist`.
4. Use a current Node.js version supported by this project and Astro.
5. Add the custom domain only after the preview deployment is approved.

A minimal Wrangler configuration can later point its assets directory at `./dist`. No CMS, database, or Worker logic is required for V1. Keep the existing production site and DNS untouched until a Cloudflare preview deployment has been reviewed.

## Pages CMS later

Pages CMS can be added after the site is in GitHub. Configure its fields to edit `src/content/site.json` and upload media to `public/images/`. Keep components, CSS, section order, typography, and layout outside the CMS so the editor stays small and safe.
