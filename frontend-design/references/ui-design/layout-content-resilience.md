---
title: Make Layouts Resilient to Long Content
impact: HIGH
impactDescription: prevents overflow, overlap, and broken scanning in real-world data
tags: layout, overflow, truncation, line-clamp, min-w-0, resilience
---

## Make Layouts Resilient to Long Content

Production data is often longer than mocks. Plan for extremes early.

**Incorrect (text breaks flex/grid layouts):**

```html
<div class="flex gap-3">
  <div class="font-medium">Very long project name without breaks ...</div>
</div>
```

**Correct (controlled overflow behavior):**

```html
<div class="flex min-w-0 gap-3">
  <div class="min-w-0 truncate font-medium">Very long project name ...</div>
</div>
<p class="line-clamp-3 break-words">Long user-generated description ...</p>
```

**Rules:**
- Set `min-w-0` on flex/grid children that hold text.
- Use `truncate`, `line-clamp-*`, and `break-words` intentionally.
- Define empty-state behavior for lists, panels, and details views.
- Test with short, average, and extreme-length user content.
