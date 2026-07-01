---
name: wordpress-audit
description: End-to-end WordPress security audit workflow for malware-infected sites on dedicated Ubuntu servers, including host forensics, persistence checks, WordPress integrity review, and final client-ready reporting.
license: MIT
metadata:
  repository: https://github.com/odinlayer/ai-skills/tree/main/wordpress-audit
  compatibility: Pi skill format; intended for Linux shell environments with WordPress on dedicated Ubuntu servers and authorized security assessment scope.
---

# WordPress Audit (Ubuntu, Post-Infection)

Use this skill to run a structured security audit for a WordPress website hosted on a dedicated Ubuntu server after suspected or confirmed malware infection.

## When to Use

- WordPress website compromise investigation
- Malware cleanup validation and post-incident audit
- Ubuntu server security review with WordPress scope
- Client-requested WordPress-focused penetration/security assessment

## Do Not Use

- Without explicit authorization from the site/system owner
- For uncontrolled exploitation beyond agreed test scope
- For destructive or service-impacting actions unless explicitly approved

## Operating Mode

Default mode is **read-only evidence collection**.  
Only perform remediation steps when the user explicitly confirms remediation mode.

## Required Inputs

Collect these before starting:

- Target domain(s) and WordPress path(s)
- Server access details (SSH/sudo constraints)
- Approved scope (prod/staging, internal/external)
- Time window for testing and impact constraints
- Incident context (known IOCs, suspected initial access, known symptoms)

If any required input is missing, stop and request it before deep testing.

## Audit Workflow

Follow phases in order. Keep evidence and findings mapped to each phase.

### 1) Scope and Safety Gate

1. Confirm written authorization and permitted test actions.
2. Confirm whether this is investigation-only or includes remediation.
3. Capture current date/time, timezone, and hostname for all evidence.
4. Create evidence workspace and command log.

### 2) Host Compromise Triage (Ubuntu)

Collect and review:

- OS/kernel/version, uptime, last reboot
- Logged-in users, sudoers, new/unknown accounts
- Running services/processes and parent-child anomalies
- Listening ports and external network connections
- Auth logs (`/var/log/auth.log*`) for brute force and suspicious logins
- Shell histories and suspicious binaries in `/tmp`, `/var/tmp`, `/dev/shm`

### 3) Persistence and Backdoor Hunt

Inspect persistence vectors:

- System/user cron: `/etc/crontab`, `/etc/cron.*`, `/var/spool/cron/*`
- systemd units/timers (enabled + recently changed)
- SSH authorized keys for all privileged accounts
- init scripts, profile files, rc.local, LD_PRELOAD indicators
- Webshell launchers and hidden startup scripts

Flag each as: `benign`, `suspicious`, `confirmed malicious`.

### 4) WordPress Integrity and Malware Review

Check WordPress-specific compromise indicators:

- Core file integrity and unexpected core modifications
- Suspicious PHP in uploads/themes/plugins/mu-plugins
- Obfuscation patterns (`base64_decode`, `eval`, `gzinflate`, long hex blobs)
- Rogue admin users and authentication changes
- Dangerous plugin/theme additions or tampering
- `.htaccess` abuse, redirect injectors, hidden loaders
- `wp-config.php` hardcoded backdoors or leaked creds
- Webroot permissions/ownership drift

### 5) Web and App Security Assessment

Perform non-disruptive security checks first:

- Baseline exposure scan (headers, TLS, known risky endpoints)
- Auth and access-control weaknesses
- Directory traversal and unsafe file exposure checks
- Plugin/theme vulnerability posture (version and risk review)
- External attack surface (admin interfaces, xmlrpc, debug artifacts)

Run active exploitation checks only if in approved pentest mode.

### 6) IOC Extraction and Correlation

Extract and normalize:

- File hashes, suspicious paths, process names, domains/IPs, URLs
- Malicious cron/systemd entries
- Webshell signatures and C2 indicators

Correlate with timeline:

- Initial access (best-known)
- Execution and persistence
- Lateral actions / data access
- Outbound communication

### 7) Containment and Remediation Plan

If remediation mode is approved, propose and/or execute in controlled order:

1. Contain active persistence and webshell execution
2. Rotate credentials/keys/tokens
3. Restore trusted WordPress core/plugins/themes
4. Patch and harden host + WordPress
5. Re-scan to verify clean state

Never delete evidence before chain-of-custody requirements are met.

### 8) Final Report Production

Produce a client-ready report with:

- Executive summary
- Scope and methodology
- Incident and compromise timeline
- Findings by severity (Critical/High/Medium/Low)
- Evidence references for every finding
- Confirmed malware/persistence details
- Risk impact and business implications
- Remediation actions (done vs pending)
- Hardening recommendations and follow-up plan

## Report Format

Use this exact section structure:

1. Executive Summary
2. Engagement Scope and Constraints
3. Environment Overview (WordPress + Ubuntu)
4. Key Findings (by severity)
5. Malware and Persistence Analysis
6. WordPress-Specific Security Findings
7. Server-Side Security Findings
8. Indicators of Compromise
9. Timeline of Activity
10. Remediation Completed
11. Remediation Required
12. Hardening Checklist
13. Appendix (commands, evidence paths, hashes)

## Quality Bar

- No unverified claims
- Each finding must include evidence path or command output reference
- Separate hypothesis vs confirmed fact
- Clearly mark residual risk after remediation
