---
title: Harden Form Input Ergonomics
impact: MEDIUM-HIGH
impactDescription: reduces form friction and prevents avoidable user errors
tags: form, inputmode, autocomplete, spellcheck, validation, unsaved-changes
---

## Harden Form Input Ergonomics

Small input details materially affect completion rates and error recovery.

**Incorrect (friction and brittle handling):**

```html
<input type="text" placeholder="Phone">
<input type="text" onpaste="event.preventDefault()">
```

**Correct (semantic input behavior):**

```html
<input type="tel" inputmode="tel" autocomplete="tel-national" name="phone">
<input type="email" autocomplete="email" spellcheck="false" name="email">
```

**Rules:**
- Use the right `type`, `name`, `autocomplete`, and `inputmode`.
- Do not block paste in inputs.
- Disable spellcheck for emails, usernames, and one-time codes.
- Keep submit enabled until request start; show clear pending state during submit.
- Warn before navigation when dirty form state would be lost.

Reference: [MDN autocomplete](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/autocomplete)
