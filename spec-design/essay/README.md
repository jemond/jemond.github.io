# Essay page — build spec

Static HTML + CSS. No build step, no JS, no dependencies beyond Google Fonts.
Design direction: **Editorial** (option 1b from \`Essay Page.dc.html\`).
Reference render: \`Essay — Final.dc.html\` in this project.

## Files

| File | Goes to |
|---|---|
| \`essay.css\` | \`/essays/essay.css\` |
| \`250-years/index.html\` | \`/essays/250-years/index.html\` |
| \`_template.html\` | keep out of the deployed site; copy per new post |

Link it from the bio line on the homepage — wrap "United States" (or "America")
in \`<a href="/essays/250-years/">\`.

## Publishing a post

1. \`cp _template.html essays/<slug>/index.html\`
2. The stylesheet is linked as \`../essay.css\`, which resolves from
   \`/essays/<slug>/index.html\`. Keep that folder-per-post structure.
3. Fill in title, \`<time>\` (both the \`datetime\` attribute and the visible
   text), description, canonical URL.
4. Write the body as plain \`<p>\` elements. Delete the furniture block you
   do not need.

The same template carries a 200-word riff and a 5,000-word essay. Nothing
about the page changes with length — only the amount of body copy.

## The system

- **One reading column, 640px** (\`--measure\`), ~68 characters per line.
- **A 190px margin column to its left** (\`--margin-col\`) that only pull
  quotes occupy. Everything else spans the reading column.
- Collapses to a single column at 960px; type steps down at 560px.

### Type

| Role | Font | Size / leading |
|---|---|---|
| Title | Libre Caslon Display 400 | clamp(2.25rem, 5.2vw, 3.6rem) / 1.04, -0.02em |
| Body | Libre Caslon Text 400 | 1.09rem / 1.66 |
| Pull quote | Libre Caslon Display 400 | 1.5rem / 1.26 |
| Subhead (h2) | Libre Caslon Display 400 | 1.62rem / 1.2 |
| Meta, labels, footer | IBM Plex Mono 400/500 | 11px, 0.16–0.2em tracking, uppercase |

### Color

\`--paper #f3efe6\` · \`--ink #14120f\` · \`--ink-muted #8a857c\` ·
\`--accent oklch(0.42 0.11 25)\` (oxblood: dates, drop cap, pull quotes, hover)

Two rule weights only: 2px solid ink for structural rules (masthead, footer),
1px 18%-ink for soft dividers.

### Rules of the road

- The drop cap is automatic (\`p:first-of-type::first-letter\`). Never hand-mark it.
- Pull quotes are **verbatim** lines from the essay, under ~15 words, max two per post.
- No hero images, no author photo, no reading time, no tags, no share buttons.
- Dates only.

## Notes for the developer

- \`color-mix()\` and \`oklch()\` are used deliberately; both are baseline in all
  current browsers. If a fallback is ever needed: accent ≈ \`#8a2b22\`.
- \`text-wrap: pretty\` / \`balance\` degrade to normal wrapping — no fallback needed.
- Self-host the three fonts if you want to drop the Google Fonts request; the
  page is otherwise a single CSS file.
- Print styles are included: the page prints clean at 11pt with the accent
  flattened to black.
- Add \`prefers-reduced-motion\` nothing — there is no motion.
