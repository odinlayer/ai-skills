# wordpress-audit

Repository: https://github.com/odinlayer/ai-skills/tree/main/wordpress-audit

License: MIT

`wordpress-audit` is an end-to-end WordPress security audit workflow for
malware-infected sites on dedicated Ubuntu servers. It covers host forensics,
persistence checks, WordPress integrity review, IOC extraction, remediation
planning, and final client-ready reporting.

## Files

- `SKILL.md` - Skill instructions consumed by LiteLLM/Pi-compatible skill clients.
- `README.md` - Human-facing skill documentation and lineage notes.

## Scope

Use this skill only for authorized security work on WordPress environments. The
default mode is read-only evidence collection. Remediation and active
exploitation checks require explicit approval and an agreed test scope.

## Source Skill Lineage

This workflow consolidates procedures adapted from:

- analyzing-linux-audit-logs-for-intrusion
- analyzing-linux-system-artifacts
- analyzing-persistence-mechanisms-in-linux
- analyzing-web-server-logs-for-intrusion
- performing-linux-log-forensics-investigation
- collecting-volatile-evidence-from-compromised-host
- hunting-for-webshell-activity
- performing-malware-persistence-investigation
- conducting-malware-incident-response
- eradicating-malware-from-infected-systems
- performing-malware-ioc-extraction
- performing-malware-triage-with-yara
- analyzing-linux-elf-malware
- analyzing-linux-kernel-rootkits
- implementing-file-integrity-monitoring-with-aide
- deploying-osquery-for-endpoint-monitoring
- configuring-host-based-intrusion-detection
- hardening-linux-endpoint-with-cis-benchmark
- detecting-port-scanning-with-fail2ban
- performing-web-application-penetration-test
- performing-web-application-scanning-with-nikto
- performing-agentless-vulnerability-scanning
- conducting-network-penetration-test
- conducting-internal-network-penetration-test
- performing-external-network-penetration-test
