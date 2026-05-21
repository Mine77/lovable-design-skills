# Design preference questions — when and how to ask

When a user's request is visual but the direction is unclear, let them
steer the look and feel before you build. The mechanism is a single round
of **three visual_choice questions**: palette, typography, layout.

If the runtime supports image generation, also generate visual previews for
the offered directions so the user can judge by sight, not only by names,
swatches, type samples, and wireframes.

This file is the contract. Follow it exactly.

---

## When to ask

Ask when the request is broad and design-open:

- "Build me a portfolio site" — no style specified.
- "Create a landing page for my startup" — no visual direction.
- "Make a travel blog" — could go many ways visually.
- "Build me a beautiful app" — the user is explicitly asking for input.

## When NOT to ask

- The user already gave specific direction
  ("minimal black and white, Swiss typography").
- The request is purely functional ("create a todo app", "build a
  calculator", "add auth", "fix this bug").
- The app type has obvious defaults: dashboards, admin panels, CRUD
  internal tools — these inherit the dashboard archetype + a neutral
  palette without asking.
- The user is refining existing UI ("make this card prettier") — use the
  design-directions flow instead, see `design-directions-flow.md`.

---

## The three questions

Always ask **palette + typography + layout**, in that order, in a single
round (one tool call, three questions).

### 1. Palette

- Type: `visual_choice` with the `colors` field on each option.
- 4 options, pulled from `palette-presets.md`.
- Pick presets that fit the project domain.
- Each option supplies a 4-stop hex array; the frontend renders them as
  swatch groups.

### 2. Typography

- Type: `visual_choice` with the `fontPair` field on each option.
- 4 options, pulled from `font-pairs.md`.
- Pick pairs that fit the project type. The frontend renders the heading
  font name set in itself plus a body sample set in the body font.

### 3. Layout

- Type: `visual_choice` with the `layout` field on each option.
- 4 options, pulled from `layout-archetypes.md`.
- Pick layouts that make sense for the project type — see the "make sure
  the options are visually distinct" rule in `layout-archetypes.md`.
- The frontend renders clean SVG wireframes.

### Do NOT add a fourth "what vibe?" text question.

The palette already communicates the vibe. A free-text vibe question is
redundant and almost always produces a worse answer than the swatches did.
You *may* add a single clarifying functional question (e.g. "what content
will this site have?") if you genuinely need it — never a style question.

---

## Optional image previews

Use this section only when the current agent environment has image-generation
capability. If it does not, the normal visual_choice UI is enough.

### What to generate

Generate a compact preview board or 3-4 separate UI mockup images that map to
the candidate presets. The previews should be fast decision aids, not final
designs.

Each preview should combine:

- one palette option from `palette-presets.md`
- one compatible typography option from `font-pairs.md`
- one compatible layout option from `layout-archetypes.md`

Prefer combinations that make the choices easier to compare. Example for a
marketing landing page:

- `Noir & Gold` + `Cormorant Garamond / Karla` + `broken-grid`
- `Neon Mint` + `Space Grotesk / DM Sans` + `bento-grid`
- `Paper & Ink` + `Instrument Serif / Work Sans` + `magazine`
- `Ocean Deep` + `Sora / Manrope` + `hero-grid`

### Prompting rules

- Render polished web UI mockups, not mood boards.
- Use abstract interface copy blocks or very short generic labels; do not rely
  on generated text being legible.
- Make the previews visually distinct in palette, type scale, density,
  spacing, and composition.
- Keep the project domain visible in the mockup structure when possible.
- Do not include brand names, logos, or copyrighted product marks unless the
  user provided them.
- If generating a single board, label choices outside the image in your
  message instead of relying on text inside the image.

### How to present

Show the generated previews together with the three visual_choice questions.
The user still chooses palette, typography, and layout as structured answers;
the images are supporting evidence.

If the user points at a preview instead of answering the structured questions,
map that preview back to its palette / typography / layout combination and
confirm the inferred picks before building.

---

## After the user answers

Translate the picks into a detailed creative brief — specific fonts, hex
colors, animation approaches, layout decisions. Infer the rest:

- Whitespace density: from layout (`gallery`/`masonry` → tight; `single-
  column` → generous) and palette (light palettes lean airy, dark ones
  lean dense).
- Border radius: from typography (geometric sans → 8–12px; serif editorial
  → 0–4px; rounded display → 16–24px).
- Animation intensity: from palette (Vapor Chrome, Sunset Blaze → richer
  motion; Paper & Ink, Navy Trust → restrained).
- Visual weight: from font weights, line-height, and the palette's
  contrast range.

The brief should be Awwwards-level specific. Then persist the selected
direction into `styleguide.md` when possible, following
`styleguide-persistence.md`. Then build.

---

## Rules of engagement

- Do NOT use this tool to ask about technical internals (table names,
  file paths, framework choice).
- Do NOT ask the user to pick a storage provider, an auth provider, or an
  AI provider. Default to whatever the platform ships and only offer
  alternatives if the user explicitly asks.
- Do NOT bundle a fourth design question. Three visual_choice + at most
  one functional clarifier.
- Each option needs a short, distinct description — no generic
  "modern and clean" labels on multiple options.
