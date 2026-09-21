# Ghost Sentinel Home Lab

This home lab simulates real SOC workflows: generating controlled security events, collecting and indexing the logs, searching and alerting on them, and investigating the results. It is an educational lab, not a production environment.

## Environment
- **Virtualization:** VMware Workstation Pro on a Windows laptop
- **SIEM VM:** Windows Server 2022 running Splunk Enterprise 10.4.2
- **Attacker:** Kali Linux
- **Target:** Metasploitable2 (intentionally vulnerable Linux VM)
- **Traffic analysis:** Wireshark
- **Network:** VMware NAT segment, private lab-only addressing

## Current data flow
1. Windows Security, System, and Sysmon Operational events are generated on the SIEM VM.
2. Splunk collects them through local event log inputs into a dedicated index.
3. Searches and alerts run against that index for investigation.

## Not built yet
- Kali and Metasploitable2 activity is not yet forwarded into Splunk.
- The host laptop's Sysmon log is not yet forwarded.
- Azure and Entra ID are planned, not built (see /architecture).

## Investigations
Completed and in-progress investigations are documented in /investigations.

## Status
Actively in progress.
