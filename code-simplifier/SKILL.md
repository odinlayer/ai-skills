---
name: code-simplifier
description: Refine recently changed code for clarity, consistency, and maintainability while preserving exact behavior, interfaces, and observable outputs.
license: MIT
metadata:
  repository: https://github.com/odinlayer/ai-skills/tree/main/code-simplifier
  compatibility: Pi skill format; language-agnostic refactoring guidance.
---

# Code Simplifier

Use this skill after implementation to improve readability without changing behavior.

## Scope

- Prioritize files touched in the current task.
- Expand scope only when dependencies require coordinated cleanup.

## Hard Constraints

- Preserve behavior and side effects.
- Preserve public interfaces unless explicitly approved.
- Preserve error semantics and return contracts.

## Simplification Pass

1. Remove accidental complexity:
   - Flatten unnecessary nesting.
   - Eliminate dead branches and duplicate logic.
2. Improve intent:
   - Use explicit names for variables/functions.
   - Extract helpers only when reuse or readability improves.
3. Normalize style:
   - Follow local conventions over personal preference.
4. Prefer clarity over brevity:
   - Avoid dense one-liners and nested ternaries.

## Verification

- Run available tests and linters.
- Re-check key paths if tests are missing.
- Report meaningful simplifications and any residual risks.
