# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Working preferences

- **Minimal, precise edits over rewrites.** Touch the smallest amount of code needed; don't reformat or restructure surrounding code while fixing something.
- **Propose before applying.** For anything beyond a trivial fix, describe the change first and wait for approval — don't apply it in the same turn.
- **Custom CSS goes through the HugoBlox hooks system**, not `assets/css/`. Use a head-end hook under `layouts/_partials/hooks/head-end/` (the existing `github-button.html` override is the pattern to follow). Editing `assets/css/` directly fights the module system and gets clobbered by upstream changes.
- **Research descriptions stay clear, descriptive, and jargon-free** — written for a broad academic audience, not specialists in one subfield. Prefer plain language over field-specific terms; spell out acronyms on first use.

## What this is

A personal academic site built from the HugoBlox **Academic CV** template (Hugo + Tailwind v4 + Pagefind). Source lives on `main`; the live site is `ctzag.github.io` (the `origin` remote is `github.com/ctzag/ctzag.github.io.git`).

`origin/master` exists but is an unrelated, empty orphan branch (no shared history with `main`, tree is empty). Nothing builds from it — ignore it.

## Common commands

Package manager is **pnpm** (`packageManager: pnpm@10.14.0`). Hugo version is pinned to **0.154.2 extended** in two places that must stay in sync: `hugoblox.yaml` (`build.hugo_version`) and `netlify.toml` (`HUGO_VERSION` env).

```bash
pnpm install           # first-time setup (also fetches Hugo modules via go.mod on first hugo run)
pnpm dev               # hugo server --disableFastRender (live preview at http://localhost:1313)
pnpm build             # hugo --minify && pagefind --site public
pnpm run pagefind      # rebuild search index against ./public only
```

There is no test suite and no linter. "Verifying a change" means running `pnpm dev` and checking the page in a browser.

## Architecture

This is a **Hugo Modules** site, not a vendored theme. The template's layouts, partials, blocks ("blox"), and CSS come from remote Go modules declared in `go.mod`:

- `github.com/HugoBlox/kit/modules/blox` — the page-building blocks
- `github.com/HugoBlox/kit/modules/slides` — Reveal.js slides
- `github.com/HugoBlox/kit/modules/integrations/netlify` — Netlify integration glue

`config/_default/module.yaml` declares those imports **and** the mount table that wires them into Hugo's virtual filesystem (e.g. community blox into `layouts/_partials/blox/community/`, their CSS into `assets/dist/community/blox/`). Local `layouts/` and `assets/` are also mounted, so anything you put at the same path in the local tree **overrides** the module version — that's how `layouts/_partials/hooks/head-end/github-button.html` works as a local override without forking the module.

Content is plain Markdown under `content/`:
- `_index.md` is the home page; sections like `#papers`, `#talks`, `#news` are anchors into blocks on that page (see `config/_default/menus.yaml`).
- `experience.md`, `projects/`, `courses/`, `publications/`, `blog/`, `events/`, `slides/` are top-level sections.
- `content/authors/` holds author profiles referenced by posts.

Site config is split across `config/_default/*.yaml` (languages, menus, module). There is no `hugo.yaml` at the repo root — all defaults come from `config/_default/` plus what the imported modules ship.

Static files served as-is live in `static/` (e.g. `static/uploads/resume.pdf`). Note: `public/` is in `.gitignore` as Hugo's build output, but a few PDFs under `public/uploads/` are tracked from before that rule — leave them unless intentionally cleaning up.

## Deploy

Two deploy paths are configured; both produce the same `public/` artifact.

1. **GitHub Pages (primary)** — `.github/workflows/deploy.yml` runs on push to `main` and on manual dispatch. It reads `hugo_version` out of `hugoblox.yaml`, installs Node 20 + pnpm, builds with `hugo --minify --baseURL <pages url>`, runs Pagefind if `package.json` mentions it, and deploys via `actions/deploy-pages@v4` to the `github-pages` environment. No `gh-pages` branch — Pages serves the workflow artifact directly.
2. **Netlify** — `netlify.toml` defines production / deploy-preview / branch-deploy contexts. Uses the `netlify-plugin-hugo-cache-resources` plugin to cache `resources/`.

Both workflows have `if: github.repository_owner != 'HugoBlox'` guards so they no-op on the upstream template repo.

## Automated publications import

`.github/workflows/import-publications.yml` watches `publications.bib` at the repo root. When that file changes on `main`, it runs the `academic` CLI to convert BibTeX → Markdown and opens a PR on a `hugoblox-import-publications` branch. **Heads-up:** the workflow writes to `content/publication/` (singular), while existing content lives in `content/publications/` (plural). If you ever add a `publications.bib`, verify where the generated PR lands before merging.
