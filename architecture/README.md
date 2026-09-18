# Ghost Sentinel — Architecture & Roadmap

This page documents Ghost Sentinel's actual current architecture and its planned direction. Anything marked **PLANNED** is not yet built. It's the direction this project is heading, documented honestly rather than implied as already in place.

## Current Architecture (built and verified)
- VMware Host-Only network, isolating the lab from the internet
- Kali Linux (attacker) — 192.168.112.130
- Metasploitable2 (target) — 192.168.112.128
- Windows host running Splunk Enterprise (indexer/search head) plus the Splunk Universal Forwarder
- Wireshark for packet-level traffic analysis
- One working Splunk alert (failed-logon threshold / brute force detection) with email notification, fully documented in `/investigations`

See `/homelab` and `/connection` for the full documented setup and verification steps behind this list.

## Planned Architecture
Everything below is a roadmap item, not a completed component.

### Identity & Cloud — PLANNED
- **Azure** tenant to host cloud-side identity and logging
- **Microsoft Entra ID** for user/group identity, conditional access concepts, and sign-in log ingestion into Splunk
- Goal: show how identity telemetry (cloud) correlates with endpoint and network telemetry (on-prem) during an investigation

### Endpoint Telemetry — PLANNED
- **Sysmon** deployed on Windows hosts for process creation, network connection, and file/registry telemetry
- Sysmon logs forwarded into Splunk alongside Windows Security events
- Goal: detect and investigate process-level attacker behavior (e.g. living-off-the-land binaries), not just authentication events

### Network Security Monitoring — PLANNED
- Network visibility beyond ad hoc Wireshark captures
- Goal: correlate network-layer evidence with endpoint and identity evidence within a single investigation

### Detection Engineering — PLANNED
- Additional Splunk alerts beyond the current brute-force detection: port scan detection, privilege escalation, PSExec/lateral movement, malware/AV triage (see `/playbooks`)
- Each new detection gets its own investigation write-up in `/investigations`

### MITRE ATT&CK Mapping — PLANNED
- Each investigation and detection mapped to relevant MITRE ATT&CK tactics/techniques (e.g. T1110 Brute Force) to show structured threat modeling rather than ad hoc detection

### Dashboards — PLANNED
- Splunk dashboards summarizing alert volume, investigation outcomes, and telemetry health across endpoint, network, and identity sources

### SOC Visuals — PLANNED
- A technical architecture diagram covering Azure, Entra ID, Splunk, Windows/Sysmon, Kali, Metasploitable2, and network/telemetry flows
- A realistic SOC analyst workstation/environment visual
- Visuals will be built to explain the actual architecture once it exists, not created purely for visual polish

## Why document this before it's built?
A credible portfolio shows both what's done and where it's going. Ghost Sentinel is built progressively — this roadmap exists so anyone reviewing the repo (a hiring manager, a mentor, future me) can see the honest state of the project: what's real, working evidence today, and what's the deliberate next step.

