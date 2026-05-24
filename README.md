# Bazarstore LLC

Hugo placeholder website for **Bazarstore LLC** and the `bazarstore.biz` business division.

The site positions Bazarstore LLC as a full-cycle market-entry, import, logistics, distribution, compliance, retail access, public procurement, and brand-development partner for international suppliers entering the Azerbaijani market.

## Stack

- Hugo `0.161.1`
- `mise` for pinned local tooling
- Netlify-ready static deployment
- YAML-based site configuration in `hugo.yaml`
- Markdown/YAML page content in `content/_index.md`
- Custom Hugo layouts in `layouts/`
- Static favicon, logo, hero assets, and `robots.txt` in `static/`

## Quick Start

Install the pinned tool versions:

```sh
mise install
```

Run the local Hugo server:

```sh
mise exec -- hugo server --bind 127.0.0.1 --port 1313 --buildDrafts --cacheDir "$PWD/resources/_gen"
```

Open the local site:

```text
http://localhost:1313/
```

Build the production site:

```sh
mise exec -- hugo --cleanDestinationDir --ignoreCache --gc --minify --cacheDir "$PWD/resources/_gen" --noBuildLock
```

The generated site is written to `public/`.

## Netlify

Netlify configuration is stored in `netlify.toml`.

Production build:

```toml
[build]
  command = 'hugo --gc --minify --cacheDir "$PWD/resources/_gen"'
  publish = "public"
```

Production environment:

```toml
HUGO_VERSION = "0.161.1"
HUGO_ENV = "production"
HUGO_ENABLEGITINFO = "true"
```

Local Netlify development keeps `HUGO_ENV = "development"` through the `context.dev.environment` block.

## Project Structure

```text
archetypes/             Hugo content archetypes
assets/source/          Non-published source/design files
content/_index.md       Main page content and YAML data
data/                   Hugo data directory, currently unused
i18n/                   Hugo translation directory, currently unused
layouts/baseof.html     Base HTML, SEO tags, favicon links, and CSS
layouts/index.html      Homepage layout
layouts/list.html       Generic list layout
layouts/single.html     Generic single-page layout
static/                 Static assets copied directly to the published site
hugo.yaml               Hugo site configuration
mise.toml               Pinned Hugo version
netlify.toml            Netlify build and dev configuration
```

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

- Open Graph tags
- Twitter Card tags
- JSON-LD `Organization` schema
- `robots.txt`
- branded `404.html`

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
- `.hugo_build.lock`
- `.netlify/`
- `.DS_Store`

These are covered by `.gitignore`.
