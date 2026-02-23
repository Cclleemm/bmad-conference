# STORY-003: Slide Structure & Reveal.js Config

**Priority:** P0 — Must Have
**Story Points:** 2
**Status:** Not Started
**Depends on:** STORY-001, STORY-002

---

## User Story

As the presenter,
I want all ~12 slides structured with the narrative arc in index.html,
So that I have the complete skeleton ready for content and design.

---

## Scope

**In scope:**
- Create all ~12 `<section>` elements following narrative arc
- Each section with class `.slide-{name}` and `.slide-content` wrapper
- Reveal.js configuration tuned for presentation use
- Placeholder content per slide (title + brief note of purpose)

**Out of scope:**
- Final slide content and bespoke layouts (STORY-004)
- Animations (STORY-004)

---

## Narrative Arc (from PRD)

1. **Title slide** — conf-bmad, presenter intro
2. **Skepticism** — "Vibe coding? Unreliable garbage for enterprise."
3. **Experimentation** — "Then I tested it... explosive potential."
4. **The Scale Problem** — "At enterprise scale? Chaos."
5. **Pain points detail** — Context loss, architectural drift, tech debt, no collab
6. **BMAD as a Response** — Determinism without killing the vibe
7. **BMAD Key Features** — Specialized agents, systematic planning, persistent context
8. **DevOps Gains** — Quality alignment, living docs, AI pipelines
9. **Human Orchestrating AI** — The new developer role
10. **Punchline** — "The book isn't written yet, but BMAD is the first critiquable — and brilliant — chapter"
11. **Live Demo Teaser** — Transition to live demo
12. **Thank You / Contact** — Closing slide

---

## Acceptance Criteria

- [ ] All ~12 sections present in index.html
- [ ] Each section has `class="slide-{name}"` per naming convention
- [ ] Each section has `.slide-content` wrapper div
- [ ] Placeholder content visible on each slide (title at minimum)
- [ ] Arrow key navigation works through all slides
- [ ] Reveal.js config: keyboard enabled, controls hidden, progress bar hidden, hash disabled
- [ ] `data-transition` attribute set per slide (can be adjusted later)

---

## Technical Notes

### Reveal.js Config

```javascript
Reveal.initialize({
  hash: false,
  controls: false,
  progress: false,
  keyboard: true,
  transition: 'slide',
  transitionSpeed: 'default',
  width: 1920,
  height: 1080,
  margin: 0,
  center: true
});
```

### Slide Skeleton Pattern

```html
<section class="slide-skepticism" data-transition="slide">
  <div class="slide-content">
    <h2>Placeholder: Skepticism</h2>
    <p>Vibe coding? That's unreliable garbage for enterprise.</p>
  </div>
</section>
```

---

## Definition of Done

- [ ] All slides present and navigable
- [ ] Naming convention respected
- [ ] Reveal.js configured for presentation mode
- [ ] Skeleton ready for bespoke content/design in STORY-004
