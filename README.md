# Indi-RomCoM Guide

A documentation site, built with Hugo and the [Hextra](https://github.com/imfing/hextra) theme, about the paper *Indi-RomCoM: Code-Mixed Benchmark for Evaluating LLMs on Romanized Indic-English Instructions* (arXiv 2606.30790). It covers the paper, its pipeline and results, a validated list of issues, and the Telugu extension plan.

## Layout

```
hugo.yaml                  site config (menu, search, theme options)
content/                   all pages (Markdown)
  docs/issues/             the issue list, one page per severity group
assets/css/custom.css      accent color and status-chip styles
assets/js/flexsearch.js    override so search works on any sub-path
assets/vendor/             FlexSearch + Mermaid, bundled (no CDN at build time)
themes/hextra/             Hextra theme (vendored copy, commit e58687e)
.github/workflows/pages.yml  GitHub Pages deploy
```

## Run locally

Install Hugo **extended** 0.146 or newer (`brew install hugo` on macOS), then run:

```bash
hugo server            # http://localhost:1313
hugo --gc --minify     # build into ./public
```

## Deploy to GitHub Pages

1. Create a repo, e.g. `indi-romcom-guide`, and push this folder to `main`.
2. In the repo, go to **Settings → Pages → Source** and choose **GitHub Actions**.
3. The workflow builds and publishes the site to `https://<your-user>.github.io/indi-romcom-guide/`.

Links are relative and use `.html` file names, so the site works under a sub-path without changing `baseURL`.

## Editing

- Add a page by creating `content/docs/<name>.md` with `title` and `weight` front matter.
- Status chips on issue pages are plain HTML: `<span class="st st-ok">Confirmed</span>`.
- Link to pages with root paths and `.html`, e.g. `[C5](/docs/issues/critical.html#c5-nli-labels-are-mapped-two-different-ways)`.
