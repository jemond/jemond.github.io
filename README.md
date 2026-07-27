# justinemond.com

Personal site for Justin Emond, founder of [Third and Grove](https://www.thirdandgrove.com).

An annotated reading list — everything read since 2017 — plus a current reading queue, greatest hits, and suggested reading lists by theme.

## Stack

Static HTML styled by one shared stylesheet, `site.css`. No build step, no dependencies, no frameworks. Deployed via GitHub Pages on push to `master`.

**The live site is `docs/`, not the repo root.** GitHub Pages is configured to serve from `master` / `/docs`, so everything reachable on justinemond.com lives under `docs/`; everything outside it (this file, `CLAUDE.md`, `spec-design/`) is repo-only.

- `docs/index.html` — homepage
- `docs/essays/<slug>/index.html` — long-form pieces, same design system as the homepage (see `docs/essays/_template.html` to publish a new one)
- `docs/robots.txt` and `docs/sitemap.xml`. `docs/CNAME` points GitHub Pages at the custom domain.

## Deploy

```bash
git add docs/index.html && git commit -m "..." && git push
```

GitHub Pages serves from `master` / `/docs`. The `docs/CNAME` file points `justinemond.com` to the repo.

## Adding a book

See [CLAUDE.md](CLAUDE.md) for formatting rules and workflow.
