# Personal academic website (Quarto → GitHub Pages)

A single page that gathers links to material already public elsewhere
(journal DOIs, RePEc/IDEAS, ORCID, arXiv, Zenodo). The site hosts no PDFs.

## Structure
```
_quarto.yml              navbar, theme, footer, site-url
index.qmd                home / bio
research.qmd             publications table (from publications.yml) + working papers
publications.yml         one block per journal article
papers/<slug>/index.qmd  one page per working paper, linking to RePEc/arXiv/Zenodo
teaching.qmd             course descriptions
notes.qmd, notes/        short posts (hidden until the first one is written)
styles.scss, styles-dark.scss   colors and fonts
```

## Keeping things off the site
- `draft: true` in a page's front matter → not published, not listed.
- File name starting with `_` → never rendered.
- `.gitignore` → never leaves your computer.

## Routine
Edit → preview (`quarto preview`) → commit and push. Every push to `main`
rebuilds the site (see `.github/workflows/publish.yml`).

## Adding content
- **Publication:** add a block to `publications.yml` (title, author, date,
  subtitle = journal, path = DOI URL). Also update "Recent publications" in index.qmd.
- **Working paper:** in `papers/<slug>/index.qmd` put the RePEc/arXiv and Zenodo links,
  delete `draft: true`, and uncomment the "Working papers" block at the end of research.qmd.
  For another paper, copy the folder to `papers/new-slug/`.
- **Note:** copy `notes/_template.qmd` to `notes/2026-10-15-some-title.qmd`.
  For the first one, delete `draft: true` in notes.qmd and uncomment Notes in `_quarto.yml`.

## Publishing (once)
The GitHub repo is `estebancolla/estebancolla.github.io`.
1. In R, from this project: `usethis::use_git()`
2. Connect and push:
   `usethis::use_git_remote("origin", "https://github.com/estebancolla/estebancolla.github.io.git")`
   then in the Terminal: `git push -u origin main`
3. Terminal: `quarto publish gh-pages` (creates the gh-pages branch).
4. GitHub → repo Settings → Pages → source: branch `gh-pages`.
