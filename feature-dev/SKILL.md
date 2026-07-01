---
name: feature-dev
description: End-to-end feature development workflow with structured discovery, codebase exploration, clarifying questions, architecture options, implementation, and quality review.
license: MIT
metadata:
  repository: https://github.com/odinlayer/ai-skills/tree/main/feature-dev
  compatibility: Pi skill format; repository-driven software feature delivery.
---

# Feature Development

Use this skill when implementing a non-trivial feature and you want design quality before coding speed.

## Workflow

1. Discovery:
   - Clarify problem, expected outcomes, constraints, and success criteria.
2. Codebase exploration:
   - Identify analogous features, extension points, and ownership boundaries.
3. Clarifying questions:
   - Resolve ambiguous behavior and edge cases before architecture.
4. Architecture options:
   - Produce at least two implementation approaches with trade-offs.
5. Implementation:
   - Execute the selected approach with scoped, convention-aligned edits.
6. Quality review:
   - Check correctness, simplicity, and adherence to repository standards.
7. Summary:
   - Report what changed, key decisions, and next steps.

## Mandatory Gates

- Do not start implementation until requirements and architecture are explicit.
- Do not merge with unresolved high-severity correctness issues.

## Quality Bar

- Changes match local patterns and contracts.
- Tests scale to risk of the change.
- New behavior is observable and documented in code where needed.
