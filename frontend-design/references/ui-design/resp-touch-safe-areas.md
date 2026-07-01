---
title: Optimize Touch Interaction and Safe Areas
impact: MEDIUM-HIGH
impactDescription: improves mobile reliability and reduces accidental interaction bugs
tags: responsive, touch, safe-area, mobile, modal
---

## Optimize Touch Interaction and Safe Areas

Mobile interaction quality depends on explicit touch and viewport handling.

**Incorrect (fragile mobile behavior):**

```css
.drawer { overflow-y: auto; }
```

**Correct (touch-safe behavior):**

```css
.tap-target { touch-action: manipulation; }
.drawer { overscroll-behavior: contain; }
.safe-shell {
  padding-top: env(safe-area-inset-top);
  padding-bottom: env(safe-area-inset-bottom);
}
```

**Rules:**
- Set `touch-action: manipulation` for common tap controls.
- Use `overscroll-behavior: contain` for modals/drawers/sheets.
- Define `-webkit-tap-highlight-color` intentionally.
- Respect notch and home-indicator areas with `env(safe-area-inset-*)`.
- Ensure controls remain reachable and readable in narrow/mobile viewports.
