---
name: security-guidance
description: Secure coding review workflow for changed code, combining pattern checks, data-flow analysis, and severity-based remediation guidance for common application vulnerabilities.
license: MIT
metadata:
  repository: https://github.com/odinlayer/ai-skills/tree/main/security-guidance
  compatibility: Pi skill format; model-agnostic security review guidance.
---

# Security Guidance

Use this skill when reviewing code changes for security risk before merge or release.

## Inputs

- Diff or changed-file list
- Runtime surface (web, API, workers, CLI, infra scripts)
- Threat context (public endpoints, auth boundaries, sensitive data flows)

## Review Workflow

1. Pattern scan:
   - Flag risky constructs (injection sinks, unsafe deserialization, raw HTML insertion, weak auth checks, secret literals).
2. Data-flow tracing:
   - Trace untrusted input to sink points across files.
3. Authorization checks:
   - Verify resource-level access control and tenant boundaries.
4. Secret and config checks:
   - Detect hardcoded credentials, weak defaults, and missing env separation.
5. Dependency and platform checks:
   - Highlight obvious vulnerable or outdated critical dependencies.

## Vulnerability Classes

- Injection (SQL/command/template)
- XSS and output encoding gaps
- SSRF and unsafe URL fetch patterns
- Path traversal and file write/read misuse
- Broken auth/session checks
- IDOR and missing object-level authorization
- Unsafe crypto or token handling

## Severity and Output

- Rate findings as Critical/High/Medium/Low with evidence.
- Provide file/line references and exploit path in plain language.
- Include minimal fix direction for each finding.
- If no actionable issues are found, state residual risk and remaining blind spots.

## Boundaries

- Do not claim full security assurance from static review alone.
- Treat this as one layer alongside tests, dependency scans, and manual review.
