# STORY-001: Project Setup

**Priority:** P0 — Must Have
**Story Points:** 2
**Status:** Not Started

---

## User Story

As the presenter,
I want a working Reveal.js project with Vite dev server,
So that I can start building slides immediately.

---

## Scope

**In scope:**
- npm init + install reveal.js and vite
- Create file structure per architecture (index.html, css/theme.css, css/animations.css, assets/)
- Configure vite.config.js for dev server
- Create minimal index.html with Reveal.js boilerplate (1 test slide)
- Verify `npm run dev` serves on localhost with HMR

**Out of scope:**
- Actual slide content
- Theming (beyond Reveal.js defaults)
- Animations

---

## Acceptance Criteria

- [ ] `npm run dev` starts Vite dev server on localhost
- [ ] Browser shows a single test slide with Reveal.js running
- [ ] Arrow keys navigate (even with just 1 slide, no errors)
- [ ] File structure matches architecture document
- [ ] HMR works (edit CSS → browser updates without refresh)

---

## Technical Notes

### Files to Create

```
conf-bmad/
├── index.html
├── css/
│   ├── theme.css         (empty placeholder)
│   └── animations.css    (empty placeholder)
├── assets/
│   ├── fonts/
│   └── images/
├── vite.config.js
└── package.json
```

### Dependencies

```bash
npm init -y
npm install reveal.js
npm install -D vite
```

### index.html Boilerplate

- Import reveal.js CSS and JS
- Single `<section>` with "conf-bmad" test title
- Initialize Reveal with basic config (keyboard: true, hash: false, controls: false)

---

## Definition of Done

- [ ] All files created per structure
- [ ] Dev server runs without errors
- [ ] Test slide visible in Chrome
- [ ] HMR functional
