# CLAUDE.md

Orientation for Claude Code sessions on this repo.

## What this is

Hugo Guillen's personal/academic website, served at
`https://HugoGuillen.github.io`. Built with **Jekyll** using the
[**al-folio**](https://github.com/alshedivat/al-folio) theme and deployed
to GitHub Pages via GitHub Actions.

## Key files

| Path | Purpose |
|------|---------|
| `_config.yml` | Main Jekyll site configuration |
| `Gemfile` | Ruby gem dependencies (Jekyll + plugins) |
| `package.json` | NPM deps (only `@mermaid-js/mermaid-cli` for diagram rendering at build time) |
| `Dockerfile`, `docker-compose.yml` | Local development environment |
| `.github/workflows/deploy.yml` | CI: build site + deploy to GitHub Pages |

## Content lives in

- `_pages/` — top-level pages (about, cv, publications, projects, blog, etc.)
- `_posts/` — blog posts (filenames: `YYYY-MM-DD-title.md`)
- `_news/` — short news items rendered on the homepage
- `_projects/` — project portfolio entries
- `_bibliography/` — BibTeX entries for the publications page
- `_data/cv.yml` — structured CV data consumed by the CV page

## Templating & assets

- `_layouts/` — page templates (`default.html`, `post.html`, `about.html`, `distill.html`, …)
- `_includes/` — reusable Liquid partials
- `_includes/scripts/` — `<script>` tag partials (mathjax, analytics, bootstrap, …)
- `_sass/` — SCSS source
- `assets/` — compiled CSS, JS (`assets/js/`), images (`assets/img/`), fonts, etc.
- `_plugins/` — custom Jekyll plugins

## Local development

Preferred (matches CI):

```sh
docker compose up
# site served at http://localhost:8080
```

Native (requires Ruby 3.2.1 + Bundler):

```sh
bundle install
bundle exec jekyll serve
```

## Deployment

Pushing to the default branch (`master`) triggers
`.github/workflows/deploy.yml`, which:

1. Sets up Ruby 3.2.1 and installs gems.
2. Runs `npm install` (for the mermaid CLI).
3. Runs `bundle exec jekyll build`.
4. Publishes `_site/` via `JamesIves/github-pages-deploy-action`.

## Security note

Avoid adding `<script>` tags that load from abandoned or compromised
CDNs. In particular, do **not** reintroduce `polyfill.io` — the
domain was sold in June 2024 and began serving malicious code, and was
blocked by Cloudflare/Google. Modern MathJax (v3+) and the rest of the
site work fine without it on every browser this site supports. Prefer
`cdn.jsdelivr.net` or vendoring small libraries directly under
`assets/js/` when an external dependency really is needed.
