# 🛡️ Metasploitable3 — Penetration Testing Report

Comprehensive black-box penetration testing and vulnerability assessment of the **Metasploitable3** lab environment (Windows Server 2008 R2 SP1 and Ubuntu 14.04), following the **PTES** phase model for infrastructure testing and the **OWASP Testing Guide** for the web application components.

Team final project (NTI). My contribution: trojanized service analysis (UnrealIRCd backdoor) and container escalation review (docker group).

## 📋 Engagement Summary

- **Testing type:** Black-box, unauthenticated, network-based
- **Targets:** Metasploitable3 virtual machines on private, non-routable lab networks
- **Attacker platform:** Kali Linux
- **Testing period:** 17 - 23 August 2026
- **Workflow:** Reconnaissance → Service Enumeration → Vulnerability Identification → Exploitation → Post-Exploitation Verification
- **Results:** 8 validated findings (6 Critical, 2 High) — confirmed remote code execution in five of six engagements, and authentication bypass with unauthorized data disclosure in the sixth

## 🔍 Key Findings

- **SMBv1 Remote Code Execution (MS17-010 / EternalBlue, CVE-2017-0143):** unauthenticated kernel-level RCE on the Windows host, yielding NT AUTHORITY\SYSTEM
- **Weak Administrative Credentials (GlassFish):** admin console reachable over the network, password recovered by dictionary attack
- **Authenticated RCE via WAR Deployment:** GlassFish admin access turned directly into server-side code execution
- **Pre-Authentication SQL Injection (Drupal 7.5 "Drupageddon"):** arbitrary PHP execution with no valid credentials
- **SQL Injection / Authentication Bypass (payroll application):** login bypass and disclosure of employee salary records
- **ProFTPD 1.3.5 mod_copy Command Execution:** unauthenticated SITE CPFR/CPTO writes a payload into the web root, executed over HTTP
- **Trojanized UnrealIRCd 3.2.8.1 Backdoor (CVE-2010-2075):** any command sent after a fixed trigger string executes with no authentication
- **Excessive Group Membership (docker):** the compromised account's docker group membership provides a direct path to root

## 📂 Repository Contents

- `NTI final project -Penetration Testing  report.pdf` — the full consolidated report: methodology, findings register, severity ratings, tools, commands reference, and a prioritized remediation plan
- `Cyber Security Presentation.pptx` — the project presentation slides

## 👥 Team

- **Mohamed ElAzab** — Trojanized service analysis (UnrealIRCd) and container escalation review
- **Mahmoud Amgad** — Windows service exploitation (MS17-010) and GlassFish application server
- **Rawda Mohamed** — Content management system testing (Drupal core)
- **Sara Mahmoud** — Web application injection testing (payroll application)
- **Ahmed Nigm** — Network daemon exploitation (ProFTPD)
- **Thaghra** — Consolidation, quality review and reporting

> ⚠️ All activity documented here was performed against intentionally vulnerable, purpose-built training virtual machines inside private, non-routable lab networks. No third-party, production or internet-facing systems were in scope.
