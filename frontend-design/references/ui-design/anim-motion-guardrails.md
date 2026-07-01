---
title: Apply Motion and Transition Guardrails
impact: MEDIUM
impactDescription: improves accessibility and prevents avoidable rendering cost
tags: animation, reduced-motion, transition, transform, performance
---

## Apply Motion and Transition Guardrails

Animation should communicate state changes without harming accessibility or performance.

**Incorrect (expensive and inaccessible):**

```css
.panel {
  transition: all 300ms ease;
}
```

**Correct (explicit and accessible):**

```css
.panel {
  transition: transform 200ms ease, opacity 200ms ease;
  transform-origin: center;
}

@media (prefers-reduced-motion: reduce) {
  .panel {
    transition: none;
    transform: none;
  }
}
```

**Rules:**
- Honor `prefers-reduced-motion`.
- Never use `transition: all`; declare specific properties.
- Prefer `transform` and `opacity` over layout-triggering properties.
- Keep interactions interruptible and responsive during animation.
