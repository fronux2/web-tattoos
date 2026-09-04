# Design System — Marco Ink

## Direction

**Personality:** Ink & Brass — a tattoo studio's own world (flash sheets, stencil paper, brass machine fittings), not a generic dark SaaS dashboard.
**Foundation:** Warm ink black, single brass accent.
**Depth:** Borders-only. Hairline `rgb(198 138 61 / 0.14)` for structure, `rgb(198 138 61 / 0.32)` for emphasis (buttons, active states). No shadows except the flash-tag's small paper-lift shadow.

## Tokens

### Colors (defined in `src/styles/global.css` `@theme`)
```
--color-ink: #14110d            /* page background */
--color-ink-surface: #1d1914    /* cards, panels */
--color-ink-elevated: #241d16   /* hover state */
--color-ink-inset: #191510      /* form inputs (darker = receives content) */
--color-brass: #c68a3d          /* primary accent */
--color-brass-bright: #dda254   /* hover/active accent */
--color-paper: #e7d9b8          /* flash-tag surface only */
--color-paper-ink: #1c1712      /* text on paper */
--color-oxblood: #8b3a2b        /* rare, unused so far — reserve for a genuine alert/error */
--color-text-primary: #f2ede3
--color-text-secondary: #b8ad9c
--color-text-muted: #7a7267
--color-hairline: rgb(198 138 61 / 0.14)
--color-hairline-strong: rgb(198 138 61 / 0.32)
```

### Typography
- Display (`font-display`): Fraunces — headings only (h1–h4), weight 500/600.
- Body (`font-body`): Inter — everything else, default on `<body>`.
- Utility (`font-mono`): IBM Plex Mono — eyebrows, nav labels, flash tags, process step numbers. Always uppercase + `tracking-[0.1em]`–`[0.16em]` at 11–12px.
- Loaded via Google Fonts `@import` at the top of `src/styles/global.css`.

### Radius
Small everywhere: `rounded-[2px]` on photos/cards, `rounded-[3px]` on buttons/inputs/nav pills. No large radii — this is a hairline system, not a soft one.

### Spacing
Section padding: `py-20` (home sections), `py-16` (about/contact/gallery hero). Section dividers: `border-t border-hairline`, no filler `bg-stone-900` bands.

## Patterns

### Flash tag (signature component — `src/components/FlashTag.astro`)
A rotated parchment tag (`bg-paper`, `text-paper-ink`, `rotate-3`, `font-mono text-[11px]`) pinned to the top-right corner of any tattoo photo, showing its style. Used in `Gallery.astro` and the home page's featured-works grid. Reuse this for any future photo grid instead of a gradient/caption overlay.

### Icon set (`src/components/Icon.astro`)
Single-stroke linework SVGs (`stroke-width="1.4"`, no fill) replacing emoji. Current names: `blackwork`, `floral`, `tradicional`, `realismo`, `needle`, `coverup`, `sparkle`, `chat`, `arrow`. Add new icons to the `PATHS` map in the same style — thin line, rounded caps, 24×24 viewBox — never introduce emoji as UI icons again.

### Buttons
- Primary: `bg-brass hover:bg-brass-bright text-paper-ink rounded-[3px]`, no pill shape.
- Secondary/outline: `border border-hairline-strong hover:bg-ink-elevated`.

### Form inputs (`contact.astro`)
`bg-ink-inset border border-hairline-strong rounded-[3px] focus:ring-1 focus:ring-brass focus:border-brass`. Inputs are inset (darker than surrounding surface), never lighter.

### Grouped tiles (specialties / services grids)
`gap-px bg-hairline` container with `bg-ink-surface` children — produces a 1px hairline grid without stacking individual borders. `hover:bg-ink-elevated` on each tile for the elevation step.

## Decisions

| Decision | Rationale | Date |
|----------|-----------|------|
| Kept dark ink + amber-family base | Already correct for a tattoo studio (autoclave/brass-machine world); the problem was generic execution, not the palette concept | 2026-09-04 |
| Replaced all emoji icons with linework SVGs | Emoji read as placeholder/unfinished; linework matches tattoo needle-line vocabulary | 2026-09-04 |
| Flash tag as signature element | A rotated parchment tag mimics a real flash-sheet price tag — the one element unique to this product's world | 2026-09-04 |
| Borders-only depth, no shadows | Dense, technical, hairline-structure fits a studio/portfolio better than soft SaaS shadows | 2026-09-04 |
| Fraunces for display type | Serif with an ink/letterpress quality reads as hand-set flash-sheet lettering, not a SaaS dashboard | 2026-09-04 |
