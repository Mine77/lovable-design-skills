# Styleguide persistence

Persist the user's selected UI aesthetic so future work can build from the
same taste instead of re-asking or drifting.

---

## When to read

Before any visual implementation, look for `styleguide.md` at the project
root.

- If it exists, read it and follow it as the default aesthetic direction.
- If it conflicts with the user's latest explicit request, the latest user
  request wins; update the file after the new direction is chosen.
- If multiple styleguide-like files exist, prefer the root `styleguide.md`
  and mention any ambiguity briefly.

## When to write

Create or update `styleguide.md` after the user selects a visual direction
through either:

- the three visual_choice questions from `ask-questions-flow.md`
- the rendered direction picker from `design-directions-flow.md`
- an explicit user instruction such as "use this style going forward"

Do this on a best-effort basis. If the environment cannot write files, present
the markdown content inline.

## Update rules

- Preserve any existing project or brand context.
- Add or replace a section named `## Current UI direction`.
- Include enough detail for another agent to implement consistently without
  re-asking the user.
- Keep the file human-readable; this is a design contract, not a config dump.
- Use semantic token names, not only raw color classes.

## Suggested template

```md
# Styleguide

## Current UI direction

Last updated: YYYY-MM-DD

### Summary

One concise paragraph describing the chosen aesthetic, product tone, and what
the interface should avoid.

### Palette

- Preset: <preset id / name>
- Colors: `#000000`, `#111111`, `#222222`, `#333333`
- Usage:
  - Background:
  - Foreground:
  - Primary:
  - Accent:

### Typography

- Preset: <font pair id>
- Display: <heading font>
- Body: <body font>
- Rules:
  - Heading weight / line-height:
  - Body weight / line-height:
  - Accent usage:

### Layout

- Archetype: <layout id>
- Structure:
  - Grid:
  - Density:
  - Spacing:
  - Responsive behavior:

### Components

- Radius:
- Borders:
- Shadows:
- Buttons:
- Cards / panels:
- Navigation:

### Motion

- Intensity:
- Preferred patterns:
- Avoid:

### Implementation notes

- Use CSS variables / Tailwind semantic tokens for colors, gradients, and
  shadows.
- Avoid raw one-off color utilities in components.
- Preserve this styleguide unless the user explicitly changes direction.
```
