# Playbooks

Alerting and escalation workflows for this homelab — the step-by-step response a SOC analyst would follow once an investigation confirms a specific alert type.

## Status
🟡 In progress — no playbooks written yet.

## Planned Playbooks
- Brute force / password spray detection and response
- Port scan detection and response
- Privilege escalation (unauthorized admin group change)
- PSExec / lateral movement detection (Event ID 7045)
- Malware detection (AV/Defender alert triage)

## Format (planned)
Each playbook will follow:
1. **Trigger** — the alert/condition that starts this playbook
2. **Initial Triage** — first checks an analyst should run
3. **Investigation Steps** — SPL queries and log sources to check
4. **Decision Criteria** — what separates benign from malicious for this alert type
5. **Escalation Path** — when and how to move from Tier 1 → Tier 2 → IR
6. **Documentation** — what to record for the incident report

