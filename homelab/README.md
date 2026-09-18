# WreadToad Home Lab

This homelab is designed to simulate real SOC workflows, including
malicious activity generation, log ingestion, alerting, and investigation.
It uses VMware for virtualization, Kali Linux and Metasploit for offensive
security testing, and Splunk Enterprise as the SIEM.

## Structure
- `/notes` — quick-reference commands and filters
- `/investigations` — documented findings from lab activity, including
  classification, severity, and escalation reasoning
- `/playbooks` — alerting and escalation workflows
- `/homelab` — environment and architecture documentation

## Environment
- **Virtualization:** VMware
- **Attacker:** Kali Linux (Nmap, Hydra, Metasploit)
- **Target:** Metasploitable2 (vulnerable Linux VM)
- **Log Source:** Windows Host (Splunk Universal Forwarder)
- **SIEM:** Splunk Enterprise
- **Traffic Analysis:** Wireshark

## Network Architecture
- **VMware Network Mode:** Host-Only / Custom
- **Kali:** 192.168.112.130
- **Metasploitable2:** 192.168.112.128
- **Windows Host → Splunk:** Localhost → port 9997

## Traffic Flow
1. Kali performs scans or attacks against Metasploitable2.
2. Metasploitable2 responds, generating network traffic.
3. Windows logs suspicious behavior (failed logons, process creation, etc.).
4. Splunk Forwarder sends logs to Splunk.
5. Splunk indexes logs for alerting and investigation.

## Status
🟢 Actively in progress

