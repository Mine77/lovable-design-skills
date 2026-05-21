# Worked examples — four end-to-end style derivations

These four examples show the §5 *Derive, don't copy* micro-flow in
action. **Mimic the shape of these derivations** when inventing a new
style. The rules in `SKILL.md` tell you *what*; these examples show
*how to think*.

Each example follows the same 7-step structure:
**Domain → Tone → Palette → Typography → Layout → Inferred details → Name.**

---

## Example 1 — Slides editor for designers (the "Minimal Mono" derivation)

1. **Domain & user.** Web-based slides editor. Users = designers and PMs
   who already use Figma/Linear daily. Primary emotional register:
   *"focused editorial workspace"*, not *"playful productivity toy"*. The
   canvas content (slides) must dominate; chrome must recede.
2. **Tone.** Editorial + brutally minimal. Rejected *playful* (toy),
   *maximalist* (would compete with canvas), *retro-futuristic*
   (off-brand for serious work).
3. **Palette.** `Paper & Ink` (`#f5f3ee` / `#e8e4dd` / `#2d2d2d` /
   `#0d0d0d`) — description "Clean editorial, Swiss typography ready"
   matches tone exactly. Tuning: lift the canvas `#f5f3ee` by ~1% for
   the editor stage so slides sit on a slightly warmer surface than
   chrome. Keep `#0d0d0d` as ink, reserved for active/pressed states
   only; use `#2d2d2d` for primary text to soften contrast.
4. **Typography.** `instrument-serif-work-sans`. Body 400/500 Work Sans;
   headings 500–600 Work Sans; **Instrument Serif italic reserved for
   exactly one accent word per page-level heading** ("Recent *decks*").
   No serif in body. This single italic move is the signature.
5. **Layout.** `sidebar` (thumbnails) + `dashboard` (header + canvas +
   right rail). Sidebar narrowed to 240px (not the doc-suggested 280px)
   because thumbnails don't need width. Right rail collapsible.
6. **Inferred details.**
   - Whitespace: tight chrome, generous canvas margin.
   - Radius: 6px (geometric sans + editorial → small, not zero).
   - Hairline: 1px `border/40` everywhere; no shadows except focus ring.
   - Motion: 150ms fades on hover only; no spring, no parallax.
   - Controls: `h-9` uniform; ghost-by-default, solid only for primary.
   - Emphasis: serif italic + opacity scale (`/60`, `/40`, `/20`) does
     the work that color usually does in saturated palettes.
7. **Name.** *Minimal Mono*.

---

## Example 2 — Travel blog for a solo writer

1. **Domain & user.** Long-form travel writing, photography-heavy.
   Reader = someone discovering the site from a referral. Should feel
   *"like opening a curated magazine in a quiet café"*.
2. **Tone.** Editorial + organic. Rejected *brutally minimal* (would
   suffocate the photos), *playful* (cheapens the writing), *brutalist*
   (off-brand for travel intimacy).
3. **Palette.** `Warm Sand` (`#faf8f5` / `#f0ebe3` / `#c9b99a` /
   `#8b7355`) — welcoming, approachable. Tuning: introduce a 5th value
   for ink (`#2a2520` deep warm brown, not pure black) so type doesn't
   feel cold against the warm neutrals.
4. **Typography.** `lora-nunito-sans`. Lora 500/600 for article titles,
   Nunito Sans 400/600 for body. Pull-quotes set in Lora italic at
   1.5× body size with left hairline rule.
5. **Layout.** `magazine` for the index (one featured story hero + grid
   below) + `single-column` for article pages (max-width ~68ch).
6. **Inferred details.**
   - Whitespace: generous; article body has 1.7 line-height.
   - Radius: 4px on images, 0px on text containers.
   - Hairline: warm `#c9b99a/30` rules between sections.
   - Motion: reveal-on-scroll fades for images, nothing else.
   - Controls: text links underlined on hover, never bare blue.
   - Emphasis: italic + small caps for bylines; drop caps on first ¶.
7. **Name.** *Quiet Café*.

---

## Example 3 — Law firm marketing site

1. **Domain & user.** Mid-size corporate law firm. Visitor = potential
   client (executive) evaluating in 30 seconds whether to inquire.
   Register: *"institutional, considered, expensive"*.
2. **Tone.** Authoritative + restrained editorial. Rejected
   *brutalist*, *playful*, *retro-futuristic* — all off-brand.
3. **Palette.** `Navy Trust` (`#0f1b3d` / `#1e3a5f` / `#3b6fa0` /
   `#e8edf3`) — finance/legal explicit match. Tuning: replace the
   lightest `#e8edf3` with `#f8f9fb` for surface; add `#c9a84c` muted
   gold (borrowed from `Noir & Gold`) as the single accent for case
   numbers and CTAs — Navy alone is too monochrome for a 6-section
   landing page.
4. **Typography.** `libre-baskerville-ibm-plex`. Baskerville for
   partner names, practice areas, headlines; IBM Plex Sans 400/500 for
   body; **IBM Plex Mono for case numbers and dates** (custom move
   beyond the preset).
5. **Layout.** `full-width-sections` (alternating navy ↔ off-white
   bands) on the landing, `asymmetric` 60/40 on practice-area pages
   (description left, contact card right).
6. **Inferred details.**
   - Whitespace: very generous; section padding 120px desktop.
   - Radius: 0px everywhere. Hard edges = institutional.
   - Hairline: 1px gold `#c9a84c/60` under section headings only.
   - Motion: none on page load. Hover = 200ms color shift on links.
   - Controls: solid navy buttons with gold hover, never gradient.
   - Emphasis: small caps on partner titles; serif for proper nouns.
7. **Name.** *Marble Brief*.

---

## Example 4 — Fitness tracking iOS-style web app

1. **Domain & user.** Workout tracker, mobile-first. User = early-
   morning gym-goer logging sets between exercises. Register:
   *"energized, immediate, no-friction"*.
2. **Tone.** Maximalist energy + playful. Rejected *editorial*
   (slows interaction), *brutally minimal* (too cold for fitness),
   *organic* (not the brand vibe target users want).
3. **Palette.** `Neon Mint` (`#0d1b2a` / `#1b4332` / `#2dd4a8` /
   `#73ffb8`) — startup energy match. Tuning: add `#ff4d6d` magenta
   as a *secondary* accent for PRs and streaks (one preset accent
   can't carry both "active" and "celebrate"). Background gradient
   `#0d1b2a → #142d3d` on top-half for depth.
4. **Typography.** `sora-manrope`. Sora 600/700 for numbers (weight,
   reps, time) — these are the heroes. Manrope 400/500 for labels.
   Tabular numerals on for all timer/counter displays.
5. **Layout.** `bento-grid` for the dashboard (today's workout,
   streak, last PR, suggested next), `feed` for history.
6. **Inferred details.**
   - Whitespace: dense but rhythmic; 8px grid.
   - Radius: 16px on cards, 12px on buttons — rounded = energetic.
   - Shadow: `0 4px 20px -4px hsl(168 76% 42% / 0.3)` on primary CTA.
   - Motion: spring `stiffness: 200, damping: 18` on every tap;
     confetti on PR; count-up animation on stat numbers.
   - Controls: 48px tap targets minimum; primary = mint gradient.
   - Emphasis: number scale dominates — 56px hero numbers vs 14px
     labels.
7. **Name.** *Voltage Mint*.

---

## How to use these

When you start a new project:

1. Find the example closest to your domain.
2. Don't copy its outputs — copy its **reasoning shape**: which lines it
   wrote at each step, what alternatives it explicitly rejected, where
   it tuned a preset vs. accepted it, what custom moves it added beyond
   the preset (italic-only-on-one-word, gold-borrowed-from-other-palette,
   mono-for-case-numbers, magenta-for-celebration).
3. Produce your own 7 lines. Commit. Build.

If your derivation reads less specific than any of these four examples,
you are still in lookup-table mode. Restart §5 step 1.
