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
├── index.html        ← the entire site, one file (190KB)
├── vercel.json       ← clean URLs, security headers, cache strategy
├── .vercelignore     ← excludes rebuild source from deploys
├── .gitignore
├── README.md
└── src/              ← Tailwind rebuild source (local-only)
    ├── input.css
    └── tailwind.config.js
```

`index.html` is fully self-contained — Tailwind pre-compiled and inlined, all 47 product images as inline SVG placeholders, AR seal logo as inline SVG, favicon inline. Only external dependency is Google Fonts. No build step required.

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

### Product cards (47 placeholders)
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

## Rebuilding Tailwind (only if adding new utility classes)

The CSS in `index.html` is pre-compiled and tree-shaken. If you add a new Tailwind utility:

```bash
cd src
npx tailwindcss -i input.css -o output.css --minify
```

Then copy the contents of `output.css` into the `<style id="tw-compiled">…</style>` block in `index.html`.

If you only write custom CSS (in the second `<style>` block at the top of `index.html`), you can ignore the `src/` folder entirely.

---

## Tech notes

- **Zero JS dependencies** — ~30 lines of vanilla JS for the mobile menu drawer
- **Zero external image dependencies** — all 47 product placeholders + hero + logos are inline SVG
- **No build step required** for the deployed site
- **Mobile-first responsive** — horizontal scroll-snap galleries on phones, sticky drawer menu, 44×44 touch targets
- **A11y** — semantic HTML, ARIA labels, Escape-to-close menu

---

## License

© 2026 Aramea Jewelry. All rights reserved. Built by Thomas — WynwoodDreams.
