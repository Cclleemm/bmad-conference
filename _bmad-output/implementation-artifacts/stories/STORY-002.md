# STORY-002: Design System (theme.css)

**Priority:** P0 — Must Have
**Story Points:** 3
**Status:** Not Started
**Depends on:** STORY-001

---

## User Story

As the presenter,
I want a dark/geeky design system with dev-culture aesthetic,
So that slides look professional and resonate with a DevOps audience.

---

## Scope

**In scope:**
- CSS custom properties for colors, fonts, spacing, animation durations
- Dark palette calibrated for projector display (higher contrast than screen)
- Typography scale (monospace + sans-serif, projection-readable sizes)
- Base slide layout styles (.slide-content padding, centering)
- Override Reveal.js default theme

**Out of scope:**
- Per-slide bespoke layouts (STORY-004)
- Animation @keyframes (STORY-004)

---

## Acceptance Criteria

- [ ] Dark background with high-contrast text (WCAG AA minimum)
- [ ] Monospace font loaded and applied to code/accent elements
- [ ] Sans-serif font for body text, readable at projection distance
- [ ] All colors use CSS custom properties (--color-*)
- [ ] All fonts use CSS custom properties (--font-*)
- [ ] All spacing uses CSS custom properties (--spacing-*)
- [ ] Animation duration variables defined (--duration-fast/normal/slow)
- [ ] .slide-content base styles applied (padding, max-width, centering)
- [ ] Reveal.js default theme fully overridden (no default styles leaking)
- [ ] Test on a few slides looks consistent and polished

---

## Technical Notes

### Custom Properties to Define

```css
:root {
  /* Colors */
  --color-bg: /* deep dark */;
  --color-text: /* high contrast light */;
  --color-primary: /* accent color */;
  --color-accent: /* secondary accent */;
  --color-muted: /* subtle text */;
  --color-code-bg: /* code block background */;

  /* Fonts */
  --font-mono: /* monospace family */;
  --font-sans: /* sans-serif family */;
  --font-size-xl: /* titles, projection-readable */;
  --font-size-lg: /* subtitles */;
  --font-size-md: /* body */;
  --font-size-sm: /* small text */;

  /* Spacing */
  --spacing-sm: ;
  --spacing-md: ;
  --spacing-lg: ;
  --spacing-xl: ;

  /* Animation */
  --duration-fast: 300ms;
  --duration-normal: 500ms;
  --duration-slow: 800ms;
}
```

### Font Strategy
- Bundle fonts in assets/fonts/ (no network dependency)
- Use @font-face declarations
- Monospace: for code, terminal aesthetics, accent text
- Sans-serif: for readable body text

### Projection Considerations
- Font sizes larger than typical screen (min 1.5rem body, 3rem+ titles)
- Contrast ratio higher than WCAG AA (projectors lose contrast)
- Avoid thin font weights (< 400)
- Test with reduced brightness to simulate projector

---

## Definition of Done

- [ ] All custom properties defined and used consistently
- [ ] Fonts bundled locally and loading
- [ ] Slides readable and visually polished in browser
- [ ] No Reveal.js default styles visible
