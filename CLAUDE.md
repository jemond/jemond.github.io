# justinemond.com Site Instructions

## Repo & Deploy
- Local path: `/Users/justin/claude/justinemond.com/`
- GitHub: `git@github.com:jemond/jemond.github.io.git` (SSH)
- **The live site is everything under `docs/`.** GitHub Pages is configured (repo Settings → Pages) to serve from `master` / `/docs`, not the repo root. Files outside `docs/` (this file, `.claude/`, `README.md`, `spec-design/`) are in the repo but never served on justinemond.com.
- Push to `master` branch to deploy — anything under `docs/` goes live; everything else is just repo housekeeping.

## Books I've Read — Format
New books go at the **top** of the `<ol class="booklist">` list (numbering runs high-to-low, newest first — bump every existing number by one, or just recompute from the total count). Format:

```html
<li><span class="num">N</span><span class="entry"><em>Full Title: Full Subtitle</em>, <strong>by First Last</strong> &mdash; Review text.</span></li>
```

Rules:
- Always look up the **full proper title and author** before adding any book
- Author is wrapped in `<strong>`, prefixed with "by "; annotation is separated by `&mdash;`
- No category labels

## Current Reading List — Format
Located below the Books I've Read section, `<ol class="plainlist">`. Format:

```html
<li><em>Full Title: Full Subtitle</em>, by First Last</li>
```

Rules:
- Always look up the **full proper title and author**
- Author is plain text, not bold — no annotation
- No category labels (e.g., no "History —", "Economics —")
- Update the `<p class="section__meta">Updated [Month Year]</p>` line when updating

## Greatest Hits — Format
`<ul class="titlelist">`. Title only, no `<em>`, no author, no annotation:

```html
<li>Full Title: Full Subtitle</li>
```

A book only needs to already appear in Books I've Read to be added here.

## Suggested Reading Lists — Format
Each themed list is a `<div><h2>Label</h2><ol class="numlist">…</ol></div>` inside `.listgroup`. Same title-only rule as Greatest Hits — no `<em>`, no author:

```html
<li>Full Title</li>
```

## Books Started but Not Finished ("Abandoned") — Format
`<ol class="numlist numlist--annotated">`. Title in `<em>`, plus a short reason after an em dash:

```html
<li><em>Full Title</em> &mdash; reason.</li>
```

## Layout
- The homepage uses the same `.layout` grid as an essay: a 190px margin column (holds `.section__label`) beside the 640px reading column (`.section__body`). Every section is two siblings sharing `.section-top` so their rules align across the gutter.
- Collapses to one column at 960px — labels move above their body.

## SEO
- `<meta name="description">`, Open Graph, Twitter card tags, canonical link, and a `Person` JSON-LD block live in `<head>`. Update the description/OG copy if the page's purpose changes.
- `robots.txt` and `sitemap.xml` live at `docs/` (the served root) alongside `docs/index.html`.

## Essays
Long-form pieces (e.g. things originally written for LinkedIn) live at `docs/essays/<slug>/index.html` (served at `/essays/<slug>/`), styled by the shared `/site.css` (same stylesheet as the homepage — link it as `/site.css`, an absolute path, since essay pages are nested one level deeper than `index.html`). The `<article>` carries both `class="essay layout"`. No hero images, author photo, reading time, tags, or share buttons — dates only.

**Publishing a new essay:**
1. `cp docs/essays/_template.html docs/essays/<slug>/index.html` (the template starts with `_` so Jekyll/GitHub Pages excludes it from the deployed site — keep it that way)
2. Fill in title, `<time datetime>` + visible date, meta description (doubles as the LinkedIn share blurb), canonical URL, and OG tags
3. Write the body as plain `<p>` elements
4. If the piece was originally posted elsewhere (e.g. LinkedIn), credit it at the end of the body: `<p class="essay__source">Posted Month D, YYYY on <a href="URL">LinkedIn</a>.</p>` — never fabricate this URL/date, ask if unknown
5. Add the new URL to `sitemap.xml`
6. Link to it from wherever references the piece (e.g. the homepage bio line)

Rules:
- Pull quotes (`<blockquote class="pullquote">`) must be verbatim lines from the essay, under ~15 words, max two per post
- Never hand-mark the drop cap — it's automatic CSS on the first paragraph's first letter
- The same template covers a 200-word riff and a 5,000-word essay; only the amount of body copy changes

## Design
Colors, fonts, and typography rules are documented in `.claude/design.md`.

## Workflow
1. Look up full title + author for any book before touching the HTML
2. Edit `docs/index.html`
3. `git add docs/index.html && git commit && git push`
