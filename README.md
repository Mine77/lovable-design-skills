<div align="center">

# Lovable Design System Skill

**A portable Lovable-inspired design taste layer for coding agents.**

[![Skill](https://img.shields.io/badge/type-agent%20skill-111827?style=for-the-badge)](#)
[![Design](https://img.shields.io/badge/focus-frontend%20design-ff6b6b?style=for-the-badge)](#)
[![Portable](https://img.shields.io/badge/works%20with-Codex%20%7C%20Cursor%20%7C%20Claude%20Code-4f46e5?style=for-the-badge)](#)

</div>

This repository packages the design guidance behind Lovable-style frontend
generation into a reusable agent skill. It captures the prompt-level design
philosophy, curated palette / typography / layout presets, and interaction
flows that help an agent avoid generic AI UI and commit to a distinctive
visual direction.

> [!NOTE]
> This is an unofficial skill. It is not affiliated with, endorsed by, or
> maintained by Lovable.

## What It Does

`lovable-design-system` gives your coding agent a stronger design brief before
it writes UI code:

| Capability | What the skill adds |
| --- | --- |
| Design taste | A clear philosophy for bold, non-generic frontend design |
| Visual presets | 26 palettes, 15 font pairs, and 15 layout archetypes |
| Decision flow | Rules for when to ask visual preference questions and when to build |
| Redesign flow | A structured ritual for generating and applying design directions |
| Implementation guardrails | Token-based Tailwind / CSS variable guidance and SEO defaults |

Use it when building or refining landing pages, marketing sites, portfolios,
product surfaces, dashboards, and other frontend experiences where visual
quality matters.

## Quick Start

Install the skill from this repository with the Skills CLI:

```sh
npx skills add <repo-url> --skill lovable-design-system
```

Or copy the skill folder into your agent's skill directory:

```sh
cp -R lovable-design-system ~/.agents/skills/
```

Then ask your agent to use the skill when designing UI:

```text
Use the lovable-design-system skill to redesign this landing page.
```

## What's Inside

```text
lovable-design-system/
├── SKILL.md
└── references/
    ├── ask-questions-flow.md
    ├── design-directions-flow.md
    ├── font-pairs.md
    ├── layout-archetypes.md
    └── palette-presets.md
```

### `SKILL.md`

The entry point for agents. It defines the core philosophy, banned generic
defaults, implementation rules, SEO defaults, and the full decision loop.

### `references/palette-presets.md`

A curated library of 26 four-stop color palettes, grouped by mood and use case:
dark and sophisticated, light and airy, earthy, cool and calm, energetic,
romantic, seasonal, experimental, and authoritative.

### `references/font-pairs.md`

15 Google Fonts pairings that combine distinctive display type with readable
body type. Each pair includes guidance for the kind of product or page it suits.

### `references/layout-archetypes.md`

15 layout structures, from hero grids and bento grids to dashboards, magazines,
feeds, galleries, and broken grids.

### `references/ask-questions-flow.md`

The exact flow for asking visual preference questions when the user has not
provided a design direction. It keeps the agent focused on three concrete
choices: palette, typography, and layout.

### `references/design-directions-flow.md`

A redesign workflow for improving existing UI. It anchors on the current
screen, pins the user's taste, then generates three distinct rendered
directions before implementation.

## How Agents Use It

The skill follows a simple loop:

1. Decide whether the request is visual and design-open.
2. If the user already gave a direction, build with that direction.
3. If the direction is missing, ask visual choices for palette, typography,
   and layout.
4. Translate the chosen presets into a concrete creative brief.
5. Build with semantic design tokens instead of raw one-off color classes.
6. Run a visual QA pass and reject generic AI-looking output.

The result is less "default SaaS template" and more intentional art direction:
stronger type, clearer composition, bolder color, and UI that fits the product
instead of blending into every other generated landing page.

## Best For

- Frontend design systems
- Landing pages and marketing sites
- Portfolio and editorial pages
- Product dashboards and SaaS surfaces
- UI redesigns, polish passes, and visual direction exploration
- Agents that need a reusable taste layer across projects

## Not Included

- Project-specific tokens, components, or brand guidelines
- Runtime scaffolding for a particular framework
- Proprietary assets, images, logos, or fonts
- A replacement for human design judgment

## Design Principles

- Commit to one bold aesthetic direction.
- Avoid generic AI defaults like purple gradients, centered hero cards, and
  untouched shadcn styling.
- Use semantic tokens for color, gradients, shadows, and theme values.
- Pair expressive display type with readable body type.
- Make layout decisions intentionally, not by habit.
- Ask for visual preference only when it meaningfully improves the result.

## Credits

Built as a portable skill from Lovable-inspired design prompt patterns, then
organized into a framework-agnostic reference system for agents.
