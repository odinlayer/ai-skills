# frontend-design

Repository: https://github.com/odinlayer/ai-skills/tree/main/frontend-design

License: MIT

`frontend-design` is now a consolidated skill that merges:

- OdinLayer's original frontend design guidance
- curated `ui-design` best-practice rules
- curated `web-taste` design-taste guidance
- curated `tailwind` performance + architecture rules

## Files

- `SKILL.md` - Unified UI/UX + Tailwind + performance workflow (framework-agnostic).
- `README.md` - Human-facing notes and source lineage.
- `references/ui-design/` - curated UI/UX rules plus the full Core Web Vitals set.
- `references/tailwind/` - curated Tailwind architecture/performance rules.
- `references/web-taste/taste-playbook.md` - framework-agnostic design taste playbook.
- `scripts/generate_palette.py` - semantic palette generator (seed hue based).
- `scripts/verify_palette.py` - palette verification helper.

## Features

- Framework-agnostic UI/UX guidance for professional, consistent web interfaces.
- Tailwind-focused architecture and token-driven styling practices.
- Full Core Web Vitals rule coverage through curated references.
- Mobile/touch safety, URL-state deep-linking, and long-content resilience guidance.
- Locale-aware formatting and accessibility updates (`aria-live`, skip links).
- Compact web-taste playbook for visual hierarchy and product feel.
- Palette generation and validation helpers for cohesive theming.

## Source Lineage

1) OdinLayer base skill
- Local prior `frontend-design` implementation

2) Anthropic plugin adaptation source
- https://github.com/anthropics/claude-plugins-official/tree/main/plugins/frontend-design

3) dot-skills curated sources
- UI design:
  https://github.com/pproenca/dot-skills/tree/master/skills/.curated/ui-design
- Web taste:
  https://github.com/pproenca/dot-skills/tree/master/skills/.curated/web-taste
- Tailwind:
  https://github.com/pproenca/dot-skills/tree/master/skills/.curated/tailwind

4) Additional review heuristics adapted from:
- https://github.com/vercel-labs/web-interface-guidelines
