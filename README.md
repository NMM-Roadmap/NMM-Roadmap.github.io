# Project Page — Toward Native Multimodal Modeling

Static GitHub-Pages site for the paper. **No build step required**: this folder is everything.

## Local preview

```bash
cd web
python3 -m http.server 8000
# open http://localhost:8000
```

## Deploy to GitHub Pages

You have several options. Pick one:

### Option A — Repo with `/web` as Pages root (easiest)

1. Push this repo to GitHub.
2. Settings → Pages → **Source: Deploy from a branch**.
3. **Branch**: `main`, **Folder**: `/web`.
4. Wait ~1 min, your site is live at `https://<user>.github.io/<repo>/`.

### Option B — Dedicated `gh-pages` branch

```bash
# from the repo root
git checkout --orphan gh-pages
git rm -rf .
cp -r web/. .
echo > .nojekyll
git add . && git commit -m "publish project page"
git push -u origin gh-pages
# then: Settings → Pages → Source: gh-pages branch, root /
```

### Option C — User/org root site

If this repo is named `<user>.github.io`, just push the `web/` contents to the
default branch root.

## Files

| File | Purpose |
|---|---|
| `index.html` | The single-page site (Tailwind + Alpine.js, all from CDN) |
| `data/models.json` | 43 native multimodal models extracted from the paper |
| `.nojekyll` | Tells GitHub Pages to skip Jekyll processing |

## Customizing

- **Authors / arXiv link / PDF link**: edit the `<header id="top">` block in `index.html`.
- **Add / edit models**: re-run `python3 ../../tmp/extract_models.py` after updating
  `paper/intro_original_backup.tex`, **or** just edit `data/models.json` directly.
- **BibTeX**: edit the `<pre id="bibtex-text">` block inside the *Cite* section.
- **Color scheme**: tweak the `tailwind.config.theme.extend.colors` block at the
  top of `index.html`.

## Tech stack

- [Tailwind CSS](https://tailwindcss.com) (CDN, JIT in browser)
- [Alpine.js](https://alpinejs.dev) for reactivity (search/filter/sort)
- [Chart.js](https://www.chartjs.org) for the release timeline
- [Inter](https://rsms.me/inter/) + [JetBrains Mono](https://www.jetbrains.com/lp/mono/) via Google Fonts

No npm, no bundler, no node, no Jekyll. Just HTML.
