# Layout archetypes

The full layout library available when asking the user to choose a page
structure. Each archetype renders as a clean SVG wireframe in the visual
choice question, so the user picks composition, not content.

When asking, pick **three or four** layouts that make sense for the project
type — a portfolio should get masonry / hero-grid / gallery, NOT dashboard.
An e-commerce site should get card-grid / hero-grid, NOT feed. Make sure
the options are visually distinct from each other: don't pair
`single-column` with `full-width-sections` in the same question, they read
the same at wireframe scale.

---

| id                     | Shape                                                | Best for                                  |
| ---------------------- | ---------------------------------------------------- | ----------------------------------------- |
| `hero-grid`            | Hero banner + card grid below                        | Marketing landings, product showcases     |
| `single-column`        | Centered stacked content                             | Long-form, essays, focused storytelling   |
| `split-screen`         | Two-column hero (50/50)                              | Pre-launch, lead-gen, app marketing       |
| `sidebar`              | Side nav + main content                              | Docs, workspace shells, admin             |
| `masonry`              | Staggered grid of varied tiles                       | Portfolios, galleries, image-heavy        |
| `bento-grid`           | Mixed-size grid (Apple-style)                        | Product features, design systems          |
| `magazine`             | Featured story + secondary grid                      | Editorial, news, publishing               |
| `dashboard`            | Header + sidebar + multi-panel canvas                | SaaS dashboards, analytics, tools         |
| `full-width-sections`  | Stacked full-width bands                             | Brand sites, scrollytelling               |
| `zigzag`               | Alternating image/text rows                          | Feature explainers, product tours         |
| `card-grid`            | Uniform equal-sized cards                            | E-commerce, course catalogs, directories  |
| `asymmetric`           | Unequal two-column (60/40 or 70/30)                  | Editorial portfolios, agency sites        |
| `broken-grid`          | Overlapping, off-grid elements                       | Fashion, music, experimental brand        |
| `feed`                 | Chronological content stream                         | Social, blogs, changelogs                 |
| `gallery`              | Thumbnail grid (uniform tiles)                       | Photography, illustration portfolios      |

---

## Once the user picks

The chosen layout sets a *structural contract* for the rest of the build:

- `hero-grid`, `bento-grid`, `card-grid` → maintain a clear column rhythm
  (12-col grid, 24–32px gutters); align hero to grid.
- `single-column`, `magazine` → cap measure around 65–75ch for body copy.
- `split-screen` → keep both halves equally weighted in visual mass; don't
  let the form side shrink under 40% on desktop.
- `sidebar`, `dashboard` → fix the sidebar width (240–280px), make the
  canvas `min-w-0` so flex children don't blow out.
- `masonry`, `gallery`, `feed` → use container queries / CSS columns
  rather than JS measuring where possible.
- `zigzag` → alternate every other row; ensure both image and text sides
  are vertically centered.
- `broken-grid`, `asymmetric` → keep a hidden underlying grid so the
  "broken" elements still feel composed, not accidental.

Do not silently swap the chosen archetype mid-build. If the content
clearly doesn't fit, surface it and re-ask.
