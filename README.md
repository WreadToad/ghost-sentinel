# Ghost Sentinel

Ghost Sentinel is a hands-on cybersecurity/SOC portfolio and homelab. It demonstrates practical, job-ready security operations skills — Splunk as a SIEM, Windows telemetry, and controlled attack simulation against Kali Linux and Metasploitable2 — through a real, documented investigation workflow rather than just a collection of tools.

## START HERE

New to this repo? In two minutes:

- **What this is:** a hands-on SOC home lab where I build a monitored environment, generate controlled security events, and investigate them the way an analyst would.
- **See the work:** open `/investigations` for documented investigations.
- **See the environment:** open `/homelab` and `/architecture`.

Everything here is an educational lab simulation, not professional or production experience.

## Security Workflow
Every investigation in this repo follows the same coherent pipeline, from raw signal to written conclusion:

**Alert → Telemetry → Investigation → Analysis → Detection → Response/Recommendation → Documentation**

## Structure
- `/architecture` — current vs. planned architecture and roadmap
- `/homelab` — environment and network architecture documentation
- `/connection` — connection setup, IP assignments, and forwarder verification
- `/investigation-template` — blank SOC-style investigation template
- `/investigations` — completed, documented investigations (classification, severity, escalation)
- `/playbooks` — alerting and escalation workflows (in progress)
- `/notes/cheat sheets` — quick-reference commands and filters

## Current Environment (built and verified today)
- **Virtualization:** VMware
- **Offensive tools:** Kali Linux, Metasploit
- **Target:** Metasploitable2
- **SIEM:** Splunk Enterprise
- **Traffic analysis:** Wireshark

See `/architecture` for the full target environment, including what's planned but not yet built.

## Status
🟢 Actively in progress

## Homelab Goals
Ghost Sentinel exists to demonstrate real, practical SOC analyst skills. The long-term goals are to:
- Build and maintain a realistic defensive cybersecurity homelab
- Demonstrate SIEM/SOC workflows using Splunk
- Collect and analyze Windows/Sysmon telemetry
- Practice network security monitoring and investigation
- Integrate Azure and Entra ID concepts
- Use Kali and Metasploitable2 only within the isolated lab for controlled testing
- Create realistic but safe security events, then investigate them from a defender's perspective
- Develop dashboards, detections, alerts, investigation workflows, and incident documentation
- Demonstrate how endpoint, identity, network, cloud, and SIEM telemetry work together
- Document the architecture and evolution of the environment
- Produce professional screenshots and evidence suitable for a cybersecurity portfolio

## Recommended Viewing Order
1. Read `/architecture` for the big-picture plan — what's built vs. what's planned
2. Read `/homelab` to understand the current environment
3. Review `/connection` to see how the lab was built and verified
4. Explore `/investigations` to see SOC-style analysis
5. Check `/playbooks` to understand alerting workflows (in progress)
6. Use `/notes/cheat sheets` for commands and quick references
