---
name: php-lsp
description: Configure and use PHP language-server workflows (Intelephense) for symbol navigation, diagnostics, and safe refactoring in PHP repositories.
license: MIT
metadata:
  repository: https://github.com/odinlayer/ai-skills/tree/main/php-lsp
  compatibility: Pi skill format; PHP projects with Node/npm available.
---

# PHP LSP

Use this skill for `.php` projects when you need language-aware navigation and diagnostics.

## Setup

Install Intelephense globally:

- `npm install -g intelephense`
  or
- `yarn global add intelephense`

Verify installation:

- `intelephense --version`

## Usage Guidance

- Use language-server diagnostics before broad manual refactors.
- Resolve symbol definitions and references through LSP-aware tooling.
- Re-run project tests and static checks after edits.

## Fallback

If LSP is unavailable, rely on repository checks (for example PHPUnit, Psalm,
PHPStan, or project-specific CI commands).
