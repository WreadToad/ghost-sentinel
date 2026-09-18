# GHOST SENTINEL — PROJECT STATE
*This is the permanent source of truth for Ghost Sentinel. Read this file first whenever Darren says "continue Ghost Sentinel." Never assume Step 1 — check here first.*

## CURRENT STATUS
- Overall project phase: **Day 1** (per Ghost-Sentinel-Master-Plan.md Section 12 sequence: Environment Audit -> GitHub Connection -> Repository Audit -> Security Check -> Organization -> First Training Task)
- Exact current step: Steps 1-3 are done (Environment Audit, GitHub Connection, Repository Audit + Security/Privacy Check). **Choosing the first hands-on scenario is next.**
- Current objective: Pick and run the first hands-on attack-simulation scenario - port scan simulation or privilege escalation simulation (both flagged as trial-deadline priority)
- Status: **IN PROGRESS**

## LAST COMPLETED ACTION
- Action: Repository audit + mandatory Section 11 security/privacy check on the ghost-sentinel repo
- Result: Confirmed real content in README.md, architecture/README.md, connection/README.md, homelab/README.md, and investigations/investigation-01-failed-logon-threshold.md (the completed EventCode 4625 self-test investigation). Confirmed stubs/placeholders in investigation-template, playbooks, and notes/cheat sheets (none written yet). Security check found one item (hostname WIN-HOMELAB01 in investigation-01) - Darren confirmed it's already a fake/fictionalized hostname, not real, so **no redaction needed**. No passwords, API keys, personal info, or real company data found anywhere in the repo.
- Files/components changed: None (audit only)

## CURRENT ENVIRONMENT
- **Host system:** Windows laptop (Home Lab-owned) - see HOMELAB_STATE.md for full infrastructure detail
- **Virtual machines:** Kali + Metasploitable2 confirmed working and networked (Home Lab-owned, used here per Section 13)
- **Splunk:** Browser-based Splunk Enterprise. Trial expires ~Sept 28, 2026. Full config already backed up (Splunk-Backup-2026-09-18/ in the vault).
- **Windows:** Confirmed to mean the host laptop itself, not a separate VM
- **Sysmon:** Installed and running (52,000+ events). Gap: operational log channel not yet forwarded into Splunk.
- **Kali:** Working, IP 192.168.112.130
- **Metasploitable2:** Working, IP 192.168.112.128
- **Azure / Entra ID:** Not started (Section 19) - planned, not built, per architecture/README.md
- **GitHub:** Connected. Repo is github.com/WreadToad/ghost-sentinel, 43 commits (including this state file). Cloud workspace GitHub access is sandboxed to pre-approved repos, so this file is maintained via Darren's own browser session.
- **Networking:** Kali and Metasploitable2 confirmed on the same VMware NAT/Host-Only segment, mutually reachable
- **Other infrastructure:** VMware Workstation Pro confirmed as the real hypervisor

## WHAT IS WORKING
- Full VM inventory audited and confirmed (see HOMELAB_STATE.md)
- Splunk access confirmed, config backed up ahead of trial expiration
- Sysmon confirmed running
- Kali <-> Metasploitable2 connectivity confirmed twice independently
- GitHub repo audited: real, honest documentation (built-vs-planned clearly separated), one complete investigation, security check passed clean

## WHAT IS BROKEN OR BLOCKED
- Sysmon's operational log isn't forwarded into Splunk yet (documented gap, not fixed)
- Splunk trial deadline ~Sept 28, 2026 - port scan sim, privilege escalation sim, and lockout-pattern alert should be finished before then
- Repo's playbooks and cheat-sheet notes are still empty stubs (expected at this stage, not a problem)
- Cloud workspace can't get unscoped GitHub API/OAuth access - working around it via Darren's browser session for any repo writes

## IMPORTANT DECISIONS
- VMware Workstation Pro is the real hypervisor (not VirtualBox)
- The GitHub repo is named ghost-sentinel, not splunk-power-Darren
- GitHub connection was already completed prior to this state-tracking system - don't re-run device-login assuming it's unconnected
- 2026-09-18: Home Lab (Kali, Metasploitable2, host, Sysmon, Splunk infrastructure) is documented as its own distinct-but-integrated project, separate from Ghost Sentinel - see HOMELAB_STATE.md
- Hostnames/IPs used in investigation write-ups (e.g. WIN-HOMELAB01) are intentionally fictionalized per Darren's confirmation - this satisfies the Section 11 security check for that content
- Sections 18-24 of the master plan are a reconstructed draft; Section 24's 15-phase build order is still a placeholder

## DO NOT REDO
- Day 1 Environment Audit - complete, verified twice
- VirtualBox-vs-VMware investigation - resolved, VMware is the answer
- GitHub connection setup - already done
- Kali <-> Metasploitable2 connectivity check - verified twice
- Repository audit + security/privacy check - complete, passed clean (fake hostname confirmed intentional)

## PROJECT PROGRESS
1. Day 1 Step 1 (Environment Audit) completed
2. Day 1 Step 2 (GitHub Connection) completed - ghost-sentinel repo confirmed live
3. Splunk config backed up ahead of trial expiration
4. Kali <-> Metasploitable2 connectivity independently reconfirmed
5. 2026-09-18: Home Lab formally documented as distinct-but-integrated (Section 13); this state-tracking system established
6. Day 1 Step 3 (Repository audit + security/privacy check) completed - repo content confirmed real and clean

## NEXT ACTION
**NEXT ACTION:** Pick the first hands-on attack-simulation scenario from the Home Lab Scenario Checklist and run it - options are the **port scan simulation** (Nmap from Kali against Metasploitable2, analyze resulting traffic/logs) or the **privilege escalation simulation** (add a test user to an admin group, investigate the resulting event). Both are flagged trial-deadline priority. Waiting on Darren's choice.

## INTEGRATIONS WITH HOME LAB (Section 13)
- **Kali + Metasploitable2** - Home Lab-owned infrastructure; Ghost Sentinel's attack-simulation scenarios run directly against them
- **Host laptop + Sysmon** - Home Lab-owned; supplies telemetry Ghost Sentinel's Splunk SIEM work depends on
- **Splunk** - runs on Home Lab infrastructure but is Ghost Sentinel's core analysis tool
- **Windows Server 2022 (2)** - Home Lab-owned; earmarked as future Domain Controller for Ghost Sentinel's planned AD lab
- **What crosses between them:** log/telemetry data flows from Home Lab into Splunk for Ghost Sentinel's investigations; nothing flows back
- **Dependency/config warning:** Don't let Ghost Sentinel work reinstall Splunk, delete/rebuild VMs, or change networking without checking HOMELAB_STATE.md

## SESSION HANDOFF
- What we accomplished: Completed Day 1 Step 3 (repository audit + security/privacy check); confirmed repo content is real and honest; resolved the one flagged item (fake hostname, confirmed intentional)
- Files modified: This file updated
- Configuration changes: None
- Errors encountered: None this round
- What remains unfinished: First hands-on scenario not yet chosen/run; Sysmon->Splunk forwarding gap not yet fixed
- Exact point where we stopped: Waiting on Darren to choose port scan sim vs. privilege escalation sim
- Exact next action: Run the chosen scenario against Kali + Metasploitable2, then document it as investigation-02 following the existing template
