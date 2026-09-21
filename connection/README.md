# Lab Connection Overview

This document explains how the virtual machines and Splunk connect in the lab: network mode, data flow, and how ingestion was verified. Private lab IP addresses are intentionally omitted.

## Network Mode
- **VMware network:** NAT with private, lab-only addressing
- **Purpose:** Lets the lab machines communicate with each other in a contained virtual environment.

## Machines
- **Kali Linux (attacker):** offensive tooling; used for planned attack simulations
- **Metasploitable2 (target):** intentionally vulnerable target; used for planned attack simulations
- **Windows Server 2022 (SIEM VM):** runs Splunk Enterprise 10.4.2 and is the source of the Windows telemetry

## Current Data Flow
1. Windows Security, System and Sysmon (Operational) event logs on the SIEM VM are collected by local Splunk inputs (no separate forwarder).
2. Events are indexed into a dedicated `homelab` index.
3. Searches and alerts run in Splunk against that index.

## Verification
- Ingestion health checked by counting events per sourcetype in `index=homelab` and confirming recent timestamps for Security, System and Sysmon.
- Baseline of account, logon and process activity documented before running the privilege-escalation scenario (see `/investigations`).

## Not Built Yet
- Forwarding logs from Kali and Metasploitable2 into Splunk
- Sysmon on additional hosts, with forwarding into Splunk
- Wireshark-based network captures tied into investigations

## Purpose
This overview confirms the machines and telemetry pipeline are in place before running attacks or investigations.
