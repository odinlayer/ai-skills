---
title: Encode UI State in URL When It Matters
impact: HIGH
impactDescription: improves shareability, navigation continuity, and user trust
tags: layout, navigation, state, url, deep-linking
---

## Encode UI State in URL When It Matters

Stateful interfaces should preserve meaningful context across refresh and share.

**Incorrect (state lost on reload):**

```text
/orders
```

**Correct (stateful deep link):**

```text
/orders?status=pending&sort=updated_desc&page=3&tab=fraud
```

**Rules:**
- Encode filters, tab/view mode, sort order, and pagination in query params.
- Keep destructive operations out of URL params; keep them explicit in UI flow.
- Preserve back/forward navigation semantics when state changes.
- Prefer durable URLs for investigation and collaboration workflows.
