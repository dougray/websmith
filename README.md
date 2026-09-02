# Websmith

Site for **Websmith** — serving small business and non-profits with digital presence and defense.

**Live site:** https://dougray.github.io/websmith/

## Structure

Single self-contained `index.html`. All CSS is inline in `<head>`. No build step,
no JavaScript, no dependencies. The only external request is Google Fonts
(Jost and JetBrains Mono).

```
index.html      the whole site
.nojekyll       tells GitHub Pages to serve the files as-is
assets/
  websmith-logo.webp   hero logo (900px)
  websmith-logo.jpg    same, fallback format
  og-card.jpg          1200x630 social preview
  apple-touch-icon.png 180x180
  favicon.png          32x32
```

## Editing

Open `index.html` and edit the text directly. Commit to `main` and GitHub Pages
redeploys within a minute or two.

The contact address (`dugcanlift@gmail.com`) appears in five places — both
call-to-action buttons, the plain-text link under the contact button, the footer,
and the JSON-LD block near the top of the file. Update all of them together.

The absolute URLs in the `og:` meta tags and the JSON-LD assume
`dougray.github.io/websmith/`. If a custom domain is added later, add a `CNAME`
file and update those URLs.

## Regenerating image assets

From the source render kept at the repo root (`websmith-logo-source.png`, 1254×1254):

```bash
magick websmith-logo-source.png -resize 900x900 -strip -quality 84 assets/websmith-logo.webp
magick websmith-logo-source.png -resize 900x900 -strip -quality 82 assets/websmith-logo.jpg
magick websmith-logo-source.png -resize 1100x1100 -background black -gravity center \
  -extent 1200x630 -strip -quality 82 assets/og-card.jpg
magick websmith-logo-source.png -crop 1020x720+180+180 +repage -background black \
  -gravity center -extent 1020x1020 -resize 180x180 -strip assets/apple-touch-icon.png
magick assets/apple-touch-icon.png -resize 32x32 -strip assets/favicon.png
```

## Licence

MIT — see `LICENSE`.
