# STORY-005: Projection Test & Final Polish

**Priority:** P1 — Should Have
**Story Points:** 2
**Status:** Not Started
**Depends on:** STORY-004

---

## User Story

As the presenter,
I want to verify the slides work perfectly on a projector,
So that the presentation looks great at the DevOps Meetup Geneva.

---

## Scope

**In scope:**
- Test on external display (HDMI projector or external monitor)
- Verify font readability at projection distance
- Verify contrast ratios hold on projector (projectors lose contrast)
- Verify animations run smooth on external display
- Adjust font sizes, colors, spacing if needed
- Full run-through rehearsal (5 minutes timing)

**Out of scope:**
- Content changes (STORY-004)
- New slides or structural changes

---

## Acceptance Criteria

- [ ] All text readable from back of room (~5m distance)
- [ ] Colors and contrast hold on projector display
- [ ] Animations smooth on external display (no lag from dual-screen)
- [ ] Full presentation fits in 5 minutes
- [ ] No visual glitches, overflow, or clipping on projector resolution
- [ ] F11 fullscreen works correctly in Chrome
- [ ] Forward/backward navigation works flawlessly through all slides

---

## Test Checklist

- [ ] Connect to external display
- [ ] Open localhost in Chrome, F11 fullscreen
- [ ] Navigate all slides forward
- [ ] Navigate all slides backward
- [ ] Check text readability at distance
- [ ] Check contrast on projector
- [ ] Check animation smoothness
- [ ] Time full run-through
- [ ] Note any adjustments needed

---

## Definition of Done

- [ ] Projection test completed
- [ ] All issues found are fixed
- [ ] Full rehearsal timed at ~5 minutes
- [ ] Presenter confident and ready
