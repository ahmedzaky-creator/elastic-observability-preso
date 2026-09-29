# Elastic Observability — Customer Cut

Customized version of the Elastic Observability company presentation with **8 slides removed** for customer delivery.

**Source:** https://elastic.github.io/observability-team/collaterals/observability-presentation/company-preso.html

## Removed slides (original player numbers 1–34)

| # | Label | File |
|---|-------|------|
| 7 | Streams to S3 | `streams-lake.html` |
| 16 | Columnar Engine | `columnar.html` |
| 19 | PromQL | `promql.html` |
| 20 | Migration | `migrate.html` |
| 24 | NS Hero | `nightshift-hero.html` |
| 31 | NS · Plug & Play | `ns-msg-plugplay.html` |
| 32 | AI Economics | `nightshift-ai-economics.html` |
| 33 | NS Reveal | `nightshift-reveal.html` |

**Result:** 26 active slides (was 34). Removed slides remain in `disabled` so you can re-enable them later via Overview (`G`) or by editing `fslides.config.js`.

## Artifacts

| File | Purpose |
|------|---------|
| `elastic-observability-preso.pptx` | PowerPoint export (26 slides, ~7.3 MB) |
| `company-preso.html` | Single-file standalone player (offline / email / open in browser) |
| `pages/index.html` | Same standalone bundle, ready for GitHub Pages |
| `dist/` | Multi-file static build (`company-preso.html` = player) |

## Present locally

```bash
cd ~/elastic-observability-preso
fslides serve
# → http://localhost:3000
```

Keys: `→` next · `G` overview · `N` notes · `F` fullscreen

## Re-export after edits

```bash
export PUPPETEER_EXECUTABLE_PATH="/Applications/Google Chrome.app/Contents/MacOS/Google Chrome"
fslides pptx
fslides export company-preso.html
fslides build dist
cp company-preso.html pages/index.html
```

## Publish to GitHub Pages (same github.io experience)

### Option A — single-file Pages site (simplest)

```bash
cd ~/elastic-observability-preso

# Create a new public repo on GitHub first, then:
git init
git add pages/index.html pages/elastic-observability-preso.pptx fslides.config.js README.md
git commit -m "Customer cut of Elastic Observability preso (26 slides)"

gh repo create elastic-observability-preso --public --source=. --remote=origin --push

# Deploy pages/ as the site root on gh-pages
git subtree push --prefix pages origin gh-pages
# OR: copy pages/* to a dedicated gh-pages branch manually
```

Then in GitHub: **Settings → Pages → Source: Deploy from a branch → `gh-pages` / root**.

URL will be:

```
https://<your-username>.github.io/elastic-observability-preso/
```

### Option B — one command with fslides (needs origin + Pages enabled)

```bash
cd ~/elastic-observability-preso
git init
git remote add origin git@github.com:<you>/elastic-observability-preso.git
# push main first, enable Pages on gh-pages branch in Settings
fslides publish
```

`fslides publish` builds a self-contained export and pushes it to the `gh-pages` branch.

### Option C — open without a repo

Double-click `company-preso.html` or drag it into Chrome. No server required.
