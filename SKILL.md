---
name: odinlayer-skills
description: Router skill for the OdinLayer multi-skill repository. Use when tasks involve WordPress security audits, office document workflows (DOCX/PDF/PPTX/XLSX), frontend UI/UX and Tailwind performance, security guidance, code review/modernization/simplification, feature development, documentation updates, language-server workflows (Go/PHP/Rust/TypeScript), or YouTube transcript extraction. Select and load only the relevant sub-skill(s) from this repository.
---

# OdinLayer Skills Router

Use this file as a dispatcher. Do not solve tasks from this file alone.

## Routing Rules

1. Identify the primary task domain.
2. Load the matching sub-skill `SKILL.md`.
3. For cross-domain work, load at most 2-3 relevant sub-skills.
4. Prefer the most specific sub-skill over generic coding guidance.
5. If the request is ambiguous, ask one concise clarification question.

## Sub-Skill Map

- WordPress malware/security audits:
  - `wordpress-security-audit/SKILL.md`
- Office documents (DOCX, PDF, PPTX, XLSX):
  - `office-documents/SKILL.md`
- Frontend design, UI/UX, Tailwind, web vitals:
  - `frontend-design/SKILL.md`
- Security practices and secure implementation guidance:
  - `security-guidance/SKILL.md`
- Code quality and refactoring:
  - `code-review/SKILL.md`
  - `code-modernization/SKILL.md`
  - `code-simplifier/SKILL.md`
- Feature implementation:
  - `feature-dev/SKILL.md`
- Documentation updates:
  - `update-docs/SKILL.md`
- Language tooling / LSP workflows:
  - `gopls-lsp/SKILL.md`
  - `php-lsp/SKILL.md`
  - `rust-analyzer-lsp/SKILL.md`
  - `typescript-lsp/SKILL.md`
- YouTube transcript extraction and handling:
  - `youtube-transcript/SKILL.md`

## Execution Notes

- Keep outputs aligned with the selected sub-skill workflow.
- When multiple sub-skills are used, state which one drives each task segment.
- Do not invent non-existent sub-skills; use only directories present in this repository.
