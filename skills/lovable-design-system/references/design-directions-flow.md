# Design directions — the redesign ritual

For **refining existing UI** ("make this prettier", "add wow", "make it
more elegant", "fix the hero"), do not just edit. Run the two-act
redesign ritual: pin the user's taste, then generate three rendered
directions for them to pick.

This is distinct from the ask-questions flow in `ask-questions-flow.md`:
- Ask-questions = fresh build, no UI yet, gather taste.
- Design directions = existing UI on screen, the user wants it better.

---

## When to generate design directions

- The user explicitly asks for design directions, options, alternatives,
  concepts, variations.
- The user asks to fix / improve / make better / make more elegant / more
  beautiful / more impressive, add sparkle, or add wow to existing UI.
- The request is visual and qualitative, and screenshot-bounded options
  would clarify the direction.

## When to SKIP and just edit

- The user gave an exact deterministic edit
  ("make the button #111", "increase padding to 16px",
  "change the label to Save").
- The user specified a required library / runtime feature outside the
  Tailwind + Motion preview envelope (Three.js, Mapbox, tldraw,
  real-time, complex gestures, D3/Recharts implementation details,
  AnimatePresence / layoutId semantics, drag/whileHover/whileTap
  semantics). These cannot be faithfully rendered as static directions.
- The user wants new functionality, not visual refinement.
- The request is functionality, backend, data, auth, integration, or a
  bug fix with no visual styling question.
- You cannot identify the target from the message, attachments, or a
  capturable screenshot.

---

## Act 1 — Anchor on what's there, then pin the taste

1. **Capture the current preview** of the exact element/section being
   redesigned. The directions step expects a real visual reference, not
   prose. If you only have prose, the call will refuse with a missing-
   context warning — recapture or crop tighter and retry.
2. **Pin taste** with one round of three visual_choice questions:
   palette, typography, layout — same recipe as
   `ask-questions-flow.md`. Each rendered visually (swatches, real type
   samples, wireframe sketches) so the answer is a concrete preset.
3. Skip the fourth "what vibe?" question. The three picks encode the
   mood.

## Act 2 — Generate three directions

Generate **three rendered design directions** with these locks:

- **Locked across all three**: the palette, the type pair, the layout
  the user just picked. Hard constraints. No drift.
- **Varied across the three**: composition, density, hierarchy, emphasis,
  motion register.

The captured screenshot must ride along as a real image input on the
generation call. Do NOT describe the screenshot in a free-text context
field instead — that path is rejected.

Give each direction its own point of view:
- A sensory metaphor ("liquid metal", "paper architecture", "neon
  whisper").
- An energy register (calm / kinetic / monumental).
- Structural moves that make the variants meaningfully distinct (asymmetric
  vs. centered, dense vs. airy, image-led vs. type-led).

Three flavors of the same locked taste — NOT three versions of the same
composition with a swapped accent color.

---

## Show the picks

Show the three rendered directions back to the user as real previews,
side by side, each one clickable / fully rendered. One concise question:

> Which direction should I build?

Nothing bundled in, no clarifying disambiguation, no second question
hidden inside. Carry the prototype identifiers (`prototypeRef` +
`sourceToolCallEventID`) through from the directions step so the picker
resolves to the right rendered output.

## After the user picks

Implement the chosen direction with composition matched exactly:

- Same hero alignment.
- Same component counts.
- Same sectioning.
- Same density.
- Copy the chosen direction's design tokens verbatim into the project's
  CSS — don't re-derive values.
- Persist the chosen palette, typography, layout, motion register, and
  component treatment into `styleguide.md` when possible. Follow
  `styleguide-persistence.md`.

The prototype is structural reference, not just a mood board. If the user
later asks to see the same pending directions again, present them again
WITHOUT regenerating. If they want fresh ones, restart from "Pin the
taste".

---

## Scope discipline

Screenshot scope bounds the output:

- Logo stays logo.
- Headline stays headline.
- Button stays button.
- Card stays one card.
- Section stays section.

Do not ask for, or build, page chrome around a smaller element. If the
screenshot misses the target, recapture before calling.
