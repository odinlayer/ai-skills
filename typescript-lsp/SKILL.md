---
name: typescript-lsp
description: Configure and use TypeScript language-server workflows for TypeScript and JavaScript projects, including diagnostics, symbol navigation, and safer refactors.
license: MIT
metadata:
  repository: https://github.com/odinlayer/ai-skills/tree/main/typescript-lsp
  compatibility: Pi skill format; Node-based TypeScript or JavaScript repositories.
---

# TypeScript LSP

Use this skill for `.ts`, `.tsx`, `.js`, `.jsx`, `.mts`, `.cts`, `.mjs`, and `.cjs` projects when you need language-intelligence support.

## Setup

Install globally:

- `npm install -g typescript-language-server typescript`
  or
- `yarn global add typescript-language-server typescript`

Verify:

- `typescript-language-server --version`
- `tsc --version`

## Usage Guidance

- Use LSP diagnostics and symbol operations before broad refactors.
- Confirm typing and build state after edits:
  - `tsc --noEmit` (or project equivalent)
  - project test suite
  - project lint command

## Fallback

If LSP is unavailable, prioritize deterministic checks (`tsc`, tests, lint)
before merge.
