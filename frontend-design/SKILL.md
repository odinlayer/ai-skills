---
name: frontend-design
description: Consolidated UI/UX + Tailwind CSS design and performance guidance for building or reviewing user-facing web interfaces. Use when designing layouts, responsive behavior, accessibility, forms, interaction patterns, Tailwind architecture, or Core Web Vitals optimizations.
license: MIT
metadata:
  repository: https://github.com/odinlayer/ai-skills/tree/main/frontend-design
  compatibility: Pi skill format; framework-agnostic web UI design/review tasks with Tailwind CSS.
---

# Frontend Design

Use this skill for web UI work where quality matters: structure, usability, Tailwind practices, and performance.

## Scope

- UI/UX strategy and interaction design
- Tailwind CSS architecture and utility usage
- Accessibility and semantic HTML quality
- Responsive behavior and mobile ergonomics
- Core Web Vitals and frontend performance

## Constraints

- Do not assume React, Next.js, or any specific framework.
- Use framework-agnostic guidance unless the user explicitly requests framework specifics.
- Favor HTML, CSS, and Tailwind patterns that transfer across stacks.

## Operating Model

### Phase 0: 0.5-Second Test

Before writing UI code, define what a user should perceive in the first half-second:

- hero metric
- dense table/list
- focused form
- media grid
- timeline/activity stream
- split list/detail workspace

If the answer is generic ("sidebar + cards"), reframe the page around a concrete user moment.

### Phase 1: Experience Brief

Capture:

- user type and immediate context
- primary goal (one task in <10s)
- secondary goals
- pain points
- desired emotional tone (focused, confident, calm, premium, etc.)

### Phase 2: Structure and Interaction

- Map goals to minimal features (`must-have`, `should-have`, `could-have`).
- Keep one primary action per screen.
- Group by user intent, not backend data shape.
- Choose the lightest interaction container that works (inline, popover, sheet, full page).

### Phase 3: Visual and Tailwind System

- Define semantic tokens first (`background`, `foreground`, `primary`, `muted`, `border`).
- Use one primary hue family and controlled variants.
- Prefer semantic Tailwind tokens/classes over raw color utility noise in app chrome.
- Use scale contrast for hierarchy (hero values clearly larger than support text).
- Keep content realistic (names, values, states) to validate design decisions.

### Phase 4: Verification

- Run accessibility checks and keyboard flow review.
- Validate responsive behavior and text fit.
- Validate Core Web Vitals and interaction latency.

## Priority Rule Sets

### UI/UX Rules (Curated + Full Web Vitals)

Reference folder: `references/ui-design/`

| Priority | Category | Prefix |
|---|---|---|
| 1 | Accessibility & WCAG Compliance | `access-` |
| 2 | Core Web Vitals Optimization | `cwv-` |
| 3 | Visual Hierarchy & Layout | `layout-` |
| 4 | Responsive & Mobile-First Design | `resp-` |
| 5 | Typography & Font Loading | `typo-` |
| 6 | Color & Contrast | `color-` |
| 7 | Forms & Validation UX | `form-` |
| 8 | Animation & Performance | `anim-` |

This skill keeps a focused UI/UX subset and preserves the complete Core Web Vitals set:

- `cwv-optimize-lcp`
- `cwv-minimize-cls`
- `cwv-improve-inp`
- `cwv-critical-css`
- `cwv-lazy-load-offscreen`
- `cwv-responsive-images`

### Tailwind Rules (Curated)

Reference folder: `references/tailwind/`

| Priority | Category | Prefix |
|---|---|---|
| 1 | Build Configuration | `build-` |
| 2 | CSS Generation | `gen-` |
| 3 | Bundle Optimization | `bundle-` |
| 4 | Utility Patterns | `util-` |
| 5 | Component Architecture | `comp-` |
| 6 | Theming & Design Tokens | `theme-` |
| 7 | Responsive & Adaptive | `resp-` |
| 8 | Animation & Transitions | `anim-` |

## Tailwind Baseline

- Prefer CSS-first Tailwind v4 patterns where applicable.
- Keep design tokens semantic and consistent.
- Avoid uncontrolled `@apply` sprawl; use utilities directly unless abstraction is justified.
- Use container queries and mobile-first breakpoints intentionally.
- Avoid production CDN usage for Tailwind; optimize bundle generation.

## Palette Helper Scripts

- `scripts/generate_palette.py`: generate semantic color tokens from a seed hue.
- `scripts/verify_palette.py`: verify contrast/harmony invariants.

Example:

```bash
python scripts/generate_palette.py --seed 210 --mode both --items 6 --app "Your App"
```

## Reference Routing

- Accessibility, forms, readability, and layout consistency:
  - start in `references/ui-design/_sections.md`
- Tailwind build, utility syntax, theme tokens, bundle size:
  - start in `references/tailwind/_sections.md`
- Product taste and visual character patterns:
  - `references/web-taste/taste-playbook.md`

## Performance Targets

- LCP: under 2.5s
- CLS: under 0.1
- INP: under 200ms

Apply relevant `cwv-*`, `bundle-*`, and `build-*` references when these targets are at risk.

## Quality Bar

- Layout and hierarchy reflect user goals, not template defaults.
- Keyboard navigation and visible focus states work across primary flows.
- Color and typography meet readability standards.
- Tailwind usage is maintainable, token-driven, and avoids unnecessary bloat.
- Responsive behavior is stable across mobile and desktop.
- Performance tradeoffs are explicit and measurable.

## Output

- Files changed and why.
- Rules/reference files used for decisions.
- Remaining UX/performance debt, if any.
