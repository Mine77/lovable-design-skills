---
name: lovable-design-system
description: Distinctive, production-grade frontend design with bold aesthetic direction, curated palette/typography/layout presets, and a structured design-direction flow. Use whenever building or refining UI (landing pages, product surfaces, marketing sites, dashboards) — especially when the brief is visual, broad, or "make it look good". Rejects generic AI aesthetics (Inter + purple gradients + centered cards). Stack assumption: React + Vite + TypeScript + Tailwind v3 + shadcn/ui, but the philosophy is stack-agnostic.
---

# Lovable Design System

This skill captures the full design context the Lovable agent operates under:
the **philosophy** (what good UI must avoid and aspire to), the **curated
visual asset library** (palettes, font pairs, layouts), and the **interaction
flows** for gathering design direction from a user (visual_choice questions,
rendered design directions).

It is a 1:1 transcription of the system-level guidance — no project-specific
content. Drop it into any agent (Codex, Cursor, Claude Code, Lovable, etc.)
and you get the same baseline taste and the same decision procedure.

---

## 1. Core philosophy — read every time

Before writing a single line of code, commit to a BOLD aesthetic direction.

- **Purpose**: What problem does this interface solve? Who uses it?
- **Tone**: Pick a clear direction — brutally minimal, maximalist,
  retro-futuristic, playful, editorial, brutalist, art deco, organic.
  Execute with conviction. Half-committed designs read as generic.
- **Differentiation**: What makes this unforgettable?

**NEVER use generic AI aesthetics.** The following are banned defaults:

- Overused fonts: Inter, Poppins, Roboto as the *only* font.
- Purple/violet gradients on white.
- Predictable layouts: centered hero, three feature cards, CTA.
- Identical-looking shadcn defaults across every project.

No two projects should look the same. If a screenshot of what you just built
could pass for any other AI-generated SaaS landing page, start over.

### Visual execution pillars

- **Typography**: Avoid defaults. Pair a *distinctive display font* with a
  *refined body font*. See `references/font-pairs.md`.
- **Color**: Commit to a cohesive palette. Bold accents outperform timid,
  evenly-distributed colors. See `references/palette-presets.md`.
- **Motion**: One well-timed hero animation creates more delight than
  scattered micro-interactions. Prefer Motion / Framer Motion.
- **Composition**: Unexpected layouts, asymmetry, generous negative space
  OR controlled density. See `references/layout-archetypes.md`.
- **Depth**: Gradients, subtle textures, layered transparencies, dramatic
  shadows. Match intensity to the chosen tone.

Match complexity to vision: maximalist designs need extensive effects;
minimalist designs need precision in spacing and typography.

### Design system implementation (Tailwind/CSS variables stack)

CRITICAL: Never write raw color classes (`text-white`, `bg-black`,
`text-[#ff0000]`) in components. Always go through semantic design tokens.

- Define rich tokens in `index.css` (or your global stylesheet) using HSL.
- Mirror them into `tailwind.config.ts` so Tailwind classes resolve.
- Use semantic names: `--background`, `--foreground`, `--primary`,
  `--primary-foreground`, `--secondary`, `--muted`, `--accent`, etc.
- Compose gradients and shadows as variables too:
  `--gradient-primary`, `--shadow-elegant`.
- Customize shadcn components via `cva` variants, not inline overrides.
- Ensure proper contrast in BOTH light and dark modes.

Example:

```css
:root {
  --primary: 270 91% 60%;            /* HSL components, no hsl() wrapper */
  --primary-glow: 270 91% 75%;
  --gradient-primary: linear-gradient(135deg, hsl(var(--primary)), hsl(var(--primary-glow)));
  --shadow-elegant: 0 10px 30px -10px hsl(var(--primary) / 0.3);
}
```

```tsx
const buttonVariants = cva("…", {
  variants: {
    variant: {
      premium: "bg-gradient-to-r from-primary to-primary-glow shadow-[var(--shadow-elegant)]",
    }
  }
})
```

Always check the CSS variable format before plugging into color functions.
Always use HSL components (no `hsl()` wrapper) inside `:root`.

---

## 2. The curated visual asset library

These three reference files contain the *exact* asset library the Lovable
agent picks from when asking the user for design direction. Treat them as
the canonical menu — don't invent new presets unless none fit.

- `references/palette-presets.md` — 26 named color palettes with hex values
  and a one-line domain hint each.
- `references/font-pairs.md` — 15 heading+body font pair presets with the
  vibe each communicates.
- `references/layout-archetypes.md` — 15 layout wireframe archetypes with
  the project types they suit.

---

## 3. Interaction flows

When the user's request is visual but the direction is unclear, do NOT just
build. Pull direction from them in a structured way.

- `references/ask-questions-flow.md` — when to ask design preference
  questions, how to structure the three visual_choice questions (palette,
  typography, layout), and the never-ask rules.
- `references/design-directions-flow.md` — the two-act "redesign ritual":
  pin the taste with visual_choice questions, then generate three rendered
  directions that vary in composition while keeping palette/type/layout
  locked.

---

## 4. SEO defaults (for any public page)

- `<title>` < 60 chars with primary keyword.
- `<meta description>` < 160 chars.
- Single `<h1>` per page.
- Semantic HTML (`<header>`, `<main>`, `<section>`, `<article>`, `<nav>`,
  `<footer>`).
- `alt` text on every image.
- JSON-LD structured data when applicable.
- Lazy-load below-the-fold images.
- Canonical tags.
- Responsive viewport meta.

---

## 5. Decision procedure — the loop

1. Read the user's request. Is it visual? Is the direction explicit?
2. If direction is given ("minimal black & white Swiss typography"), build.
3. If direction is missing AND the surface is design-open (landing, portfolio,
   marketing, brand site), ask the **three visual_choice questions**
   (palette / typography / layout) from `references/ask-questions-flow.md`.
4. Skip the questions for purely functional requests (todo app, calculator,
   CRUD admin), for obvious-default surfaces (dashboards, admin panels), or
   when the user has already given explicit direction.
5. For *refinement* of existing UI ("make it more elegant", "add wow"),
   use the design-directions flow in
   `references/design-directions-flow.md` instead of the questions flow.
6. Translate the user's picks into a detailed creative brief: specific
   fonts, hex colors, animation approaches, layout decisions. Infer
   whitespace, border radius, animation intensity, and visual weight from
   the palette + typography combo.
7. Build. Use design tokens. Avoid the banned defaults. Match complexity
   to the chosen tone.
8. After meaningful milestones, do a visual QA pass: screenshot, check
   contrast, check that the page does NOT look like generic AI output.

---

## 6. Do / Don't recap

**Do**

- Commit to one bold aesthetic direction and execute it fully.
- Use semantic design tokens for every color, shadow, gradient.
- Pair a distinctive display font with a refined body font.
- Pick presets from the curated palette / font / layout library.
- Ask the three visual_choice questions when direction is missing.
- Match implementation complexity to the chosen tone.

**Don't**

- Don't ship Inter + purple gradient + centered hero defaults.
- Don't write raw color classes in components.
- Don't use the same shadcn defaults you'd use on any other project.
- Don't ask for design direction on purely functional CRUD apps.
- Don't bundle questions — keep palette / type / layout as three separate
  visual choices.
- Don't generate three "directions" that only differ by accent color —
  they must differ in composition, density, hierarchy, motion.
