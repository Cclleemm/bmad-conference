# STORY-004: Slide Content, Design & Animations

**Priority:** P0 — Must Have
**Story Points:** 8
**Status:** Not Started
**Depends on:** STORY-002, STORY-003

---

## User Story

As the presenter,
I want each slide to have bespoke content, layout, and animations,
So that the presentation is visually striking and the animations pace the storytelling.

---

## Scope

**In scope:**
- Final content per slide (provided by user)
- Bespoke layout per slide (different layouts slide-by-slide)
- Custom CSS animations per slide (@keyframes in animations.css)
- Fragment reveals for text pacing
- Auto-Animate between slides where it creates cinematic effect
- Per-slide data-transition choices
- Visual elements (code snippets, terminal aesthetics, icons if needed)

**Out of scope:**
- Design system changes (STORY-002, should be stable)
- Slide structure changes (STORY-003, order is set)

---

## Approach

This is the creative core of the project. Work iteratively slide by slide:

1. User provides content for a slide (or batch of slides)
2. Design bespoke layout for that slide
3. Create custom animations in animations.css
4. Apply fragments for text reveal pacing
5. Configure transitions to/from adjacent slides
6. User reviews and iterates

---

## Acceptance Criteria

- [ ] Every slide has final content (no placeholders)
- [ ] Every slide has a unique, bespoke layout
- [ ] Animations pace the narrative — elements animate in to time delivery
- [ ] All animations use GPU-only properties (transform, opacity)
- [ ] All animations run at 60fps (no jank)
- [ ] Transitions between slides are smooth and intentional
- [ ] Auto-Animate used where it creates cinematic cross-slide effects
- [ ] Fragments used for sequential text reveals
- [ ] Dev-culture visual language present (monospace, terminal accents, code aesthetics)
- [ ] Total slide count fits comfortably in 5 minutes (~25s per slide average)

---

## Technical Notes

### Animation Rules (from Architecture)

- Only `transform` and `opacity` in @keyframes
- `will-change: transform, opacity` on animated elements
- Durations: 300ms–800ms
- Easing: `cubic-bezier()` or named easings, never `linear`
- All CSS, no JS animations

### Animation Types to Use

- `.anim-fade-up` — element fades in + translates up
- `.anim-typewriter` — text appears character by character (CSS only)
- `.anim-scale-in` — element scales from 0 to 1
- `.anim-stagger` — elements appear sequentially with delay
- Custom per-slide effects as needed

### Per-Slide CSS Pattern

```css
/* In animations.css */
.slide-skepticism .slide-content h2 {
  animation: fade-up var(--duration-normal) ease-out;
}

@keyframes fade-up {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}
```

---

## Definition of Done

- [ ] All slides have final content and bespoke design
- [ ] All animations are smooth (60fps)
- [ ] Narrative pacing feels natural — animations guide delivery
- [ ] Visual consistency with theme (uses custom properties)
- [ ] Presenter (Clement) approves the final result
