# STORY-006: Workflow Status Slide — Sprint & Stories Overview

**Priority:** P0 — Must Have
**Story Points:** 3
**Status:** Not Started
**Depends on:** STORY-004
**Created:** 2026-02-23

---

## User Story

As the presenter,
I want a slide showing the workflow-status output with completed phases and the sprint stories table,
So that the audience sees the concrete output of the BMAD planning process before the live demo.

---

## Description

### Background

After demonstrating the product-brief workflow (slide 15) and showing the roadmap of phases (slide 16), the presentation needs a "result" slide that shows what happens when all the planning workflows complete. This slide bridges the gap between "here's the process" and "now let's code" (live demo).

The content is based on the real `/workflow-status` output from the Fondue DevOps MeetUp Geneva demo project — a web app for choosing fondue type and pickle count at the meetup.

### Narrative Purpose

This slide is the payoff moment: "All that structured workflow produced THIS — a clear sprint with 12 organized stories, ready to code." It demonstrates that BMAD turns vague requirements into a concrete, actionable sprint plan.

---

## Scope

**In scope:**
- New slide inserted after slide 16 (roadmap) and before slide 17 (merci)
- Terminal-style frame consistent with slides 13-15 (install, workflow-init, product-brief)
- Workflow status display showing:
  - Phases 1-3 completed (✓) with file paths
  - Phase 4 current (→) with sprint info
  - Sprint table with stories (day, ID, title, points, priority, status)
- Fragment reveals to pace the content delivery
- CSS styling in theme.css/animations.css for the status display

**Out of scope:**
- Changes to existing slides
- New SVG gradients or design system changes
- Interactive elements

---

## Content Reference

The slide content is based on this workflow-status output:

```
Project: Fondue DevOps MeetUp Geneva (web-app, Level 3)
Progress: 3/5 core workflows completed | Sprint 1 planned

✓ Phase 1: Analysis
  ✓ product-brief → docs/product-brief-fondue-...md

✓ Phase 2: Planning
  ✓ prd → docs/prd-fondue-...md

✓ Phase 3: Solutioning
  ✓ architecture → docs/architecture-fondue-...md

→ Phase 4: Implementation [CURRENT]

Sprint 1 — "Deliver a fully functional fondue choice app..."

Stories (12 total):
┌─────┬───────────┬──────────────────────────────────┬─────┬──────────┐
│ Day │   Story   │              Title               │ Pts │ Priority │
├─────┼───────────┼──────────────────────────────────┼─────┼──────────┤
│ 1   │ STORY-001 │ Project Setup & Database Schema  │ 3   │ must     │
│ 1   │ STORY-002 │ Submit Choice Server Action      │ 2   │ must     │
│ 1   │ STORY-003 │ Guest Form UI                    │ 3   │ must     │
│ 2   │ STORY-005 │ Dashboard Stats Cards            │ 3   │ must     │
│ 2   │ STORY-006 │ Submissions Table                │ 2   │ must     │
│ 3   │ STORY-004 │ Submission Confirmation          │ 1   │ should   │
│ 3   │ STORY-009 │ Responsive Layout & Styling      │ 3   │ must     │
│ 3   │ STORY-010 │ Form Validation & Error Handling │ 2   │ must     │
│ 4   │ STORY-007 │ Submissions API Route            │ 2   │ should   │
│ 4   │ STORY-008 │ Dashboard Auto-Refresh           │ 2   │ could    │
│ 4   │ STORY-011 │ Deploy to Vercel                 │ 3   │ must     │
│ 5   │ STORY-012 │ Modify Existing Submission       │ 3   │ could    │
└─────┴───────────┴──────────────────────────────────┴─────┴──────────┘

Recommended Next Step:
Run /dev-story STORY-001 to start implementing.
```

**Design notes:**
- Keep it simple and visual — the table is the star
- Use the same terminal-frame aesthetic as previous demo slides
- Use existing terminal CSS classes (`.terminal-frame`, `.terminal-body`, `.term-line`, etc.)
- Use colored status indicators: green ✓ for completed phases, cyan → for current
- Fragment reveals: phases first, then sprint info, then stories table, then next step

---

## Acceptance Criteria

- [ ] New slide appears after roadmap (slide 16) and before merci
- [ ] Uses terminal-frame aesthetic consistent with slides 13-15
- [ ] Shows phases 1-3 as completed (✓) with green color
- [ ] Shows phase 4 as current (→) with cyan/highlight color
- [ ] Displays sprint stories in a clean table format
- [ ] Fragment reveals pace the content (3-4 fragments)
- [ ] Text readable at projection distance (adequate font size)
- [ ] No horizontal overflow — content fits within terminal frame
- [ ] Forward/backward navigation works correctly with fragments
- [ ] Terminal auto-scroll works when fragments overflow

---

## Technical Notes

### HTML Structure

- Single new `<section>` element in `index.html`
- Uses existing terminal CSS classes (`.terminal-frame`, `.terminal-wide`, `.terminal-body`, `.terminal-body-left`)
- Uses existing terminal text classes (`.term-line`, `.t-prompt`, `.t-success`, `.t-dim`, `.t-answer`, `.t-cyan`, `.t-brand`)
- Fragment reveals via `.fragment` with `data-fragment-index`
- Table rendered as styled `<div>` lines (consistent with terminal aesthetic) rather than HTML `<table>`

### CSS

- Minimal new CSS — reuse existing terminal styles
- May need minor additions for table-row styling within terminal
- Follow existing patterns in `theme.css` and `animations.css`

### Insertion Point

- After the current slide 16 (`.slide-roadmap`)
- Before the current slide 17 (`.slide-thanks`)
- This becomes slide 17, and "Merci" becomes slide 18

---

## Dependencies

**Prerequisite Stories:**
- STORY-004: Slide Content, Design & Animations (must be complete — it is)

**Blocked Stories:**
- None

**External Dependencies:**
- None

---

## Definition of Done

- [ ] HTML section added to `index.html` at correct position
- [ ] CSS styles added (if any new ones needed)
- [ ] Fragment reveals work correctly (forward and backward)
- [ ] Terminal auto-scroll works if content overflows
- [ ] Content matches the workflow-status reference above
- [ ] Visually consistent with slides 13-15 (terminal aesthetic)
- [ ] Readable at projection distance
- [ ] No CSS or layout regressions on other slides

---

## Story Points Breakdown

- **HTML:** 2 points (terminal content with fragments)
- **CSS:** 1 point (minor additions, mostly reusing existing styles)
- **Total:** 3 points

**Rationale:** Moderate complexity — significant content to lay out in terminal format, but reuses established terminal patterns from slides 13-15.
