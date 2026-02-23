---
stepsCompleted: [step-01-init, step-02-discovery, step-02b-vision, step-02c-exec-summary, step-03-users, step-04-ux, step-05-features, step-06-nfr, step-07-integration, step-08-constraints, step-09-risks, step-10-future, step-11-complete]
inputDocuments:
  - "product-brief-conf-bmad-2026-02-20.md"
  - "https://buildmode.dev/blog/bmad-method-deep-dive/ (web reference)"
workflowType: 'prd'
documentCounts:
  briefs: 1
  research: 0
  brainstorming: 0
  projectDocs: 0
  projectContext: 0
classification:
  projectType: web_app
  domain: general
  complexity: low
  projectContext: greenfield
---

# Product Requirements Document - conf-bmad

**Author:** Clement.raussin
**Date:** 2026-02-20

---

## 1. Executive Summary

conf-bmad is a browser-based slide deck presentation for the DevOps Meetup Geneva. It delivers a 5-minute storytelling experience about the industrialization of vibe coding and the BMAD method, told through the authentic journey of a millennial developer who went from skeptic to advocate. The presentation runs locally on Mac via browser with keyboard navigation, smooth animations, and a dark/geeky minimalist design. A separate live demo follows the slides.

---

## 2. Product Vision

### Problem Statement

Vibe coding is exploding in popularity, but enterprise adoption faces a credibility wall. Scaling AI-assisted development to real projects exposes critical failures: context loss between sessions, architectural inconsistencies, mounting technical debt, zero documentation trail, and no meaningful collaboration workflow for DevOps teams.

### Vision Statement

Deliver a visually striking, animation-driven browser presentation that makes the case for structured AI development methodology through authentic storytelling — positioning BMAD humbly as one possible answer, not the definitive solution.

### Narrative Arc

1. **Skepticism** — "I'm a millennial dev. Vibe coding? That's unreliable garbage for enterprise."
2. **Experimentation** — "Then I tested it... and the potential is explosive."
3. **The Scale Problem** — "But at enterprise scale? Chaos. Context loss, architectural drift, tech debt, no collab."
4. **BMAD as a Response** — "BMAD brings determinism without killing the vibe: specialized agents, systematic planning, persistent context."
5. **DevOps Gains** — "Quality alignment, living docs for teams, AI pipelines, human orchestrating AI."
6. **Punchline** — "The book of vibe coding isn't written yet, but BMAD is the first critiquable — and brilliant — chapter."

---

## 3. Target Users

### Primary User: The Presenter (Clement)

- Millennial developer, DevOps background
- Runs slides locally on Mac via browser
- Classic keyboard controls (arrow keys, clicker compatible)
- Needs fluid navigation with beautiful minimalist animations
- Single-use scenario: launch URL → present → done

### Secondary Users: Meetup Audience

- DevOps Meetup Geneva attendees — devs, ops, SREs
- Passive consumers watching projected slides
- Need clear readability at projection distance
- Visual impact that reinforces geeky/dev-culture tone

---

## 4. User Experience

### User Flow

1. Open local URL in browser (e.g. `localhost:3000`)
2. Press F11 for fullscreen manually
3. Navigate slides with left/right arrow keys
4. Present for ~5 minutes (~10-15 slides)
5. End presentation, switch to live demo (separate)

### UX Principles

- **Storytelling-first**: The slide structure enforces the narrative arc — impossible to get lost
- **Minimalism**: Each slide has one idea, one visual, one animation purpose
- **Rhythm**: Animations pace the delivery — they're not decoration, they're timing
- **Readability**: Large text, high contrast, projection-optimized

---

## 5. Feature Requirements

### F-001: Slide Navigation

| Field | Value |
|-------|-------|
| Priority | P0 — Must Have |
| Description | Navigate between slides using keyboard arrow keys (left = previous, right = next) |
| Acceptance Criteria | Left/right arrow keys navigate slides; no other controls needed |

### F-002: Slide Transitions

| Field | Value |
|-------|-------|
| Priority | P0 — Must Have |
| Description | Smooth animated transitions between slides that reinforce narrative flow |
| Acceptance Criteria | Transitions are fluid, consistent, and distraction-free; each transition completes in <500ms |

### F-003: Element Animations

| Field | Value |
|-------|-------|
| Priority | P0 — Must Have |
| Description | Animated entry of text and visual elements within slides to pace storytelling |
| Acceptance Criteria | Elements animate in on slide entry; animations support the narrative rhythm; no jank or stutter |

### F-004: Dark/Geek Theme

| Field | Value |
|-------|-------|
| Priority | P0 — Must Have |
| Description | Dark theme with geeky/dev-culture aesthetic — monospace accents, terminal-inspired elements, clean typography |
| Acceptance Criteria | Consistent dark palette; dev-culture visual language; readable at projection distance; professional but playful |

### F-005: Slide Content — Full Narrative Arc

| Field | Value |
|-------|-------|
| Priority | P0 — Must Have |
| Description | Complete set of slides covering the 6-beat narrative arc defined in the vision |
| Acceptance Criteria | All 6 narrative beats are represented; each slide has a clear purpose; total count fits 5 minutes (~10-15 slides) |

### F-006: Responsive to Projection

| Field | Value |
|-------|-------|
| Priority | P1 — Should Have |
| Description | Layout and typography optimized for projector display at meetup venue |
| Acceptance Criteria | Text readable from back of room; no clipping or overflow; consistent rendering on projector resolution |

---

## 6. Non-Functional Requirements

### Performance

- Page load: < 2 seconds on localhost
- Animations: 60fps, no jank
- Zero network dependency after initial load (fully static)

### Browser Compatibility

- Chrome on macOS (primary and only required target)

### Accessibility

- High contrast dark theme (WCAG AA for text contrast)
- Large font sizes for projection readability

### Tech Constraints

- Runs locally on Mac — no server, no deployment, no backend
- Static front-end only (HTML/CSS/JS or framework-based SPA)
- Framework suggestion: Reveal.js, Slidev, or vanilla SPA — to be decided at architecture phase

---

## 7. Integration Requirements

None. This is a fully standalone, offline, static web application with no external dependencies, APIs, or services.

---

## 8. Constraints & Assumptions

### Constraints

- Must run locally on Mac/Chrome without network
- 5-minute presentation time (~10-15 slides)
- Single presenter, keyboard-only navigation
- One-shot usage for DevOps Meetup Geneva

### Assumptions

- Venue has a projector with HDMI connection
- Presenter uses Chrome on macOS
- Presenter is comfortable with F11 fullscreen and arrow key navigation
- No need to share slides online after the event

---

## 9. Risks & Mitigations

| Risk | Impact | Likelihood | Mitigation |
|------|--------|------------|------------|
| Animations lag on projector | Medium | Low | Test on external display before event; keep animations CSS-only for GPU acceleration |
| Too many slides for 5 min | Medium | Medium | Target 10-12 slides max; rehearse with timer |
| Font rendering differs on projector | Low | Medium | Use web-safe fonts or bundle fonts; test on external display |
| Browser crashes mid-presentation | High | Very Low | Have presentation open in 2 browser windows; know the last slide shown |

---

## 10. Future Considerations

N/A — This is a one-shot project for the DevOps Meetup Geneva. No roadmap, no iterations, no post-MVP features planned.

---

## 11. Success Metrics

- **Visual impact**: Polished animations and transitions that reinforce narrative rhythm
- **Design quality**: Minimalist, geeky aesthetic that a DevOps audience instantly respects
- **Storytelling enforcement**: Slide structure drives the narrative arc — the presenter can't get lost
- **Technical reliability**: Smooth 60fps animations on Mac/Chrome, zero crashes
- **Timing**: Full narrative fits comfortably in 5 minutes
