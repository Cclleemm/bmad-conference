---
stepsCompleted: [1, 2, 3, 4, 5]
inputDocuments:
  - "https://buildmode.dev/blog/bmad-method-deep-dive/ (web reference)"
date: 2026-02-20
author: Clement.raussin
---

# Product Brief: conf-bmad

<!-- Content will be appended sequentially through collaborative workflow steps -->

## Executive Summary

conf-bmad is a browser-based slide deck (5 minutes) for the DevOps Meetup Geneva, followed by a separate live demo. The presentation tells the personal story of a millennial developer — initially dismissive of vibe coding as unreliable for enterprise — who discovered through hands-on experience that AI-assisted development has real potential, but only when paired with structured methodology. BMAD (Breakthrough Method of Agile AI-driven Development) is presented humbly as one possible answer to the industrialization challenge, not the definitive solution. The slide deck is visually geeky/dev-culture, designed as a web front-end rather than traditional presentation software.

---

## Core Vision

### Problem Statement

Vibe coding is exploding in popularity, but enterprise adoption faces a credibility wall. Individual developers get impressive results on small tasks, yet scaling AI-assisted development to real projects exposes critical failures: context loss between sessions, architectural inconsistencies, mounting technical debt, zero documentation trail, and no meaningful collaboration workflow for DevOps teams. The dev community is split between enthusiasts and skeptics, with no clear path to industrialization.

### Problem Impact

Without structured approaches, enterprises either reject AI-assisted development entirely (losing competitive advantage) or adopt it chaotically (accumulating hidden technical debt). DevOps teams — built on principles of determinism, reproducibility, and collaboration — have no framework to integrate vibe coding into their existing culture and pipelines.

### Why Existing Solutions Fall Short

Current approaches to scaling vibe coding range from ad-hoc prompt libraries to informal team conventions. Several methodologies are emerging in this space, but the fundamental challenge remains: most treat AI as a code generator rather than a collaborative workflow participant. There is no widely adopted standard for turning AI-assisted development into a deterministic, auditable, team-friendly process.

### Proposed Solution

A 5-minute browser-based slide presentation that walks the DevOps Meetup Geneva audience through a relatable narrative arc: skepticism → experimentation → revelation → the scaling problem → BMAD as one structured response. The storytelling leverages the presenter's authentic journey (testing BMAD on a large personal legacy project) to make the case that vibe coding industrialization is both necessary and achievable. Followed by a separate live demo to show BMAD in action.

### Key Differentiators

- **Authentic narrative**: Real developer journey, not vendor pitch — humble positioning acknowledging other methods exist
- **DevOps-native framing**: Speaks directly to the meetup audience's values (determinism, collaboration, pipelines, living documentation)
- **Browser-native delivery**: The medium IS the message — a web app presenting about web-native AI development
- **Conversation starter, not final word**: Positions BMAD as "the first critiquable — and brilliant — chapter" rather than the complete answer

## Target Users

### Primary Users

**The Presenter (Clement)**
- Millennial developer, DevOps background, presenting at DevOps Meetup Geneva
- Runs the slide deck locally on Mac via browser
- Needs classic keyboard controls (arrow keys, clicker compatible), fluid navigation
- Expects beautiful, minimalist design with smooth animations
- Single-use scenario: launch page, present, done

### Secondary Users

**Meetup Audience**
- DevOps Meetup Geneva attendees — technical profiles (devs, ops, SREs)
- Passive consumers: they watch the projected slides, no interaction
- Need clear readability at projection distance, visual impact that reinforces the geeky/dev-culture tone

### User Journey

1. **Presenter**: Opens local URL → full-screen browser → navigates slides with keyboard arrows → presents 5 minutes → done
2. **Audience**: Watches projected slides → follows the narrative arc (skepticism → discovery → BMAD) → retains key takeaways on vibe coding industrialization

## Success Metrics

- **Visual impact**: Slides with polished animations and transitions that reinforce the narrative rhythm — each slide feels intentional, not decorative
- **Design quality**: Minimalist, geeky aesthetic that a DevOps audience instantly respects — dark theme, clean typography, dev-culture visual language
- **Storytelling enforcement**: The slide structure itself drives the narrative arc — the presenter can't get lost because the flow (skepticism → test → potential → chaos → BMAD → punchline) is baked into the sequence and animations

### Business Objectives

N/A — This is a one-shot meetup presentation, not a commercial product.

### Key Performance Indicators

- Animations are smooth and distraction-free on local Mac/browser
- Slide count fits comfortably in 5 minutes (~1 slide per 20-30 seconds)
- Narrative arc is self-evident from slides alone — no need to memorize a script

## MVP Scope

### Core Features

- **Slide deck complet**: Toutes les slides couvrant l'arc narratif (skepticisme → test → potentiel → chaos à l'échelle → BMAD comme réponse → punchline finale)
- **Navigation clavier**: Flèches gauche/droite pour avancer/reculer entre les slides
- **Animations & transitions**: Transitions fluides entre slides, animations d'entrée des éléments pour rythmer le storytelling
- **Design dark/geek/minimaliste**: Thème sombre, typographie clean, esthétique dev-culture lisible en projection

### Out of Scope for MVP

- Partage en ligne / hébergement
- Mode speaker notes
- Export PDF
- Responsive mobile
- Timer / progress bar
- Mode fullscreen automatique (le présentateur fait F11 manuellement)

### MVP Success Criteria

- Les slides défilent sans accroc sur Mac/Chrome en local
- L'arc narratif est complet et auto-portant en ~10-15 slides
- Les animations renforcent le storytelling sans distraire
- Le design est cohérent et visuellement impactant sur vidéoprojecteur

### Future Vision

N/A — Projet one-shot pour le DevOps Meetup Geneva.
