# Repository Guidelines

## Project Structure & Module Organization

This is a small Jekyll static site for `catloafprod.com`.

- `index.html` contains the main page markup and Liquid variables.
- `_config.yml` holds site metadata, social links, image paths, plugins, and default build settings.
- `_config_prod.yml` adds Cloudflare production image transform settings.
- `_includes/` contains reusable snippets such as analytics, favicon tags, and the SVG logo.
- `_layouts/` is present for Jekyll layout support, though the current page is mostly self-contained.
- `css/front.css` is a Jekyll-processed stylesheet with Liquid image paths.
- `imgs/` contains source image assets. `_site/` and `.jekyll-cache/` are generated output/cache directories; do not edit them directly.

## Build, Test, and Development Commands

Always run shell and build commands through `rtk` in this repository.

- `rtk bundle install` installs Ruby dependencies from `Gemfile`.
- `rtk bundle exec jekyll serve` runs the site locally, usually at `http://127.0.0.1:4000/`.
- `rtk bundle exec jekyll build` builds the site into `_site/` using `_config.yml`.
- `rtk bundle exec jekyll build --config _config.yml,_config_prod.yml` builds with production Cloudflare image prefixes.

## Coding Style & Naming Conventions

Use existing style over broad rewrites. Keep HTML and Liquid readable with two- or four-space indentation matching the surrounding block. Prefer semantic HTML where practical, and keep Liquid expressions simple (`{{ site.name }}`, `{% include favicon.html %}`). CSS selectors currently use a mix of element selectors, IDs, and descriptive classes such as `.artist-box`; follow that pattern for small additions. Image filenames in `imgs/` should be lowercase and descriptive, using hyphens when needed.

## Testing Guidelines

There is no automated test suite. Validate changes by running a Jekyll build and, for visual or content changes, serving the site locally. Check the rendered page for broken image paths, social links, SEO metadata, and production image-prefix behavior when `_config_prod.yml` is involved.

## Commit & Pull Request Guidelines

Recent commits use short, imperative or descriptive subjects such as `Update company name`, `Use Cloudflare image transforms`, and `Added CSP headers`. Keep commits focused on one change. Pull requests should include a brief summary, the build command run, any visual impact, and screenshots for layout, image, or branding changes.

## Security & Configuration Tips

Do not commit secrets or private analytics credentials. Treat `_config.yml`, `headers`, and generated SEO/metadata changes as production-facing configuration. When changing external links, analytics, or Cloudflare image handling, verify both local and production build behavior.
