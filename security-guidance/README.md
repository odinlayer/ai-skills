# security-guidance

Repository: https://github.com/odinlayer/ai-skills/tree/main/security-guidance

License: MIT

`security-guidance` is a secure-coding review skill for changed code, focused
on high-risk vulnerability classes, evidence-based findings, and prioritized
remediation guidance.

## Files

- `SKILL.md` - Pi-compatible security review workflow.
- `README.md` - Human-facing documentation and source lineage.

## Features

- Diff-based secure code review before merge/release.
- Pattern and data-flow analysis for high-risk vulnerability classes.
- API/auth/session/token review checks with tenant/authorization focus.
- Dependency and supply-chain risk signals (including dependency confusion indicators).
- Lightweight risk triage and standardized remediation-oriented output.

## Source Lineage

- Upstream plugin: `security-guidance`
- Source: https://github.com/anthropics/claude-plugins-official/tree/main/plugins/security-guidance
- Additional enrichment references:
  - https://github.com/mukul975/Anthropic-Cybersecurity-Skills
