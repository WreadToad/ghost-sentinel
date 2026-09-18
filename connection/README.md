# Lab Connection Overview

This document explains how each virtual machine and service in the homelab
connects to one another, including network mode, IP assignments, Splunk
forwarding, and traffic flow.

## Network Mode
- **VMware Network:** Host-Only (Custom)
- **Purpose:** Provides an isolated environment where Kali, Metasploitable2,
  and Splunk can communicate without touching the external internet.

## IP Assignments
- **Kali Linux (Attacker):** 192.168.112.130  
  - Verified via `ip a`  
  - Successful ICMP ping to Metasploitable2

- **Metasploitable2 (Target):** 192.168.112.128  
  - Responds to ICMP  
  - Used for attack simulation

- **Windows Host (Splunk Forwarder):** Localhost → Splunk Indexer  
  - Forwarder service running  
  - Sends logs to Splunk on port **9997**

## Connectivity Verification

### Kali → Metasploitable2
- Verified via ICMP ping  
- Screenshot included in investigations  
- Confirms both machines share the same network segment

### Splunk Forwarder → Splunk Indexer
- Forwarder service is **Running**  
- Startup type: **Automatic**  
- Logs successfully sent to Splunk  
- Verified via:
  - `index=_internal source=*metrics.log* group=tcpin_connections`
  - Shows active TCP ingestion on port 9997

### Windows → Splunk (homelab index)
- Windows Security logs successfully ingested  
- Verified via:
  - `index=homelab`  
  - EventCode 5379 and other security events

## Traffic Flow
1. Kali performs scans or attacks against Metasploitable2.
2. Metasploitable2 responds, generating network traffic.
3. Wireshark captures packets for analysis.
4. Windows Forwarder sends logs to Splunk.
5. Splunk indexes logs for investigation and correlation.

## Purpose
This connection overview ensures all machines and services are properly
networked before running investigations, attacks, or log ingestion workflows.
