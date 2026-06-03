# Aramea Jewelry

Editorial e-commerce storefront for **ARAMEA — Jewelry & Accessories**. Single-file static site, designed in Miami, deployed on Vercel.

> *925 Silver · 18K Gold Laminated · Heirloom-quality pieces for forever moments.*

---

## Live

- **Production:** _(deploy URL will go here)_
- **Repo:** [github.com/WynwoodDreams/aramea-jewelry](https://github.com/WynwoodDreams/aramea-jewelry)

---

## Structure

```
.
├── index.html        ← the entire site, one file
├── vercel.json       ← clean URLs, security headers, cache strategy
├── .gitignore
└── README.md
```

`index.html` is fully self-contained — all styles, scripts, SVG product
placeholders, AR seal logo and favicon are inline. External dependencies:
Google Fonts (CDN), plus hotlinked Unsplash photos and a Cloudinary logo/video
that fade in over the SVG fallbacks. No build step required.

### What's on the page
- Sticky header with primary nav, **search overlay**, account & bag links
- Auto-playing **hero carousel** (3 slides, video + SVG fallback)
- **Trust band** — free shipping, returns, lifetime warranty, certification
- New Arrivals strip + **Featured Collection** product grid
- Heritage / atelier split with New Arrivals duo
- **"Crafted for Forever"** value-prop section + customer **reviews**
- Instagram grid, newsletter footer

### Interactive features (vanilla JS, no dependencies)
- **Product quick-view** modal (click any product image)
- **Local cart** with localStorage persistence + slide-out drawer — works
  standalone, and steps aside automatically once Shopify is configured
- **Wishlist** favourites, persisted to localStorage
- **Search** overlay that filters products live
- SEO: Open Graph / Twitter cards, JSON-LD `JewelryStore` structured data,
  canonical URL

---

## Deploy

Connected to Vercel via the GitHub integration — any push to `main` triggers a production deploy automatically. Preview deploys spin up for any branch.

To deploy manually:
```bash
npx vercel --prod
```

---

## Swapping in real assets

### Hero image (right panel)
Currently shows an editorial tearsheet SVG placeholder. To swap in a real photo:
1. Drop a JPG/WebP at repo root: `hero.jpg`
2. In `index.html`, search for `alt="Aramea — editorial tearsheet"`
3. Replace the long `src="data:image/svg+xml;utf8,…"` with `src="/hero.jpg"`

### Product cards
Each card is labeled with its piece name. To swap one:
1. Search the HTML for the piece name (e.g. `Verde Eternal`, `Iris Multi-Stone`)
2. Replace the surrounding `src="data:image/svg+xml;utf8,…"` with your image path

### Logo / favicon
The AR seal appears in 3 sizes (header, hero bridge, footer) plus the favicon. All inline SVG. Search for `viewBox="0 0 60 60"` and `viewBox="0 0 100 100"`.

---

## Brand spec

| Token | Value |
|-------|-------|
| Ink | `#0a0908` |
| Ivory | `#f5f1e8` |
| Cream | `#ede6d6` |
| Sand | `#e0d6bf` |
| Gold | `#c9a96e` |
| Gold light / dark | `#d4b97e` / `#9d8654` |
| Silver | `#c4c4cc` |
| Silver light / dark | `#dcdce0` / `#8a8a92` |
| Charcoal | `#1a1715` |

**Fonts** (Google Fonts CDN): Italiana (display), Bodoni Moda (pull-quotes), Cormorant Garamond (italic accents), Jost (UI sans).

**Logo**: gold `A` + silver `R` + gold 4-point sparkle on a black disc.

---

## Styling

All CSS lives in a single hand-written `<style>` block at the top of
`index.html` using CSS custom properties (see Brand spec). There is no build
step and no framework — edit the styles directly.

---

## Tech notes

- **Zero JS dependencies** — vanilla JS for the drawer, hero carousel, quick-view, local cart, wishlist and search
- **Inline SVG placeholders** for every product, with real photos fading in on top (and removed gracefully on error)
- **No build step required** for the deployed site
- **Mobile-first responsive** — sticky drawer menu, 44×44 touch targets
- **A11y** — semantic HTML, ARIA labels, `:focus-visible` styling, Escape-to-close on every overlay
- **SEO** — Open Graph/Twitter meta, JSON-LD structured data, canonical URL

---

## License

© 2026 Aramea Jewelry. All rights reserved. Built by Thomas — WynwoodDreams.
