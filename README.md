# Bazarstore LLC

Hugo placeholder website for **Bazarstore LLC** and the `bazarstore.biz` business division.

The site positions Bazarstore LLC as a full-cycle market-entry, import, logistics, distribution, compliance, retail access, public procurement, and brand-development partner for international suppliers entering the Azerbaijani market.

## Stack

- Hugo `0.162.0`
- Go `1.26.3` for Hugo Modules
- Node.js `26.0.0`
- `mise` for pinned local tooling
- PaperMod installed as a Hugo Module
- Tailwind CSS `4.3` compiled with PostCSS
- Netlify-ready static deployment
- YAML-based site configuration in `hugo.yaml`
- Markdown/YAML page content in `content/_index.md`
- Custom homepage layout in `layouts/index.html`
- Static favicon, logo, hero assets, and `robots.txt` in `static/`

## Quick Start

Install the pinned tool versions:

```sh
mise install
```

Run the local Hugo server:

```sh
mise exec -- npm ci
mise exec -- npm run dev
```

Open the local site:

```text
http://localhost:1313/
```

Build the production site:

```sh
mise exec -- npm run build
```

Build with a clean Hugo destination:

```sh
mise exec -- npm run build:clean
```

The generated site is written to `public/`.

## Netlify

Netlify configuration is stored in `netlify.toml`.

Production build:

```toml
[build]
  command = 'npm ci && npm run build'
  publish = "public"
```

Production environment:

```toml
HUGO_VERSION = "0.162.0"
HUGO_ENV = "production"
HUGO_ENABLEGITINFO = "true"
GO_VERSION = "1.26.3"
NODE_VERSION = "26.0.0"
```

Local Netlify development keeps `HUGO_ENV = "development"` through the `context.dev.environment` block.

## Project Structure

```text
archetypes/             Hugo content archetypes
assets/source/          Non-published source/design files
assets/tailwind/input.css Tailwind 4.3 and custom source CSS
content/_index.md       Main page content and YAML data
layouts/baseof.html     Local PaperMod base override for current Hugo APIs
layouts/index.html      Custom homepage layout
layouts/partials/       PaperMod extension partials
static/                 Static assets copied directly to the published site
go.mod                  Hugo Module definition and PaperMod dependency
go.sum                  Hugo Module checksum file
hugo.yaml               Hugo site configuration
mise.toml               Pinned Hugo, Go, and Node versions
netlify.toml            Netlify build and dev configuration
package.json            Tailwind/PostCSS build scripts
postcss.config.mjs      PostCSS configuration for Tailwind 4.3
scripts/hugo.sh         Hugo runner using mise locally and Netlify's Hugo in deployment
```

## Theme

PaperMod is connected as a Hugo Module through `hugo.yaml`, `go.mod`, and `go.sum`.

PaperMod owns the list/single templates, favicon handling, canonical URL, Twitter cards, and JSON-LD metadata. The project keeps a custom homepage layout in `layouts/index.html` and small local partial overrides for the header, footer, and Open Graph metadata.

## CSS

Tailwind CSS `4.3` is compiled by PostCSS before Hugo runs:

```sh
mise exec -- npm run build:css
```

The source file is `assets/tailwind/input.css`. The generated file is `assets/css/extended/custom.css`, which PaperMod automatically includes in its extended CSS bundle. Hugo then minifies, fingerprints, and publishes the combined stylesheet.

`assets/css/extended/custom.css` is generated and ignored by Git. Use the npm scripts instead of running `hugo` directly so the CSS exists before Hugo starts.

Tailwind Preflight is intentionally not imported, so PaperMod's base styling remains stable and the custom homepage CSS only adds the Bazarstore-specific presentation layer.

## Content

The homepage content lives in `content/_index.md`.

The page uses front matter for reusable structured content:

- `title`
- `kicker`
- `description`
- `status`
- `intro`
- `highlights`
- `story_blocks`
- `route_to_market`
- `why_partner_with_us`
- `capability_groups`

The current content language is English (`en-US`). The public site domain is configured as `https://bazarstore.biz/`.

## SEO And Indexing

Current SEO baseline:

- canonical URL is generated from Hugo `.Permalink`
- `baseURL` is set to `https://bazarstore.biz/`
- meta description is kept in a normal snippet range
- empty taxonomy pages are disabled with `disableKinds`
- sitemap contains only the homepage for the current one-page placeholder

Recommended next additions before broader production use:

- deeper company pages when the placeholder becomes a full website
- supplier/contact forms if Netlify Forms or another backend is selected
- downloadable company profile PDF
- documented partner/category proof points

## Assets

Main assets:

- `static/images/bazarstore-biz-logo.svg`
- `static/images/bazarstore-hero.avif`
- `static/images/bazarstore-hero.webp`
- `static/images/bazarstore-hero.png`
- favicon files in `static/`
- `static/robots.txt`

The hero image uses AVIF/WebP with PNG fallback in the page CSS.

Important: files placed in `static/` are copied directly to `public/`. Do not keep private source files, editable design files, or internal documents in `static/`. Non-published source files should stay in `assets/source/`.

## Generated Files

Generated local files should not be committed:

- `public/`
- `resources/_gen/`
- `assets/css/extended/custom.css`
- `.hugo_build.lock`
- `.netlify/`
- `node_modules/`
- `.DS_Store`

These are covered by `.gitignore`.
