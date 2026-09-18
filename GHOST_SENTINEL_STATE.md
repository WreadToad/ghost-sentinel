# GHOST SENTINEL — PROJECT STATE
*This is the permanent source of truth for Ghost Sentinel. Read this file first whenever Darren says "continue Ghost Sentinel." Never assume Step 1 — check here first.*

## CURRENT STATUS
- Overall project phase: **Day 1** (per Ghost-Sentinel-Master-Plan.md Section 12 sequence: Environment Audit -> GitHub Connection -> Repository Audit -> Security Check -> Organization -> First Training Task)
- Exact current step: Steps 1-2 (Environment Audit, GitHub Connection) are done. **Step 3 (Repository audit + mandatory security/privacy check) is next**, not yet performed in depth.
- Current objective: Audit the real contents of the ghost-sentinel repo's folders against the Section 11 security/privacy checklist, then move into the first hands-on scenario
- Status: **IN PROGRESS**

## LAST COMPLETED ACTION
- Action: Independently re-verified Kali <-> Metasploitable2 network connectivity (nmap ping sweep across 192.168.112.0/24, then a full port scan against 192.168.112.128)
- Result: Confirmed reachable, sub-3ms latency, Metasploitable2 positively fingerprinted by its full 22-port signature (ftp/ssh/telnet/smtp/http/samba/mysql/postgresql/vnc/X11/irc/etc.)
- Files/components changed: None (verification only) - this reproduced, and matches exactly, the networking confirmation already logged in Home Lab's VM-Move-Recovery-Progress.md from earlier the same day

## CURRENT ENVIRONMENT
- **Host system:** Windows laptop (Home Lab-owned) - see HOMELAB_STATE.md for full infrastructure detail
- **Virtual machines:** Kali + Metasploitable2 confirmed working and networked (Home Lab-owned, used here per Section 13)
- **Splunk:** Browser-based Splunk Enterprise. Trial expires ~Sept 28, 2026. Full config already backed up (Splunk-Backup-2026-09-18/ in the vault) so a reinstall won't lose the Brute Force Detection alert or course lookup tables.
- **Windows:** Confirmed to mean the host laptop itself, not a separate VM
- **Sysmon:** Installed and running (52,000+ events). Gap: its operational log channel isn't yet forwarded into Splunk (index=homelab currently only gets WinEventLog:Security/System) - documented, not fixed yet.
- **Kali:** Working, IP 192.168.112.130
- **Metasploitable2:** Working, IP 192.168.112.128
- **Azure / Entra ID:** Not started. Section 19 of the master plan - audit-first pass (does a tenant exist, free-tier quota limits) hasn't happened yet.
- **GitHub:** **Connected.** Real repo is github.com/WreadToad/ghost-sentinel (NOT splunk-power-Darren - that name in the master plan doc was stale/wrong). 42 commits already in. This session's cloud workspace has a scoped/sandboxed GitHub token that can't push to this repo directly - this state file is being delivered to the repo via Darren's own authenticated browser session instead.
- **Networking:** Kali and Metasploitable2 confirmed on the same VMware NAT segment, mutually reachable
- **Other infrastructure:** VMware Workstation Pro confirmed as the real hypervisor (corrects the master plan's earlier VirtualBox assumption)

## WHAT IS WORKING
- Full VM inventory audited and confirmed (see HOMELAB_STATE.md for detail)
- Splunk access confirmed, config backed up ahead of trial expiration
- Sysmon confirmed running
- Kali <-> Metasploitable2 connectivity confirmed twice independently
- GitHub repo confirmed connected with real structure: /architecture, /connection, /homelab, /investigation-template, /investigations, /notes/cheat sheets, /playbooks, README.md

## WHAT IS BROKEN OR BLOCKED
- Sysmon's operational log isn't forwarded into Splunk yet (data pipeline gap, documented in Home Lab audit)
- Splunk trial has a hard deadline (~Sept 28, 2026) - port scan sim, privilege escalation sim, and the lockout-pattern alert should be finished before then per the scenario checklist's own sequencing note
- This cloud workspace can't get unscoped GitHub API/OAuth access (sandboxed to pre-approved repos only) - workaround is delivering files via Darren's browser instead of git push from here
- Repository audit (Day 1 Step 3) and the mandatory Section 11 security/privacy check have NOT been performed yet - don't assume the repo's existing content is already sanitized

## IMPORTANT DECISIONS
- VMware Workstation Pro is the real hypervisor (not VirtualBox) - corrects Master Plan Section 13/18's original assumption
- The GitHub repo is named ghost-sentinel, not splunk-power-Darren - corrects Master Plan Section 11/12's original assumption
- GitHub connection was already completed prior to this file's creation - do not re-run the device-login flow assuming it's unconnected
- As of 2026-09-18: **Home Lab** (Kali, Metasploitable2, the host, Sysmon, Splunk infrastructure) is documented as its own distinct-but-integrated project, separate from Ghost Sentinel. They are NOT isolated - Section 13 below documents exactly how they connect. See HOMELAB_STATE.md for that project's own state.
- Sections 18-24 of the master plan are flagged in the doc itself as a reconstructed draft from a lost context reset; Section 24's "15-phase build order" is still a placeholder and hasn't been reconciled with the Section 17 Day 1 checklist

## DO NOT REDO
- Day 1 Environment Audit (VM inventory, Splunk/Sysmon/Windows/networking confirmation) - complete, verified twice
- VirtualBox-vs-VMware investigation - resolved, VMware is the answer
- GitHub connection setup - already done, repo already exists with real history
- Kali <-> Metasploitable2 connectivity check - verified twice, don't re-run as if unconfirmed

## PROJECT PROGRESS
1. Day 1 Step 1 (Environment Audit) completed - VM inventory, Splunk/Sysmon/Windows/networking all confirmed
2. Day 1 Step 2 (GitHub Connection) completed - ghost-sentinel repo confirmed live with 42 commits and real folder structure
3. Splunk config backed up ahead of trial expiration
4. Kali <-> Metasploitable2 connectivity independently reconfirmed
5. 2026-09-18: Home Lab formally documented as a distinct-but-integrated project (Section 13), and this permanent state-tracking system (this file + HOMELAB_STATE.md) established so future sessions stop restarting from Step 1

## NEXT ACTION
**NEXT ACTION:** Perform Day 1 Step 3 - open the actual /investigations, /architecture, and /playbooks folders in the ghost-sentinel repo, see what's genuinely documented vs. a stub, and run the mandatory Section 11 security/privacy check on existing content before adding anything new. After that, move to the first hands-on scenario - priority per the Home Lab Scenario Checklist is the port scan simulation or privilege escalation simulation (both Splunk-trial-time-sensitive).

## INTEGRATIONS WITH HOME LAB (Section 13)
- **Kali + Metasploitable2** - Home Lab-owned infrastructure; Ghost Sentinel's attack-simulation scenarios (brute force, port scan, privilege escalation) run directly against them
- **Host laptop + Sysmon** - Home Lab-owned; supplies the telemetry Ghost Sentinel's Splunk SIEM work depends on
- **Splunk** - runs on Home Lab infrastructure but is Ghost Sentinel's core analysis tool; a reinstall or reconfig touches both projects
- **Windows Server 2022 (2)** - Home Lab-owned; earmarked as the future Domain Controller for Ghost Sentinel's planned Active Directory lab (BloodHound/Mimikatz/PSExec)
- **What crosses between them:** log/telemetry data (Sysmon, Windows Security events) flows from Home Lab into Splunk for Ghost Sentinel's investigations; no Ghost Sentinel-owned data flows back into Home Lab
- **Dependency/config warning:** Don't let Ghost Sentinel work reinstall Splunk, delete/rebuild VMs, or change NAT networking without checking HOMELAB_STATE.md - those changes affect Home Lab's own stability

## SESSION HANDOFF
- What we accomplished: Reconciled two stale assumptions in the master plan (VMware not VirtualBox, ghost-sentinel not splunk-power-Darren), reconfirmed Kali<->Metasploitable2 connectivity, formally separated Home Lab from Ghost Sentinel as distinct-but-integrated projects, and created this permanent state-tracking file plus HOMELAB_STATE.md
- Files modified: This file created; HOMELAB_STATE.md created in the Home Lab folder (superseding a typo'd HOMELAND_STATE.md draft that should be deleted by Darren)
- Configuration changes: None to actual lab/Splunk/VM config this session
- Errors encountered: This cloud workspace's GitHub access is sandboxed to pre-approved repos and can't do a raw OAuth device login or unscoped API push - resolved by delivering this file through Darren's own browser session instead
- What remains unfinished: Day 1 Step 3 (repo audit + security/privacy check) not yet started; Sysmon->Splunk forwarding gap not yet fixed
- Exact point where we stopped: Committing this file to the GitHub repo via Darren's browser
- Exact next action: Begin Day 1 Step 3 (repository audit + security/privacy check)
