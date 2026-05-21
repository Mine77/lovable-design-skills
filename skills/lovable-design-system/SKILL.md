---
name: lovable-design-system
description: Distinctive, production-grade frontend design with bold aesthetic direction, curated palette/typography/layout presets, and a structured design-direction flow. Use whenever building or refining UI (landing pages, product surfaces, marketing sites, dashboards) — especially when the brief is visual, broad, or "make it look good". Rejects generic AI aesthetics (Inter + purple gradients + centered cards). Stack assumption: React + Vite + TypeScript + Tailwind v3 + shadcn/ui, but the philosophy is stack-agnostic.
---

# Lovable Design System

A 1:1 transcription of the design-related system context the Lovable agent
operates under, plus the meta-instructions needed to **execute** it the way
a tasteful designer would, not the way a lookup-table would.

---

## 0. How to read this skill (READ FIRST)

This skill is **a source library and a thinking method**, not a menu to
look up answers from. If you copy preset values verbatim into the project
without deriving anything, you have used this skill wrong.

Operating rules for the agent reading this skill:

1. **Presets are starting points, never endpoints.** The 26 palettes, 15
   font pairs, and 15 layouts are *raw material*. Always tune them to the
   project: nudge a hex by a few percent for better contrast, drop a font
   weight, narrow a sidebar by 40px, mute an accent. A preset copied
   verbatim is a smell.
2. **Compose, don't pick.** A finished style = palette × typography ×
   layout × inferred details (whitespace, radius, motion, density,
   hairline weight, emphasis treatment) × a one-word name. Five inputs,
   one synthesis. Picking only the first three and stopping = lookup-
   table behavior.
3. **You are authorized to create.** Custom palettes (4 hex values),
   custom font pairings, custom layout combinations are explicitly
   allowed when no preset fits. The library is a starting menu, not a
   fence.
4. **Reason out loud before building.** Run the 7-step *Derive, don't
   copy* micro-flow in §5 every time you need to invent a style.
   Skipping the reasoning chain produces generic results.
5. **Worked examples beat rules.** Before building anything, skim
   `references/worked-examples.md`. Match the shape of those derivations,
   not just the words of the rules.
6. **Match complexity to vision.** Maximalist tones need rich motion,
   layered depth, dense composition. Minimalist tones need precision in
   spacing, hairlines, type hierarchy. Mismatch = generic.

If at any point you find yourself writing `palette: "Paper & Ink"` and
moving on without naming a tone, deriving secondary details, or giving
the style a project-specific identity — stop and restart from §5.

---

## 1. Permissions (reverse-authorizations, high visibility)

These four lines are buried inside the verbatim source material below.
They are surfaced here because Codex and other instruction-following
agents tend to miss them and over-constrain themselves:

> **"You may also create custom palettes with 4 hex values when none of
> the presets fit."**

> **"Infer whitespace, border radius, animation intensity, and visual
> weight from the palette and typography choices. The brief should be
> Awwwards-level specific."**

> **"Match complexity to vision: maximalist designs need extensive
> effects; minimalist designs need precision in spacing and typography."**

> **"Users can also describe their own preference via the free-text
> input."** — i.e. the curated lists are not exhaustive constraints.

When in doubt between "copy the preset" and "derive from the preset",
**derive**.

---

## 2. Design philosophy (verbatim)

### Design Philosophy

Before coding, commit to a BOLD aesthetic direction:
- Purpose: What problem does this solve? Who uses it?
- Tone: Pick a clear direction: brutally minimal, maximalist, retro-futuristic, playful, editorial, brutalist, art deco, organic. Execute with conviction.
- Differentiation: What makes this unforgettable?

NEVER use generic AI aesthetics: overused fonts (Inter, Poppins), purple gradients on white, predictable layouts. No two projects should look the same.

### Visual Execution

- Typography: Avoid defaults. Pair a distinctive display font with a refined body font.
- Color: Commit to a cohesive palette. Bold accents outperform timid, evenly-distributed colors.
- Motion: Use framer-motion for animations. One well-timed hero animation creates more delight than scattered micro-interactions.
- Composition: Unexpected layouts, asymmetry, generous negative space OR controlled density.
- Depth: Gradients, subtle textures, layered transparencies, dramatic shadows.

Match complexity to vision: maximalist designs need extensive effects; minimalist designs need precision in spacing and typography.

### Design System Implementation

CRITICAL: Never write custom color classes (text-white, bg-black, etc.) in components. Always use semantic design tokens.

- Leverage index.css and tailwind.config.ts for consistent, reusable design tokens
- Customize shadcn components with proper variants
- Use semantic tokens: `--background`, `--foreground`, `--primary`, `--primary-foreground`, `--secondary`, `--muted`, `--accent`, etc.
- Add all new colors to tailwind.config.js for Tailwind class usage
- Ensure proper contrast in both light and dark modes

Example approach:
```css
/* index.css - Define rich tokens */
:root {
   --primary: [hsl values];
   --gradient-primary: linear-gradient(135deg, hsl(var(--primary)), hsl(var(--primary-glow)));
   --shadow-elegant: 0 10px 30px -10px hsl(var(--primary) / 0.3);
}
```

```tsx
// Create component variants using design system
const buttonVariants = cva("...", {
  variants: {
    variant: {
      premium: "bg-gradient-to-r from-primary to-primary-glow...",
    }
  }
})
```

IMPORTANT: Check CSS variable format before using in color functions. Always use HSL in index.css and tailwind.config.ts.

### Critical design instructions

- Use tailwind semantic tokens from index.css and tailwind.config.ts files when possible. DO NOT use colors directly in components. Everything must be themed according to the design system. All colors MUST be HSL.

---

## 3. SEO defaults (verbatim)

Title <60 chars with keyword; meta desc <160 chars. Single H1. Semantic HTML. Alt text on images. JSON-LD when applicable. Lazy loading. Canonical tags. Responsive viewport.

---

## 4. The curated source library

Three reference files. Treat them as raw material, not a menu (see §0):

- `references/palette-presets.md` — 26 named color palettes with hex
  values and a one-line domain hint each.
- `references/font-pairs.md` — 15 heading+body font pair presets with
  preset ids and the vibe each communicates.
- `references/layout-archetypes.md` — 15 layout archetypes with the exact
  enum strings and the project types they suit.

Two flow files:

- `references/ask-questions-flow.md` — when and how to ask the user the
  three visual_choice questions (palette / typography / layout); the
  visual_choice question schema; post-answer brief + `@fontsource` font
  loading rules. Verbatim transcription.
- `references/design-directions-flow.md` — when to generate three
  rendered design directions for refining existing UI; the screenshot-
  context contract; the two-act "redesign ritual". Verbatim transcription.

One execution file (read before every new style):

- `references/worked-examples.md` — four end-to-end reasoning chains
  (slides editor, travel blog, law firm site, fitness app) that show the
  *Derive, don't copy* micro-flow in action. **Mimic the shape of these
  chains, not just the rules in §2.**

---

## 5. The "Derive, don't copy" micro-flow

Run this **every time** you need to invent or refine a style. Each step
should produce a written sentence, not a silent guess.

1. **Domain & user** — what is this product, who uses it, what is the
   primary emotional register they should feel within 2 seconds of seeing
   the screen? (e.g. "Slides editor for designers — should feel like a
   focused editorial workspace, not a Notion-clone toy.")
2. **Tone** — pick ONE from the §2 tone list (or coin one), and explain
   in one line why the alternatives were rejected. (e.g. "editorial +
   brutally minimal; rejected playful because production tool, rejected
   maximalist because canvas content must dominate.")
3. **Palette** — scan `palette-presets.md`, pick the preset whose
   description sentence matches the tone, and explicitly note what you'll
   tune. Custom palette if nothing fits. (e.g. "Paper & Ink — match.
   Lift `#f5f3ee` by ~1% for canvas, deepen `#0d0d0d` accent only on
   active states.")
4. **Typography** — scan `font-pairs.md`, pick the pair whose vibe
   matches, and note the weights / italic usage / where the display font
   appears vs. body. (e.g. "instrument-serif-work-sans — serif italic
   only on one accent word per heading, body 400/500.")
5. **Layout** — scan `layout-archetypes.md`, pick the archetype(s),
   note any dimensional tuning. (e.g. "sidebar (240px, not the doc-
   suggested 280px) + dashboard for editor canvas.")
6. **Infer secondary details** — from palette × typography, derive:
   whitespace density, border radius, hairline weight, shadow depth,
   motion intensity, control height, emphasis treatment. Each should be
   one sentence. (e.g. "hairline 1px `border/40`, radius 6px, no shadow
   except focus ring, motion reserved to 150ms fades on hover, h-9
   controls.")
7. **Name it** — give the synthesized style a short project-specific
   name (2 words max). The name is for internal reference and to force
   commitment. (e.g. "Minimal Mono", "Marble Editorial", "Quiet Brass".)

If any step is skipped or filled with a preset's verbatim value with no
tuning, you have failed the micro-flow. Restart.

---

## 6. Decision loop (when to do what)

1. Read the user's request. Is it visual? Is the direction explicit?
2. If direction is given ("minimal black & white Swiss typography"), run
   §5 and build.
3. If direction is missing AND the surface is design-open (landing,
   portfolio, marketing, brand site), run the **three visual_choice
   questions** from `references/ask-questions-flow.md`. After the user
   answers, run §5 with their picks as seeds, then build.
4. Skip the questions for purely functional requests (todo app,
   calculator, CRUD admin) or obvious-default surfaces (dashboards,
   admin panels). But still run §5 silently — never inherit "default
   shadcn" as the answer.
5. For *refinement* of existing UI ("make it more elegant", "add wow"),
   use the design-directions flow in
   `references/design-directions-flow.md` instead of the questions flow.
6. Build. Use semantic design tokens (HSL, no `hsl()` wrapper in
   `:root`). Avoid the banned defaults from §2. Match complexity to the
   chosen tone.
7. Visual QA after meaningful milestones: screenshot, check contrast,
   confirm the page does NOT look like generic AI output. If it does,
   restart from §5 step 2 (tone) — the failure is upstream.

---

## 7. Do / Don't recap

**Do**

- Run the §5 micro-flow every time. Write the 7 sentences down.
- Tune presets — nudge hex values, weights, dimensions to fit.
- Compose: palette × type × layout × inferred details × name.
- Use semantic design tokens (HSL) for every color, shadow, gradient.
- Mimic the shape of `references/worked-examples.md`.
- Match implementation complexity to the chosen tone.

**Don't**

- Don't copy a preset's 4 hex values into `:root` unchanged and move on.
- Don't ship Inter + purple gradient + centered hero defaults.
- Don't write raw color classes (`text-white`, `bg-[#ff0000]`) in
  components.
- Don't use the same shadcn defaults you'd use on any other project.
- Don't ask for design direction on purely functional CRUD apps — but
  still run §5 silently.
- Don't bundle a fourth "what vibe?" question — palette already encodes
  vibe. At most one functional clarifier alongside the three visual ones.
- Don't generate three "directions" that only differ by accent color —
  they must differ in composition, density, hierarchy, motion.
- Don't load fonts via Google Fonts CDN `<link>`, CSS `@import`, or by
  editing `index.html`. Use `@fontsource/*` packages — see
  `references/ask-questions-flow.md` post-answer section.
- Don't skip naming the style. A nameless style is an un-committed style.
