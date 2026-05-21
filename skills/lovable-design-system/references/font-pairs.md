# Curated typography pair presets

The full font-pair library available when asking the user to choose a
typographic direction. Each preset names a **heading font** and a **body
font**, plus the kind of project it suits.

When rendering as a visual choice, show the *heading font name set in the
heading font itself* and a *body sample set in the body font*, so the user
can compare the two type voices side by side. Always pair a distinctive
display font with a more neutral body font — never two display fonts and
never two body fonts.

All fonts below are available on Google Fonts.

---

| Preset id                          | Heading           | Body              | Suits                                    |
| ---------------------------------- | ----------------- | ----------------- | ---------------------------------------- |
| `space-grotesk-dm-sans`            | Space Grotesk     | DM Sans           | Modern tech, dev tools                   |
| `syne-plus-jakarta`                | Syne              | Plus Jakarta Sans | Creative startups, agencies              |
| `outfit-figtree`                   | Outfit            | Figtree           | Lifestyle brands, DTC                    |
| `sora-manrope`                     | Sora              | Manrope           | Digital tools, SaaS                      |
| `urbanist-epilogue`                | Urbanist          | Epilogue          | Architecture, real estate                |
| `instrument-serif-work-sans`       | Instrument Serif  | Work Sans         | Modern magazines, editorial              |
| `dm-serif-display-fira-sans`       | DM Serif Display  | Fira Sans         | Brand storytelling, hero campaigns       |
| `cormorant-karla`                  | Cormorant Garamond| Karla             | Luxury fashion, hospitality              |
| `libre-baskerville-ibm-plex`       | Libre Baskerville | IBM Plex Sans     | Law, finance, serious institutions       |
| `lora-nunito-sans`                 | Lora              | Nunito Sans       | Blogs, publishing                        |
| `bebas-neue-barlow`                | Bebas Neue        | Barlow            | Sports, events, bold campaigns           |
| `archivo-black-hind`               | Archivo Black     | Hind              | News, activism, statement                |
| `abril-fatface-cabin`              | Abril Fatface     | Cabin             | Creative portfolios                      |
| `jetbrains-mono-work-sans`         | JetBrains Mono    | Work Sans         | Tech docs, API references                |
| `space-mono-rubik`                 | Space Mono        | Rubik             | Indie tech, gaming                       |

---

## Choosing rules

- Pick **three or four** pairs per question that match the project type.
  Don't dilute the choice with pairs that obviously don't fit (e.g. don't
  offer `bebas-neue-barlow` for a luxury skincare brand).
- The user can always describe their own preference via a free-text
  "Other" option; the curated list is a starting point, not a cage.
- Once the user picks a pair, infer the *whole typographic system* from
  it: heading weights (usually 500–700), body weight (400 plus 500 for
  emphasis), line-height (1.1–1.2 for display, 1.5–1.65 for body),
  letter-spacing (slightly tight for display, neutral for body), and a
  monospace fallback for code/kbd usage.
- For Tailwind projects, wire the chosen fonts via `tailwind.config.ts`:

  ```ts
  fontFamily: {
    sans: ["DM Sans", ...defaultTheme.fontFamily.sans],
    display: ["Space Grotesk", ...defaultTheme.fontFamily.sans],
    serif: [...defaultTheme.fontFamily.serif],
    mono: [...defaultTheme.fontFamily.mono],
  }
  ```

  Then `font-display` for headings, `font-sans` for body, and reserve
  `font-serif italic` for the occasional accent word inside a heading.
