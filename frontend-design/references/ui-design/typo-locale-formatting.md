---
title: Use Locale-Aware Formatting and Translation Guards
impact: MEDIUM
impactDescription: prevents confusing formatting and protects technical terms from mistranslation
tags: typography, i18n, locale, intl, translation
---

## Use Locale-Aware Formatting and Translation Guards

Hardcoded formatting damages clarity for global users and operational tools.

**Incorrect (hardcoded locale assumptions):**

```javascript
const total = "$" + amount.toFixed(2);
const date = month + "/" + day + "/" + year;
```

**Correct (locale-aware formatting):**

```javascript
const total = new Intl.NumberFormat(locale, {
  style: "currency",
  currency: "USD"
}).format(amount);

const date = new Intl.DateTimeFormat(locale, {
  dateStyle: "medium"
}).format(timestamp);
```

**Rules:**
- Use `Intl.NumberFormat` and `Intl.DateTimeFormat` for user-facing values.
- Keep brand names, code tokens, and identifiers opt-out with `translate="no"` when needed.
- Avoid copy that depends on one locale's punctuation/ordering assumptions.
