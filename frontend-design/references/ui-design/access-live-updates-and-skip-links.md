---
title: Add Live Regions and Skip Links
impact: CRITICAL
impactDescription: keeps async updates understandable and improves keyboard navigation in dense pages
tags: access, aria-live, skip-link, headings, navigation, wcag
---

## Add Live Regions and Skip Links

Async feedback and long pages need explicit accessibility affordances.

**Incorrect (silent updates and no bypass path):**

```html
<button onclick="saveSettings()">Save</button>
<div id="toast"></div>
<!-- Toast appears visually, screen reader gets no announcement -->
```

**Correct (announced updates and keyboard bypass):**

```html
<a class="skip-link" href="#main">Skip to main content</a>

<main id="main">
  <h2 id="billing" style="scroll-margin-top: 6rem;">Billing</h2>
</main>

<div aria-live="polite" id="status-region"></div>
```

**Rules:**
- Add a visible-on-focus skip link for complex pages.
- Use `aria-live="polite"` for async status updates (save, validation, uploads).
- Keep heading hierarchy logical and stable.
- Use `scroll-margin-top` on in-page heading anchors when sticky headers exist.

Reference: [WCAG 2.2 Bypass Blocks](https://www.w3.org/WAI/WCAG22/Understanding/bypass-blocks)
