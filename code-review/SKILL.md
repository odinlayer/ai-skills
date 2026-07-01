---
name: code-review
description: Pull-request and diff-focused code review workflow using parallel review lanes, confidence scoring, and false-positive filtering to produce concise, actionable findings.
license: MIT
metadata:
  repository: https://github.com/odinlayer/ai-skills/tree/main/code-review
  compatibility: Pi skill format; works with git-based review workflows.
---

# Code Review

Use this skill for code review of a branch, commit range, or pull request.

## Inputs

- Review target (PR number, branch, or commit range)
- Repository guidelines (`AGENTS.md`, style docs, local conventions)
- Risk context (critical paths, release urgency, compliance scope)

## Eligibility Check

- Skip closed/merged/draft work.
- Skip trivial generated changes with no behavior impact.
- Skip duplicate review if the same diff was already reviewed.

## Review Lanes

Run these lanes independently, then merge findings:

1. Guideline compliance:
   - Check adherence to repository conventions and explicit instructions.
2. Bug scan:
   - Focus on functional regressions and high-impact defects in changed code.
3. Historical context:
   - Use blame/history to catch repeated mistakes and known edge cases.
4. Local intent checks:
   - Review nearby comments, docs, and invariants in touched files.

## Confidence Scoring

Score each candidate issue:

- 0: false positive
- 25: weak signal
- 50: real but low impact
- 75: high confidence and important
- 100: confirmed defect with strong evidence

Default threshold: report only issues `>= 80`.

## Output Format

- List findings ordered by severity.
- Include file and line references.
- Explain impact and minimal fix direction.
- If no issues pass threshold, state that clearly.

## Exclusions

- Pre-existing issues outside changed lines
- Pure style nits not required by local guidance
- Problems that CI/lint/typecheck will deterministically catch
- Speculative issues without reproducible or code-backed evidence
