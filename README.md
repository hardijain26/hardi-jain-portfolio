# SEO build

Each page ships as its own static HTML file with its own title, description,
canonical, structured data and readable text. The app still runs as before.

- `seo/pages.json`: titles, descriptions and schema type per page. Edit here.
- `seo/content/`: story text captured from the rendered app (generated).
- `scripts/extract-content.mjs`: re-captures that text. Run after editing a story.
- `scripts/build-seo.mjs`: writes `index.html` head, `<path>.html` files and `sitemap.xml`.

After any change to a story or to `pages.json`:

    npm i -D playwright && npx playwright install chromium   # once
    node scripts/extract-content.mjs
    node scripts/build-seo.mjs

Journey chapters (`/journey/*`) are noindex and left out of the sitemap.
