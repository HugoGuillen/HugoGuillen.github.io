# HugoGuillen.github.io

Personal academic website of Hugo Guillen-Ramirez, served at <https://HugoGuillen.github.io>.

Built with Jekyll and the [al-folio](https://github.com/alshedivat/al-folio) theme (MIT). Pushing to `master` builds the site with GitHub Actions and publishes it to the `gh-pages` branch.

## Where the content lives

| What | File |
|---|---|
| Home page bio | `_pages/about.md` |
| Publications | `_bibliography/papers.bib` (peer reviewed), `_bibliography/preprints.bib` |
| Research themes | `_projects/*.md` (shown on `/research/`) |
| Software | `_pages/software.md` |
| CV page | `_data/cv.yml`, PDF in `assets/pdf/` |
| News | `_news/YYYY-MM-DD-*.md` |
| Site settings | `_config.yml` |

## Local preview

```sh
bundle install
bundle exec jekyll serve
```
