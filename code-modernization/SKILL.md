---
name: code-modernization
description: Structured modernization workflow for legacy codebases, including readiness checks, discovery artifacts, business-rule extraction, modernization planning, rewrite or version-uplift execution, and validation by behavior-equivalence tests.
license: MIT
metadata:
  repository: https://github.com/odinlayer/ai-skills/tree/main/code-modernization
  compatibility: Pi skill format; model-agnostic workflow for local repositories.
---

# Code Modernization

Use this skill when modernizing a legacy codebase and you need a repeatable workflow from assessment to validated delivery.

## Required Inputs

- System path and target scope (full system or module)
- Target stack or target version
- Risk constraints (downtime tolerance, compliance boundaries)
- Validation requirements (equivalence, contracts, performance)

## Operating Rules

- Keep the legacy tree as baseline evidence.
- Prefer writing artifacts to `analysis/<system>/`.
- Write modernization output to `modernized/<system>/`.
- Do not claim behavioral parity without executable evidence.

## Workflow

1. Preflight readiness:
   - Confirm source completeness, toolchain, and test harness feasibility.
2. Assessment:
   - Inventory language mix, complexity hotspots, dependency age, and risk.
3. Architecture map:
   - Build domain and dependency maps, entry points, and critical flows.
4. Business-rule extraction:
   - Convert implicit logic into rule cards with source citations.
5. Modernization brief:
   - Define phased plan, architecture target, and approval checkpoints.
6. Execute one path:
   - `transform`: cross-stack rewrite of selected modules.
   - `reimagine`: greenfield rebuild from extracted behavior and constraints.
   - `uplift`: same-stack version migration with minimal diffs.
7. Security hardening:
   - Review injection, auth, secrets, dependency, and config risks.
8. Status and staleness:
   - Track artifact freshness and recommend next command.

## Validation Standard

- Run characterization tests before large edits.
- Re-run tests after changes and report pass/fail deltas.
- Mark unresolved ambiguity as a blocker, not as an assumption.
- Separate confirmed findings from hypotheses.
