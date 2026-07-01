# Web Taste Playbook (Framework-Agnostic)

Use this reference to raise visual quality and product feel without relying on framework-specific patterns.

## 1) Start With User Moment, Not Layout

Define before designing:

- Who opened this screen?
- What do they need in under 10 seconds?
- What should they feel (focused, calm, confident, premium)?

If the initial concept is just "sidebar + cards", refine the page shape.

## 2) 0.5-Second Visual Thesis

Pick one dominant first-impression shape:

- Hero metric + sparkline
- Dense operations table
- Focused single-action form
- Media/content grid
- Timeline/activity stream
- Split list/detail workspace

One screen should have one clear primary visual thesis.

## 3) Hierarchy Through Scale

- Make the most important value physically large.
- Push secondary context into quieter text styles.
- Use whitespace intentionally; density is a choice, not a default.

## 4) Color Discipline

- Use one primary hue family and semantic tokens.
- Avoid random raw utility colors for product chrome.
- Keep status colors semantically consistent (`success`, `warning`, `error`, `info`).

## 5) Card vs Row Grammar

- Use cards for heterogeneous content and summaries.
- Use rows/tables for homogeneous, scan-heavy data.
- Do not mix both structures randomly in the same context.

## 6) Content Realism

- Use plausible names, values, timestamps, and states.
- Avoid placeholder-heavy UI in final output.
- Ensure empty states show next action, not only absence.

## 7) Interaction Quality

- Every interactive element needs clear hover/focus/active states.
- Respect reduced motion preferences.
- Keep destructive actions isolated and explicit.

## 8) Consistency Rules

- Reuse spacing, radius, and typography scales.
- Keep component states and labels consistent across screens.
- Prefer predictable layout patterns over decorative variation.

## 9) Performance-Aware Polish

- Prefer subtle transforms/opacity for animations.
- Avoid expensive visual effects on critical paths.
- Keep the most important content fast to render and stable.
