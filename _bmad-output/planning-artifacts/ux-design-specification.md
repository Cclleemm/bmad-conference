---
stepsCompleted: [1, 2, 3]
inputDocuments:
  - "product-brief-conf-bmad-2026-02-20.md"
  - "prd.md"
workflowType: 'ux-design'
date: 2026-02-20
author: Clement.raussin
---

# UX Design Specification conf-bmad

**Author:** Clement.raussin
**Date:** 2026-02-20

---

## Executive Summary

### Project Vision

conf-bmad is a browser-based slide deck for the DevOps Meetup Geneva — a 5-minute storytelling experience about the industrialization of vibe coding through the BMAD method. Told through the authentic journey of a millennial developer who went from skeptic to advocate, the presentation uses a dark/geeky minimalist aesthetic with smooth animations that serve as the narrative's pacing mechanism. The web-native delivery format reinforces the message: this is a web app presenting about AI-assisted web development.

### Target Users

**Primary — The Presenter (Clement):**
A millennial developer with DevOps background presenting at DevOps Meetup Geneva. Runs the slide deck locally on Mac via Chrome. Needs classic keyboard navigation (arrow keys), fluid transitions, and a design that enforces the narrative arc so no script memorization is needed. Single-use scenario: open URL → F11 → present → done.

**Secondary — Meetup Audience:**
DevOps Meetup Geneva attendees — developers, ops engineers, SREs. Passive consumers watching projected slides. They need clear readability at projection distance and visual impact that speaks their language (dev-culture aesthetics). They should leave remembering the narrative arc and BMAD's value proposition.

### Key Design Challenges

- **Animation as narrative pacing**: Animations must serve as the storytelling metronome — guiding delivery rhythm without constraining the presenter. The timing balance between "too slow" and "too fast" is critical for a 25-second-per-slide cadence.
- **Projected dark theme readability**: Dark themes lose contrast on projectors in partially lit rooms. Contrast ratios must be calibrated for projection, not desktop viewing. Font sizes and weight must compensate for projection distance.
- **Information density constraint**: At ~25 seconds per slide, each slide must communicate one idea at a glance. The design must structurally enforce "one idea, one visual, one purpose" to prevent content overload.

### Design Opportunities

- **Medium-as-message synergy**: A web-native presentation about AI-assisted web development — the delivery format itself is a proof of concept. Design can subtly incorporate code-like elements, terminal aesthetics, and AI-evocative visuals.
- **Cinematic storytelling**: The web format enables transitions and progressive element reveals that create narrative tension — going beyond what traditional slide tools offer, creating "Apple keynote meets terminal" moments.
- **Dev-culture visual identity**: A 100% technical audience allows full commitment to developer visual language — monospace fonts, syntax highlighting accents, blinking cursors, terminal-inspired layouts — no need to dilute for non-technical comprehension.

## Core User Experience

### Defining Experience

The core experience of conf-bmad is a single, continuous gesture: pressing the right arrow key to advance through a narrative. The presenter enters a flow state where the slide transitions, element animations, and visual rhythm become an extension of their speech. There is no UI to manage, no menus to navigate, no decisions to make during the presentation — only forward momentum through a story.

The entire product value is concentrated in the quality of this single interaction: keypress → smooth transition → new slide with animated elements → narrative beat delivered.

### Platform Strategy

- **Platform**: Browser-based (Chrome on macOS), running locally via localhost
- **Input**: Keyboard-only (left/right arrow keys); clicker-compatible (clickers emit arrow key events)
- **Display**: Optimized for 16:9 projection via external display/projector
- **Architecture**: Fully static — no server, no network dependency, no build step required at presentation time
- **Fullscreen**: Manual F11 by presenter; no auto-fullscreen logic needed

### Effortless Interactions

- **Navigation**: Arrow key press = instant slide transition. No debounce confusion, no multi-step flows, no modal dialogs.
- **Launch**: Open URL → content is immediately ready. No loading screens, no splash pages, no configuration.
- **Recovery**: If the presenter accidentally goes back, going forward again returns to exactly where they were — no state loss, no animation replay confusion.
- **Predictability**: Every keypress produces the same result. No conditional UI, no hidden states, no surprises.

### Critical Success Moments

- **First impression**: The presenter opens the URL and sees the first slide in full browser width — the dark theme, typography, and visual quality immediately signal "this is not a PowerPoint."
- **First transition**: The first right-arrow press triggers a smooth, animation-rich transition that confirms the tool works flawlessly. This is the trust-building moment.
- **Mid-presentation flow**: By slide 5-6, the presenter has internalized the rhythm and is no longer thinking about the tool — they're telling the story. The slides are pacing their delivery unconsciously.
- **Make-or-break**: Any visible lag, jank, or animation stutter in front of 50+ developers would undermine the presentation's core message that AI-assisted development produces quality output.

### Experience Principles

1. **Flow-State Navigation**: The interaction is reduced to a single gesture (right arrow). Nothing must interrupt the presenter's mental flow. The tool disappears — only the story remains.
2. **Animation-as-Pacing**: Every animation serves a narrative function. Entrance animations time the delivery. Transitions create breathing room between ideas. Nothing moves without purpose.
3. **Zero-Setup Launch**: From URL to first slide in under 3 seconds. No configuration, no menus, no onboarding. The product is ready the moment it loads.
4. **Credibility-by-Craft**: Visual and technical quality is the silent proof of the presentation's message. Smooth 60fps animations, polished transitions, and attention to typographic detail demonstrate that structured AI development produces professional results.
