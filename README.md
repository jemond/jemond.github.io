# justinemond.com

Personal site for Justin Emond, founder of [Third and Grove](https://www.thirdandgrove.com).

An annotated reading list — everything read since 2017 — plus a current reading queue, greatest hits, and suggested reading lists by theme.

## Stack

Single `index.html`. No build step, no dependencies, no frameworks. Deployed via GitHub Pages on push to `master`.

## Deploy

```bash
git add index.html && git commit -m "..." && git push
```

GitHub Pages serves from `master`. The `CNAME` file points `justinemond.com` to the repo.

## Adding a book

See [CLAUDE.md](CLAUDE.md) for formatting rules and workflow.
