---
stepsCompleted: [1, 2, 3, 4, 5, 6, 7, 8]
lastStep: 8
status: 'complete'
completedAt: '2026-02-23'
inputDocuments:
  - "product-brief-conf-bmad-2026-02-20.md"
  - "prd.md"
  - "ux-design-specification.md"
workflowType: 'architecture'
project_name: 'conf-bmad'
user_name: 'Clement.raussin'
date: '2026-02-23'
---

# Architecture Decision Document

_This document builds collaboratively through step-by-step discovery. Sections are appended as we work through each architectural decision together._

## Project Context Analysis

### Requirements Overview

**Functional Requirements:**
6 FRs identified — slide navigation (F-001), smooth transitions (F-002), element animations (F-003), dark/geek theme (F-004), full narrative arc content (F-005), and projection optimization (F-006). All are tightly coupled: navigation triggers transitions, transitions trigger element animations, all rendered within the theme system and optimized for projection.

**Non-Functional Requirements:**
- Performance: <2s page load on localhost, 60fps animations with zero jank, transitions <500ms
- Browser: Chrome on macOS only — no cross-browser concerns
- Accessibility: WCAG AA contrast ratios, large projection-readable fonts
- Architecture: Fully static — no server, no network dependency, no build step at presentation time
- Reliability: Must not crash or stutter during a live 5-minute presentation

**Scale & Complexity:**

- Primary domain: Static front-end (browser-based slide deck)
- Complexity level: Low
- Estimated architectural components: 3-5 (navigation engine, animation system, theme/design system, slide content, optional dev server)

### Technical Constraints & Dependencies

- Runs on localhost only — no deployment, no hosting
- Chrome macOS is the sole target — can use modern CSS/JS without polyfills
- Zero external dependencies at runtime — all assets bundled/local
- Single-use project — no maintenance, no versioning, no updates post-event
- Framework decision pending: Reveal.js, Slidev, or vanilla SPA (PRD defers to architecture phase)

### Cross-Cutting Concerns Identified

- **Animation performance**: Affects every slide — must be GPU-accelerated (CSS transforms/opacity), no layout thrashing
- **Theme consistency**: Dark palette, typography scale, and spacing must be uniform across all slides
- **Navigation state**: Forward/backward must be deterministic — no animation replay confusion, no state loss
- **Projection readability**: Font sizes, contrast ratios, and spacing must be validated for projection distance, not desktop viewing

## Starter Template Evaluation

### Primary Technology Domain

Static front-end — browser-based slide deck with bespoke per-slide design, custom animations, and dark/dev-culture aesthetic.

### Starter Options Considered

**Option 1: Slidev (v52.12.0)** — REJECTED
- Markdown-based with Vue 3 components
- Excellent DX with Vite HMR, Shiki syntax highlighting, UnoCSS
- Rejected because: Markdown-first approach is too rigid for bespoke slide-by-slide layouts. The project requires radically different layouts and animations per slide, not structured content. Slidev's strength (fast structured content) is not aligned with the creative freedom needed.

**Option 2: Reveal.js (v5.2.1)** — SELECTED
- HTML-based slide framework with full per-slide control
- Each `<section>` is a self-contained slide with complete HTML/CSS freedom
- Auto-Animate for cinematic cross-slide element transitions
- Custom CSS animations per slide via data-attributes and CSS classes
- 11 built-in themes + full CSS custom property theming
- GPU-accelerated transforms for 60fps performance
- Mature ecosystem (10+ years), stable, well-documented

### Selected Starter: Reveal.js (v5.2.1)

**Rationale for Selection:**
The project requires bespoke visual design — different layouts per slide, different animations per slide, and a polished dev-culture aesthetic. Reveal.js provides HTML-first authoring where each slide is a fully customizable `<section>`, enabling radical per-slide variation without fighting a template system. For a one-shot presentation where maintainability is irrelevant, maximum creative control is the priority.

**Initialization Command:**

```bash
npm init
npm install reveal.js
```

**Architectural Decisions Provided by Starter:**

**Language & Runtime:**
HTML/CSS/JavaScript — no TypeScript needed for a one-shot project. Chrome macOS only, so modern ES2024+ syntax is safe.

**Styling Solution:**
Custom CSS with Reveal.js CSS custom properties for theming. No CSS framework needed — bespoke per-slide styling is the goal.

**Build Tooling:**
Minimal — Reveal.js can run with a simple local server (e.g., Vite dev server or `npx serve`). No complex build pipeline needed.

**Code Organization:**
Single `index.html` with embedded slides, a custom `theme.css` for the dark/geek design system, and optional per-slide CSS for bespoke animations.

**Development Experience:**
Vite dev server for hot reload during development. Browser DevTools for animation tuning.

**Note:** Project initialization using this setup should be the first implementation story.

## Core Architectural Decisions

### Decision Priority Analysis

**Critical Decisions (Block Implementation):**
All critical decisions are resolved — framework (Reveal.js), file structure (single file), animation approach (combined), and dev server (Vite).

**Important Decisions (Shape Architecture):**
Theming strategy, font choices, and projection calibration — addressed below.

**Deferred Decisions:**
None — project scope is small enough that all decisions are made upfront.

### N/A Categories

The following standard architecture categories do not apply to this project:
- **Data Architecture**: No database, no data model, no persistence, no caching
- **Authentication & Security**: No auth, no users, no API, runs locally only
- **API & Communication**: No API, no backend, no external services
- **Infrastructure & Deployment**: No hosting, no CI/CD, no environments — localhost only

### Frontend Architecture

**File Structure: Single File**
- One `index.html` containing all ~12 slides as `<section>` elements
- One `theme.css` for the dark/geek design system (palette, typography, spacing)
- One `animations.css` for custom per-slide `@keyframes` and animation classes
- Assets folder for fonts and images
- `vite.config.js` for dev server configuration

**Animation Strategy: Combined Approach**
Three Reveal.js animation mechanisms used where each excels:
1. **Fragments** (`.fragment`) — sequential element reveals within a slide for pacing text delivery
2. **Auto-Animate** (`data-auto-animate`) — cinematic morphing transitions between consecutive slides sharing common elements
3. **Custom CSS @keyframes** — bespoke signature effects per slide (typewriter, staggered reveals, glow effects, etc.)

All animations must use GPU-composited properties only (`transform`, `opacity`) to guarantee 60fps. No `width`, `height`, `top`, `left`, or `margin` animations.

**Navigation State:**
Reveal.js handles forward/backward navigation natively. Fragments are stateful — going back reverses fragment reveals in order. Auto-Animate transitions play in reverse when navigating backward. No custom state management needed.

### Development Setup

**Dev Server: Vite**
- Vite dev server for instant HMR during slide/CSS iteration
- Simple `vite.config.js` pointing to `index.html` as entry
- No build step needed for presentation — Vite dev server serves the presentation directly
- `npm run dev` to start, open `localhost:5173` in Chrome

**Project Structure:**
```
conf-bmad/
├── index.html          # All slides (Reveal.js sections)
├── theme.css           # Dark/geek design system
├── animations.css      # Custom per-slide animations
├── assets/
│   ├── fonts/          # Bundled fonts (monospace, sans-serif)
│   └── images/         # Slide visuals if needed
├── vite.config.js      # Dev server config
├── package.json
└── node_modules/
    └── reveal.js/
```

### Decision Impact Analysis

**Implementation Sequence:**
1. Initialize project (npm, Vite, Reveal.js)
2. Create theme.css (dark palette, typography, base spacing)
3. Build slide structure in index.html (empty sections with narrative arc)
4. Design each slide bespoke (layout, content, animations)
5. Tune animations and transitions for 60fps
6. Test on external display for projection readability

**Cross-Component Dependencies:**
- theme.css must be finalized before per-slide design (establishes palette, fonts, spacing)
- Animation classes in animations.css are referenced by slide HTML — co-developed iteratively
- Reveal.js configuration (transition speed, controls, progress bar) set once in initialization

## Implementation Patterns & Consistency Rules

### Pattern Categories Defined

**Critical Conflict Points Identified:** 3 areas where AI agents could make different choices — CSS naming, HTML slide structure, and animation performance rules.

### CSS Naming Conventions

**Class Naming (kebab-case with semantic prefixes):**
- Slide classes: `.slide-{name}` (e.g., `.slide-skepticism`, `.slide-bmad-response`)
- Animation classes: `.anim-{name}` (e.g., `.anim-fade-up`, `.anim-typewriter`)
- Layout helpers: `.layout-{name}` (e.g., `.layout-centered`, `.layout-split`)

**CSS Custom Properties (semantic naming):**
- Colors: `--color-primary`, `--color-bg`, `--color-text`, `--color-accent`
- Fonts: `--font-mono`, `--font-sans`, `--font-size-xl`
- Spacing: `--spacing-sm`, `--spacing-md`, `--spacing-lg`
- Animation: `--duration-fast`, `--duration-normal`, `--duration-slow`

**Rule:** No inline styles. All styling in `theme.css` or `animations.css`.

### HTML Slide Structure

Every slide follows the same skeleton, regardless of internal layout:

```html
<section class="slide-{name}" data-transition="slide"
         data-background-color="var(--bg-slide)">
  <div class="slide-content">
    <!-- Bespoke content here — layout varies freely -->
  </div>
</section>
```

- `.slide-content` wrapper is mandatory for consistent padding/centering
- Internal layout within `.slide-content` is fully bespoke per slide
- `data-transition` can vary per slide (slide, fade, convex, none)
- `data-background-color` uses CSS custom properties from theme

### Animation Performance Rules

**Mandatory for all agents:**

1. **GPU-only properties**: Only `transform` and `opacity` in `@keyframes` — never `width`, `height`, `top`, `left`, `margin`, `padding`
2. **will-change declaration**: Set `will-change: transform, opacity` on animated elements
3. **Duration range**: 300ms–800ms for consistency of narrative rhythm
4. **Easing**: Use `cubic-bezier()` or named easings (`ease-out`, `ease-in-out`) — never `linear` for element animations
5. **No JS animations**: All animations are CSS-only for GPU compositing guarantee

### Enforcement Guidelines

**All AI Agents MUST:**
- Use the CSS naming conventions above (prefixed kebab-case)
- Wrap slide content in `.slide-content` div
- Restrict animations to `transform`/`opacity` only
- Reference theme custom properties instead of hardcoded values

**Anti-Patterns:**
- `style="color: #fff"` → use `var(--color-text)` in CSS class
- `@keyframes { 50% { width: 200px } }` → use `transform: scaleX()` instead
- `<section><h1>Title</h1></section>` → missing `.slide-content` wrapper

## Project Structure & Boundaries

### Complete Project Directory Structure

```
conf-bmad/
├── index.html            # Entry point + all slides (<section> elements)
├── css/
│   ├── theme.css         # Design system (palette, typography, spacing, custom properties)
│   └── animations.css    # Custom @keyframes + .anim-* classes
├── assets/
│   ├── fonts/            # Bundled fonts (monospace + sans-serif)
│   └── images/           # Slide visuals (logos, illustrations if needed)
├── vite.config.js        # Dev server configuration
├── package.json          # Dependencies (reveal.js, vite)
└── .gitignore
```

### Requirements to Structure Mapping

| FR | File(s) |
|----|---------|
| F-001 Slide Navigation | `index.html` (Reveal.js config `keyboard: true`) |
| F-002 Slide Transitions | `index.html` (`data-transition` per section) + `css/animations.css` |
| F-003 Element Animations | `css/animations.css` (@keyframes) + `index.html` (`.fragment`, `.anim-*` classes) |
| F-004 Dark/Geek Theme | `css/theme.css` (palette, fonts, custom properties) |
| F-005 Narrative Arc Content | `index.html` (content of ~12 `<section>` elements) |
| F-006 Projection Readability | `css/theme.css` (font-size, contrast ratios, spacing) |

### Architectural Boundaries

No complex boundaries. Everything runs in a single browser context:

- **css/theme.css** defines the design system → consumed by `index.html` and `css/animations.css`
- **css/animations.css** defines animation effects → referenced as classes in `index.html`
- **Reveal.js** provides the runtime engine (navigation, fragments, auto-animate) → imported in `index.html`

### Data Flow

```
Keypress (→/←) → Reveal.js engine → Slide transition (CSS) → Fragment/Animation triggers (CSS) → Render (GPU)
```

No application state, no data persistence, no inter-component communication. Pure DOM + CSS rendering pipeline.

## Architecture Validation Results

### Coherence Validation ✅

**Decision Compatibility:**
Reveal.js + Vite + custom CSS: no conflicts. Vite serves `index.html` in dev mode, Reveal.js handles slide runtime, CSS handles all visuals. Minimal, coherent stack with no version conflicts.

**Pattern Consistency:**
CSS conventions (`.slide-*`, `.anim-*`, custom properties) are fully compatible with Reveal.js HTML structure. Performance rules (GPU-only animations) align with 60fps target.

**Structure Alignment:**
The `index.html` + `css/` + `assets/` structure supports all architectural decisions without overhead.

### Requirements Coverage Validation ✅

**Functional Requirements:**

| FR | Status | Solution |
|----|--------|----------|
| F-001 Slide Navigation | ✅ | Reveal.js native keyboard navigation |
| F-002 Slide Transitions | ✅ | `data-transition` + custom CSS |
| F-003 Element Animations | ✅ | Fragments + Auto-Animate + @keyframes |
| F-004 Dark/Geek Theme | ✅ | `theme.css` with CSS custom properties |
| F-005 Narrative Arc | ✅ | ~12 `<section>` elements in `index.html` |
| F-006 Projection Readability | ✅ | `theme.css` (font-size, contrast ratios) |

**Non-Functional Requirements:**

| NFR | Status | Solution |
|-----|--------|----------|
| <2s page load | ✅ | Static, localhost, no network |
| 60fps animations | ✅ | GPU-only properties enforced |
| Chrome macOS only | ✅ | No polyfills, modern CSS/JS |
| WCAG AA contrast | ✅ | Theme custom properties calibrated for projection |
| Zero network dependency | ✅ | All assets bundled locally |
| No crash during 5min | ✅ | Minimal stack, no complex JS |

### Gap Analysis Results

**Critical Gaps:** None.

**Minor Gaps (non-blocking, resolved at implementation):**
- Specific font choices (monospace/sans-serif families) — design decision, not architectural
- Exact color palette values — design decision, not architectural
- Reveal.js config details (progress bar, controls visibility) — implementation detail

### Architecture Completeness Checklist

**✅ Requirements Analysis**
- [x] Project context thoroughly analyzed
- [x] Scale and complexity assessed (low)
- [x] Technical constraints identified (Chrome macOS, localhost, static)
- [x] Cross-cutting concerns mapped (animation perf, theme, navigation state, projection)

**✅ Architectural Decisions**
- [x] Framework: Reveal.js v5.2.1
- [x] Dev server: Vite
- [x] File structure: single `index.html` + CSS files
- [x] Animation strategy: combined (fragments + auto-animate + custom CSS)
- [x] Performance constraints documented (GPU-only)

**✅ Implementation Patterns**
- [x] CSS naming conventions established (prefixed kebab-case)
- [x] HTML slide skeleton defined
- [x] Animation performance rules documented
- [x] Anti-patterns identified

**✅ Project Structure**
- [x] Complete directory structure defined
- [x] All FRs mapped to specific files
- [x] Architectural boundaries established
- [x] Data flow documented

### Architecture Readiness Assessment

**Overall Status:** READY FOR IMPLEMENTATION

**Confidence Level:** High — simple project, clear scope, minimal and proven stack.

**Key Strengths:**
- Minimal complexity — only what's needed, nothing more
- Proven framework (Reveal.js, 10+ years) for reliability
- Full creative freedom per slide with HTML-first authoring
- GPU-enforced animation performance rules prevent 60fps issues

**Implementation Handoff:**

**AI Agent Guidelines:**
- Follow all architectural decisions exactly as documented
- Use implementation patterns consistently (CSS naming, HTML skeleton, GPU-only animations)
- Respect project structure (`index.html`, `css/theme.css`, `css/animations.css`)
- Refer to this document for all architectural questions

**First Implementation Priority:**
Initialize project with `npm init` + `npm install reveal.js vite`, create base files, configure Vite dev server.
