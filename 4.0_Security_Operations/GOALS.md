# Domain 4.0 — Security Operations
**Exam Weight: 28% (Highest Weight Domain) | Study Window: Days 27–36**

---

## Top 10 Must-Know Concepts & Acronyms

### 1. Incident Response (IR) Process
**PICERL:** Preparation → Identification → Containment → Eradication → Recovery → Lessons Learned
- **Preparation:** IR plan, playbooks, tools, team roles (CIRT/CSIRT)
- **Identification:** detect and confirm the incident (SIEM alerts, user reports)
- **Containment:** short-term (isolate host) and long-term (patch, block IOCs)
- **Eradication:** remove malware, close attack vector
- **Recovery:** restore systems, verify integrity, monitor
- **Lessons Learned:** post-incident review, update playbooks

### 2. Digital Forensics Principles
- **Order of volatility:** CPU cache → RAM → swap → disk → remote logging → physical
- **Chain of custody:** documented handling — evidence admissibility
- **Legal hold:** preserve data in anticipation of litigation
- **Write blocker:** hardware/software that prevents modifying evidence media
- **Forensic image:** bit-for-bit copy (dd, FTK Imager, Autopsy)
- **Hashing evidence:** MD5/SHA-256 before and after to prove integrity

### 3. SIEM & Log Management
- **SIEM:** Security Information and Event Management — aggregates logs, correlates events
- **Log sources:** firewall, IDS/IPS, endpoint, Active Directory, DNS, proxy, VPN
- **Correlation rules:** alert when multiple events match a pattern (failed logins + privilege escalation)
- **UEBA:** User and Entity Behavior Analytics — baseline + anomaly detection
- **SOC tiers:** Tier 1 (triage/alert), Tier 2 (investigation), Tier 3 (threat hunting/forensics)
- **Key vendors:** Splunk, Microsoft Sentinel, IBM QRadar, Elastic SIEM

### 4. Endpoint Security
- **EDR:** Endpoint Detection and Response — continuous monitoring, behavioral analysis, rollback
- **AV/Anti-malware:** signature-based + heuristic detection
- **Host-based IDS/IPS (HIDS/HIPS):** monitors system calls, file changes, registry
- **FIM:** File Integrity Monitoring — alerts on unauthorized file changes (Tripwire)
- **Application whitelisting:** only approved applications can execute
- **Full disk encryption:** BitLocker (Windows), FileVault (macOS), LUKS (Linux)

### 5. Network Security Monitoring
- **IDS:** Intrusion Detection System — passive, alerts only (signature vs. anomaly-based)
- **IPS:** Intrusion Prevention System — inline, can block (same detection methods)
- **Honeypot:** decoy system to detect/study attackers
- **Honeynet:** network of honeypots
- **Network TAP:** passive traffic capture device (vs. SPAN/mirror port)
- **NetFlow:** metadata about network flows (not full packet capture) — scalable monitoring

### 6. Identity Hardening & Privileged Access
- **PAM:** Privileged Access Management — vault credentials, session recording (CyberArk, BeyondTrust)
- **PIM:** Privileged Identity Management — just-in-time privileged access (Azure PIM)
- **LAPS:** Local Administrator Password Solution — unique local admin passwords per machine
- **Service accounts:** principle of least privilege, avoid interactive login
- **MFA enforcement:** especially for admin/privileged accounts
- **Credential stuffing defense:** rate limiting, breach password checking (HaveIBeenPwned API)

### 7. Vulnerability & Patch Management Operations
- **Asset inventory:** CMDB — you can't protect what you don't know exists
- **Authenticated vs. unauthenticated scans:** authenticated finds more, requires credentials
- **Patch cadence:** emergency (0-day), critical (24–72h), high (7 days), medium/low (30 days)
- **Compensating controls:** when patching is not immediately possible (WAF rules, network isolation)
- **Penetration test types:** black box, white box, gray box

### 8. Security Automation & Orchestration
- **SOAR:** Security Orchestration, Automation and Response — automated playbook execution
- **Runbook / Playbook:** step-by-step IR procedures (manual vs. automated)
- **API integration:** SIEM → SOAR → ticketing system → endpoint
- **Threat hunting:** proactive search for undetected threats using hypotheses + data
- **Purple team:** Red team (attackers) + Blue team (defenders) collaborate to improve detection

### 9. Data & Application Security Operations
- **Code review:** static (SAST) vs. dynamic (DAST) analysis
- **SAST:** scans source code before execution (Checkmarx, SonarQube)
- **DAST:** tests running application (Burp Suite, OWASP ZAP)
- **Secrets management:** vault API keys/credentials (HashiCorp Vault, AWS Secrets Manager)
- **Secure SDLC:** integrate security at every phase, not just testing
- **DevSecOps:** shift-left security — security in CI/CD pipeline

### 10. Hardening & Configuration Management
- **CIS Benchmarks:** prescriptive hardening guides per OS/application
- **STIG:** Security Technical Implementation Guide (DoD standard)
- **Baseline configuration:** approved secure state — deviation = alert
- **Change management:** CAB (Change Advisory Board), rollback plan required
- **Disable unnecessary services/ports:** reduce attack surface
- **Group Policy (GPO):** Windows centralized configuration enforcement

---

## Acronym Quick-Reference

| Acronym | Expansion |
|---|---|
| IR | Incident Response |
| CIRT | Computer Incident Response Team |
| PICERL | Preparation, Identification, Containment, Eradication, Recovery, Lessons Learned |
| SIEM | Security Information and Event Management |
| EDR | Endpoint Detection and Response |
| IDS | Intrusion Detection System |
| IPS | Intrusion Prevention System |
| SOAR | Security Orchestration, Automation and Response |
| PAM | Privileged Access Management |
| FIM | File Integrity Monitoring |
| UEBA | User and Entity Behavior Analytics |
| SAST | Static Application Security Testing |
| DAST | Dynamic Application Security Testing |
| LAPS | Local Administrator Password Solution |
| CIS | Center for Internet Security |
| STIG | Security Technical Implementation Guide |

---

## CLI_DRILLS

Practice these commands in a lab environment. Critical for PBQs in Domain 4.0.

### Drill 1 — Analyzing Logs with grep / awk (Linux IR)
```bash
# Find failed SSH login attempts in auth log
grep "Failed password" /var/log/auth.log | awk '{print $11}' | sort | uniq -c | sort -rn | head 20

# Count unique IPs with 10+ failed attempts (brute force detection)
grep "Failed password" /var/log/auth.log | awk '{print $11}' | sort | uniq -c | awk '$1 >= 10' | sort -rn

# Find successful logins after multiple failures (possible compromise)
grep "Accepted password" /var/log/auth.log | tail -50
```
**Why it matters:** Log analysis is a core SOC/IR skill. Exam PBQs test ability to identify brute force, lateral movement, and compromise indicators from log data.

### Drill 2 — netstat / ss: Detect Suspicious Listeners & Connections
```bash
# Show all listening services with process IDs (Linux)
ss -tulnp

# Show established connections — identify C2 communication
ss -tnp state established

# Windows: show all connections with PID, then find process name
netstat -ano | findstr LISTENING
# Then: tasklist | findstr <PID>

# Kill a suspicious process (after verification)
kill -9 <PID>   # Linux
# taskkill /PID <PID> /F   # Windows
```
**Why it matters:** Identifying rogue listeners and C2 connections is a key forensic task. Know the difference between expected and unexpected ports.

### Drill 3 — File Integrity & Hash Verification (Forensics)
```bash
# Generate SHA-256 hash of a file (evidence integrity)
sha256sum suspicious_file.exe

# Generate MD5 hash (legacy, still used for quick comparison)
md5sum suspicious_file.exe

# Compare hash against known-good (VirusTotal, NIST NSRL)
# Format: sha256sum <file> | awk '{print $1}'

# Find recently modified files (last 24 hours) — detect persistence
find /etc /usr /bin -mtime -1 -type f 2>/dev/null

# Find SUID/SGID files — privilege escalation indicators
find / -perm /4000 -type f 2>/dev/null
```
**Why it matters:** Digital forensics requires provable chain of custody. Hash verification before/after confirms evidence was not tampered with. A PBQ staple.

### Drill 4 — nmap: Operational Security Scanning
```bash
# Quick host discovery (ping sweep) — asset inventory
nmap -sn 192.168.1.0/24

# Scan for specific vulnerable service versions
nmap -sV -p 22,80,443,3389,445 --open 192.168.1.0/24

# Run NSE vulnerability scripts against a target
nmap --script=smb-vuln-ms17-010 -p 445 192.168.1.100

# UDP scan for common services (DNS, SNMP, DHCP)
nmap -sU -p 53,161,162,67,68 192.168.1.100
```
**Why it matters:** Operations teams run regular scans to maintain asset visibility. Knowing how to interpret nmap output is assumed knowledge for Domain 4.0 PBQs.

### Drill 5 — Firewall Rules & iptables (Linux Hardening)
```bash
# View current iptables rules
iptables -L -n -v --line-numbers

# Block a specific IP (containing an active threat)
iptables -I INPUT -s 203.0.113.50 -j DROP

# Allow only SSH from a specific management subnet
iptables -A INPUT -p tcp --dport 22 -s 10.10.10.0/24 -j ACCEPT
iptables -A INPUT -p tcp --dport 22 -j DROP

# Save rules (persist across reboots — Debian/Ubuntu)
iptables-save > /etc/iptables/rules.v4

# Windows Firewall — block inbound on specific port (PowerShell)
New-NetFirewallRule -DisplayName "Block Port 4444" -Direction Inbound -Protocol TCP -LocalPort 4444 -Action Block
```
**Why it matters:** Containment phase of IR often requires firewall manipulation to isolate compromised hosts. Exam tests both Linux iptables and Windows Firewall syntax.

---

## Self-Test Questions
1. What is the correct order of the incident response phases (PICERL)?
2. Why must you preserve RAM before disk when capturing forensic evidence?
3. What is the difference between IDS and IPS? When would you choose one over the other?
4. What does SOAR do that a SIEM alone cannot?
5. You find a process listening on port 4444. What are your next steps?
