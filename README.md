# narcopoliticos — Automated Website Mirror

An automated system that mirrors **narcopoliticos.com** weekly using **HTTrack**, **GitHub Actions**, and **GitHub Pages**.

## How it works

```
narcopoliticos.com → HTTrack (crawl) → GitHub Actions (cron) → gh-pages branch → GitHub Pages
```

1. A cron-scheduled GitHub Actions workflow runs every **Sunday at 03:00 UTC**.
2. [HTTrack](https://www.httrack.com/) crawls the full site and downloads all pages and assets.
3. An MD5 fingerprint detects whether the content changed — a new commit is pushed to the `gh-pages` branch **only when changes exist**.
4. GitHub Pages serves the `gh-pages` branch as a static site.

## Live mirror

> `https://saulmmendoza.github.io/narcopoliticos/`

## Setup guide

A full step-by-step guide to recreating this system for any website is available at:

> [`/mirror.html`](./mirror.html) — also served at `https://saulmmendoza.github.io/narcopoliticos/mirror.html`

## Repository structure

```
.github/workflows/mirror.yml   ← weekly automation workflow
mirror.html                    ← setup instructions page
README.md
```

## Quick start (for your own site)

```bash
# 1. Fork or clone this repo
gh repo fork saulmmendoza/narcopoliticos --clone

# 2. Edit the target URL in .github/workflows/mirror.yml

# 3. Enable read+write Actions permissions in Settings → Actions → General

# 4. Enable GitHub Pages from the gh-pages branch in Settings → Pages

# 5. Trigger the first run
gh workflow run mirror.yml
```

## License

Content mirrored from narcopoliticos.com is subject to its original copyright.
Workflow code and this repository's tooling are released under the MIT License.