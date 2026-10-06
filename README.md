# tikaPOS website

Static marketing site for tikaPOS (point of sale with menu/item, POS screen, tender,
cash session, stock/inventory, PO and invoices, and built-in accounting).
Same setup as `approvalpro/`: plain HTML with inline CSS, no build step.

## Structure

```
index.html          Home page, Bahasa Indonesia (default language, served at /)
404.html            Not-found page (noindex)
sitemap.xml         Sitemap with hreflang alternates
robots.txt
favicon.ico
assets/             logo.png, og-image.png (1200x630), icon-512.png, apple-touch-icon.png
```

## SEO checklist for new pages

- `<html lang="id">`, unique `<title>` and meta description
- `<link rel="canonical">` with the absolute URL
- `hreflang` alternates (`id`, `x-default`, and `en` once it exists)
- Open Graph + Twitter tags, `og:locale` = `id_ID`
- JSON-LD where relevant; keep the FAQPage JSON-LD in sync with the visible FAQ
- Add the page to `sitemap.xml` and bump `<lastmod>`

## Adding English (planned)

Bahasa Indonesia stays at `/`. English goes under `/en/`:

1. Create `en/index.html` (translated copy) with `lang="en"`, `og:locale` = `en_US`,
   canonical `https://tikapos.id/en/`, and asset paths prefixed with `../` (or `/`).
2. In **both** pages, add the full set of alternates:
   ```html
   <link rel="alternate" hreflang="id" href="https://tikapos.id/">
   <link rel="alternate" hreflang="en" href="https://tikapos.id/en/">
   <link rel="alternate" hreflang="x-default" href="https://tikapos.id/">
   ```
3. Turn the disabled `EN` in the navbar `.lang-switch` into a link to `/en/`
   (and on the English page, make `ID` link back to `/`).
4. In `sitemap.xml`, add the `en` alternate to the existing entry and a new `<url>`
   entry for `/en/` with the same three alternates.

## TODO before launch

- Confirm the domain (`tikapos.id` is used throughout: canonical, OG, sitemap, robots).
- Add the GA4 tag in `<head>` (placeholder comment in `index.html`).
- Confirm contact email and sign-in/sign-up URLs.
