# CLAUDE.md

How to update Hugo Guillen-Ramirez's academic website. Read this first; most updates are a
one-file edit followed by a local build.

Live site: <https://HugoGuillen.github.io>. Jekyll + the al-folio theme (2023 fork, lightly
customised). Pushing to `master` builds with GitHub Actions and deploys to the `gh-pages` branch.

## Ground rules

- **Never commit or push unless Hugo asks.** A push to `master` publishes the site. Work on a
  branch; a pull request into `master` runs the build without deploying.
- **Facts come from Hugo's grant workspace**, `/mnt/d/claude-grants`:
  - Publications: `papers.csv` (full author lists, DOIs, dates) and `blocks/publications.md` (authorship roles).
  - Positions, grants, teaching, talks: `cv/HugoGuillen_MAIN_FULLSCIENTIFIC.docx`, read with `pandoc "<file>" -t plain`.
  - Approved bio wording: `blocks/bio.md`. Research themes: `blocks/research-statement.md`.
  Never invent papers, numbers, roles or dates. If a date is unknown, ask or flag it.
- **Name:** write **Guillen-Ramirez** without accents. Accented forms stay only inside
  citations of papers published that way (they are in `papers.bib` on purpose).
- **Status labels:** accepted but unpublished = "in press". Conference abstracts = "congress
  abstract". Preprints and manuscripts under review go in `preprints.bib`, never `papers.bib`.
- **DigiK grant wording:** "named associated researcher; conceived and leads the AI and methods
  component; PI of record Prof. G. Beldi; co-applicant Dr O. Endrich". Never "leads a CHF 500k grant".
- **Public email:** hugoagr@gmail.com only.

## Where each piece of content lives

| Page | URL | Edit this |
|---|---|---|
| Home (bio, news, selected papers) | `/` | `_pages/about.md` |
| Publications | `/publications/` | `_bibliography/papers.bib`, `_bibliography/preprints.bib`, `_pages/publications.md` (`years:` list) |
| Research themes | `/research/` | `_projects/N_*.md` (one card each); page shell is `_pages/projects.md` |
| Software | `/software/` | `_pages/software.md` |
| CV | `/cv/` | `_data/cv.yml`; PDF at `assets/pdf/HugoGuillen_CV_FULL_SCIENTIFIC.pdf` |
| News (home page box, newest 6) | `/news/` | `_news/YYYY-MM-DD-slug.md` |
| Name, footer, social IDs, author highlighting | all pages | `_config.yml` |
| Colours and custom styles | all pages | `_sass/_variables.scss` (`$blue-color` = light accent `#0F6E6E`, `$cyan-color` = dark accent `#4DB6AC`); custom rules at the end of `_sass/_base.scss` |

The blog (`_posts/`, `newsletter.html`) is not in the navigation; leave it alone unless asked.

## Recipes

### Add a published paper
1. Add a BibTeX entry to `_bibliography/papers.bib`. The file is **newest first**, and the
   order within a year is the display order, so insert it in the right place.
2. Custom fields this theme reads: `abbr` (venue badge, e.g. `{JAMIA}`), `selected = {true}`
   (shows on the home page; keep it to five), `note` (a line under the venue, e.g.
   `{In press (accepted October 2026).}` or `{Shared first authorship.}`), `code`, `pdf`,
   `html`, `abstract`, `bibtex_show = {true}`, `doi`. Fields `additional_info`, `award` and
   `related_publications` are **not** supported by this fork.
3. If the year is new, add it to `years:` in `_pages/publications.md`, or the entry is silently hidden.
4. Add a news item (below) and, if it fits a theme, a line on the matching `_projects/` card.
5. Keep `papers.csv` in the grant workspace as the source of truth; update it there too if Hugo asks.

**In press to published:** remove the "In press" `note`, add `volume`, `number`, `pages`,
`month`, and an `html` link once the DOI resolves. Update the "in press" wording in
`_pages/about.md`, `_projects/5_equity_audit.md`, `_pages/software.md` and `_data/cv.yml`
(grep for `in press`).

**Preprint accepted:** move the entry from `preprints.bib` to `papers.bib` and relabel it.

### Add a news item
Create `_news/YYYY-MM-DD-slug.md`:
```markdown
---
layout: post
date: 2026-10-01
inline: true
related_posts: false
---
One or two sentences in Markdown, first person, with a doi: link.
```

### Update the CV page
Edit `_data/cv.yml`. It is a list of sections, each `{title, type, contents}` with type
`map`, `list`, `nested_list` or `time_table`. Copy an existing section of the same type.
- Values are **raw HTML, not Markdown**: write `<a href="...">text</a>` and `<em>...</em>`.
- `time_table` items take `year`, `title`, `institution`, `description` (a list of strings).
- When the CV PDF changes, copy the new export over
  `assets/pdf/HugoGuillen_CV_FULL_SCIENTIFIC.pdf` (keep that filename; `_pages/cv.md` points to it).

### New position or title change
Update all of these together (grep for the old title to catch stragglers):
`_pages/about.md` (subtitle, address block, first paragraph), `_config.yml` (`description`,
`footer_text`), `_data/cv.yml` (Current/Previous positions), and add a news item.

### Add or edit a research theme
Each `_projects/N_slug.md` has `layout: page`, `title`, `description` (card text),
`importance` (sort order) and optional `github` (adds a GitHub icon to the card). The body is
the detail page: one or two paragraphs, then a "Publications and code" list.

### Add a software project
Add a section to `_pages/software.md`. The page body sits inside
`<div class="software" markdown="1">`; keep the `markdown="1"`, or Markdown inside renders as raw text.

### Replace the photo
Back up the original, then resize to 800 px wide and under 150 KB:
```sh
convert new.jpg -auto-orient -strip -colorspace sRGB -resize 800x -sampling-factor 4:2:0 \
  -interlace JPEG -quality 82 -define jpeg:extent=150KB assets/img/prof_pic.jpg
```

## Pitfalls already hit

- **Front-matter `description` must be plain text.** The theme copies it into a `<meta>` tag,
  so an HTML link there leaks as stray text at the top of the page. Put links in the body.
- **Author highlighting is exact-match.** `scholar.last_name` and `scholar.first_name` in
  `_config.yml` list every spelling used in `papers.bib` (`Hugo`, `Hugo A.`, `H. A.`,
  `Guillén-Ramírez`, `Guillen`, ...). A new spelling must be added there or the name is not underlined.
- **Author truncation:** `max_author_limit: 3`, but `_layouts/bib.html` was patched to always
  show authors up to and including Hugo. Keep that patch if the layout is ever replaced.
- **Card titles** used to be forced lowercase; `text-lowercase` was removed from
  `_includes/projects.html` and `_includes/projects_horizontal.html`.
- **`og_image`** in `_config.yml` must be an absolute URL.
- **`node_modules/` is git-ignored** and must stay out of the repo (it was 71 MB once).
- Do not reintroduce `polyfill.io` or `cdn.rawgit.com`; use `cdn.jsdelivr.net`.

## Build and check locally

Docker is not usable in this WSL setup, and `gh` is not installed. Native Ruby works
(Ruby 2.7.5 locally, 3.2.1 in CI):
```sh
cd /mnt/d/HugoGuillen.github.io
bundle install
bundle exec jekyll build --strict_front_matter
```
Quick checks on the output:
```sh
grep -o '<em>[^<]*Guill[^<]*</em>' _site/publications/index.html | wc -l   # one per paper
grep -l 'content="[^"]*<a' _site/*/index.html _site/index.html              # should print nothing
```
To see pages, serve `_site` with `python3 -m http.server 8765` and screenshot with the snap
Chromium. It cannot write to `/tmp`, so save under `~/snap/chromium/common/`:
```sh
/snap/bin/chromium --headless --no-sandbox --hide-scrollbars --virtual-time-budget=4000 \
  --window-size=1280,1600 --screenshot=$HOME/snap/chromium/common/shots/home.png http://localhost:8765/
```
Check desktop (1280 px) and phone (390 px) widths.

## Deployment

`.github/workflows/deploy.yml`: on push to `master` it installs Ruby 3.2.1 and gems, installs
`mermaid.cli` globally with npm (there is no `package.json`), runs `bundle exec jekyll build`,
and publishes `_site/` to `gh-pages`. On a pull request it builds but does not deploy.
