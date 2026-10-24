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
| `Dockerfile`, `docker-compose.yml` | Local development environment |
| `.github/workflows/deploy.yml` | CI: build site + deploy to GitHub Pages |

## Content lives in

- `_pages/` — top-level pages (about, cv, publications, projects, blog, etc.)
- `_posts/` — blog posts (filenames: `YYYY-MM-DD-title.md`)
- `_news/` — short news items rendered on the homepage
- `_projects/` — research-theme cards, rendered on `/research/` by `_pages/projects.md`
- `_bibliography/` — `papers.bib` (peer reviewed, grouped by the `years:` list in `_pages/publications.md`) and `preprints.bib` (shown separately; never move a preprint into `papers.bib` until it is accepted)
- `_data/cv.yml` — structured CV data consumed by the CV page (values are raw HTML, not Markdown)
- `_pages/software.md` — open-source tools

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
2. Installs `mermaid.cli` globally with npm (there is no `package.json`).
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

## Content rules

- Spell the name **Guillen-Ramirez** without accents, except inside reproduced citations of papers published with accents.
- The source of truth for publications, positions and grants is Hugo's grant workspace (`papers.csv` and the full scientific CV). Do not invent papers, metrics or roles.
- Label in-press papers "in press" and congress abstracts "congress abstract". Preprints go in `preprints.bib` only.
- Do not push to `master` without Hugo's go-ahead: a push deploys the public site.
