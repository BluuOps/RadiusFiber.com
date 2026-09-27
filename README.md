# radiusfiber.com

Public marketing website for RadiusFiber (separate from the OSS/BSS application).
Astro static site: zero client JS except the nav menu, contact form and scroll reveal.

```bash
npm install
npm run dev        # http://localhost:4321
npm run build      # static output in dist/
```

## Brand & design tokens
Tokens live in `src/styles/global.css` (`--rf-navy`, `--rf-blue`, `--rf-teal`, ...).
Brand colours are sampled from the RadiusFiber logo artwork; product colours
(teal, success, danger, borders, text) come from the RadiusFiber app theme.

## Assets
| Path | Source | Regenerate |
|---|---|---|
| `public/brand/*.svg`, favicons, app icons | `src/assets/brand-src/mark.svg` (hand-traced) + Montserrat 600 outlines | `npm run assets:brand` |
| `public/graphics/network-architecture*.svg`, `radius-aaa.svg` | hand-authored SVG | edit directly |
| `public/graphics/oss-bss-workflow.svg` | `scripts/build-graphics.mjs` | `npm run assets:graphics` |
| `public/product/dashboard-{desktop,mobile}.{png,webp}`, `public/social/radiusfiber-og.png` | `/render/product`, `/render/og` pages | build + preview, then `PORT=4321 npm run assets:rasters` |

Product visuals use **demonstration data** (`src/data/demo.ts`); never present it as real statistics.
Module copy (`src/data/modules.ts`) is limited to capabilities shipped in the app.

## Before launch
- Confirm `SITE.salesEmail` and `SITE.appUrl` in `src/site.ts`.
- Set `PUBLIC_DEMO_FORM_ENDPOINT` to receive demo requests (otherwise the form opens a pre-filled email).
- Have the brand owner approve the traced vector logo against the original artwork.
