---
name: security-guidance
description: Secure coding review workflow for changed code before merge/release, combining pattern checks, data-flow analysis, API/auth/dependency checks, and severity-based remediation guidance for common application vulnerabilities.
license: MIT
metadata:
  repository: https://github.com/odinlayer/ai-skills/tree/main/security-guidance
  compatibility: Pi skill format; model-agnostic security review guidance.
---

# Security Guidance

Use this skill when reviewing code changes for security risk before merge or release.
Keep focus on secure code review, not full penetration testing or incident response.

## Inputs

- Diff or changed-file list
- Runtime surface (web, API, workers, CLI, infra scripts)
- Threat context (public endpoints, auth boundaries, sensitive data flows)
- Asset criticality and deployment exposure (internet-facing vs internal)

## Review Workflow

1. Pattern scan:
   - Flag risky constructs (injection sinks, unsafe deserialization, raw HTML insertion, weak auth checks, secret literals).
2. Data-flow tracing:
   - Trace untrusted input to sink points across files and trust boundaries.
3. Authorization and tenant checks:
   - Verify object-level and function-level access controls.
   - Confirm tenant isolation and ownership checks on resource reads/writes.
4. Auth/session/token checks:
   - Validate token/session handling (`exp`, `nbf`, `iss`, `aud`, signature expectations).
   - Check privilege claims, role checks, session invalidation, and logout/revocation behavior.
5. API-specific checks:
   - Broken object level authorization (BOLA/IDOR)
   - Broken function level authorization (BFLA)
   - Mass assignment / over-posting
   - Excessive data exposure
   - Missing or weak rate limiting on sensitive flows
   - Unsafe outbound calls / URL fetch handling (SSRF risk)
6. Secret, config, and dependency checks:
   - Detect hardcoded credentials, weak defaults, and missing env separation.
   - Flag critical outdated dependencies and known exploited vulnerabilities when obvious.
   - Note supply-chain risk indicators (dependency confusion patterns, unsafe install scripts, unpinned critical deps).
7. Triage and report:
   - Prioritize by exploitability, impact, exposure, and asset criticality.
   - Produce actionable fixes and verification guidance.

## Vulnerability Classes

- Injection (SQL/command/template)
- XSS and output encoding gaps
- SSRF and unsafe URL fetch patterns
- Path traversal and file write/read misuse
- Broken auth/session checks
- IDOR and missing object-level authorization
- Broken function-level authorization
- Mass assignment and excessive data exposure
- Rate limiting gaps in sensitive workflows
- Unsafe crypto or token handling
- Dependency/supply-chain exposure (including dependency confusion indicators)

## Risk Triage

Use a lightweight weighted view:

- Exploitability: `Low/Med/High`
- Technical impact: `Low/Med/High`
- Exposure: `internal/authenticated/public`
- Asset criticality: `Low/Med/High`

Default severity guidance:

- Critical: easy exploitation + high impact on public/high-criticality surface
- High: auth bypass, tenant breakout, sensitive data exposure, or strong exploit path
- Medium: meaningful weakness requiring preconditions or limited blast radius
- Low: defense-in-depth issues with minimal direct impact

## Output Format

For each finding include:

- `Severity` and `Confidence`
- `Evidence` (file/line + relevant code path)
- `Attack path` (how issue can be reached)
- `Fix direction` (minimal, concrete change)
- `Verification` (how to validate fix)
- `Owner/SLA suggestion` (based on severity)

If no actionable issues are found:

- State residual risk and blind spots
- List what was not assessed (dynamic runtime behavior, infra controls, third-party services)

## Boundaries

- Do not claim full security assurance from static review alone.
- Treat this as one layer alongside tests, dependency scans, and manual review.
- Do not perform active exploitation unless explicitly requested and authorized.
