# Domain 2.0 — Threats, Vulnerabilities & Mitigations
**Exam Weight: 22% | Study Window: Days 9–18**

---

## Top 10 Must-Know Concepts & Acronyms

### 1. Threat Actor Types & Motivations
- **Nation-state:** sophisticated, espionage/sabotage, APT groups (APT28, APT41)
- **Hacktivist:** ideological motivation, DDoS/defacement
- **Organized crime:** financial motivation, ransomware-as-a-service
- **Insider threat:** malicious vs. unintentional (negligent) insider
- **Script kiddie:** low skill, uses pre-built tools, opportunistic
- **Attributes:** internal/external, resources/funding, sophistication, intent

### 2. Social Engineering Attack Types
- **Phishing:** bulk email-based deception
- **Spear phishing:** targeted phishing (specific individual/org)
- **Whaling:** targets C-suite executives
- **Vishing:** voice call-based phishing
- **Smishing:** SMS-based phishing
- **Pretexting:** fabricated scenario to extract info
- **Baiting:** physical media (USB drop) or digital lure
- **Tailgating/Piggybacking:** physical access bypass

### 3. Malware Types
- **Virus:** attaches to files, requires user execution, self-replicating
- **Worm:** self-propagating, no host file needed, exploits network (EternalBlue/WannaCry)
- **Trojan:** disguised as legitimate software, opens backdoor
- **Ransomware:** encrypts data, demands payment (RaaS model)
- **RAT:** Remote Access Trojan — gives attacker C2 access
- **Rootkit:** hides at kernel/OS level, evades detection
- **Logic bomb:** triggers on condition (date, event)
- **Fileless malware:** lives in memory, uses LOLBins

### 4. Network Attack Types
- **DoS / DDoS:** volumetric (UDP flood), protocol (SYN flood), application layer (HTTP flood)
- **Man-in-the-Middle (MitM):** ARP poisoning, SSL stripping, evil twin WiFi
- **DNS poisoning / Spoofing:** redirect legitimate DNS queries
- **Replay attack:** capture and retransmit valid credentials/tokens
- **Pass-the-Hash:** use captured NTLM hash without cracking (lateral movement)

### 5. Application Vulnerabilities
- **SQL injection:** unsanitized input executes SQL commands
- **XSS (Cross-Site Scripting):** injects malicious scripts into web pages (stored vs. reflected)
- **CSRF:** tricks authenticated users into executing unwanted actions
- **Buffer overflow:** overwrites adjacent memory, enables code execution
- **Directory traversal:** `../` sequences to access files outside webroot
- **IDOR:** Insecure Direct Object Reference — manipulate object IDs to access unauthorized data

### 6. Vulnerability Scanning vs. Penetration Testing
| | Vuln Scan | Pen Test |
|---|---|---|
| Goal | Find weaknesses | Exploit weaknesses |
| Who | Internal team | External ethical hacker |
| Scope | Wide, automated | Defined, manual |
| Output | Vulnerability report | Exploit proof + recommendations |
- **CVE:** Common Vulnerabilities and Exposures — unique identifier
- **CVSS:** Common Vulnerability Scoring System — 0–10 severity rating
- **NVD:** National Vulnerability Database

### 7. Threat Intelligence
- **IOC:** Indicator of Compromise (IP, hash, domain, registry key)
- **IOA:** Indicator of Attack (behavioral patterns — lateral movement, privilege escalation)
- **OSINT:** Open Source Intelligence — publicly available data
- **STIX/TAXII:** structured threat intelligence sharing format/protocol
- **Dark web monitoring:** identify leaked credentials/data

### 8. Attack Frameworks
- **MITRE ATT&CK:** Tactics, Techniques, Procedures (TTPs) — 14 enterprise tactics
- **Kill Chain (Lockheed Martin):** Recon → Weaponize → Deliver → Exploit → Install → C2 → Actions
- **Diamond Model:** Adversary, Infrastructure, Capability, Victim

### 9. Cryptographic Attacks
- **Brute force:** try all combinations
- **Dictionary attack:** wordlist-based
- **Rainbow table:** precomputed hash lookup (mitigated by salting)
- **Birthday attack:** exploits hash collision probability
- **Downgrade attack:** force use of weaker protocol (POODLE — SSL3 downgrade)
- **Side-channel:** exploit physical implementation (timing, power analysis)

### 10. Vulnerability Management Lifecycle
1. Identify (scan)
2. Prioritize (CVSS + asset criticality)
3. Remediate (patch, mitigate, accept)
4. Verify (rescan)
5. Report
- **Patch Tuesday:** Microsoft's monthly patch release cycle
- **Zero-day:** exploited before vendor is aware / patch available

---

## Acronym Quick-Reference

| Acronym | Expansion |
|---|---|
| APT | Advanced Persistent Threat |
| CVE | Common Vulnerabilities and Exposures |
| CVSS | Common Vulnerability Scoring System |
| IOC | Indicator of Compromise |
| IOA | Indicator of Attack |
| RAT | Remote Access Trojan |
| RaaS | Ransomware-as-a-Service |
| MitM | Man-in-the-Middle |
| XSS | Cross-Site Scripting |
| CSRF | Cross-Site Request Forgery |
| IDOR | Insecure Direct Object Reference |
| TTP | Tactics, Techniques, and Procedures |
| OSINT | Open Source Intelligence |
| NVD | National Vulnerability Database |

---

## CLI_DRILLS

Practice these commands in a lab environment (Kali Linux, TryHackMe, or local VM).

### Drill 1 — nmap: Network Discovery & Port Scanning
```bash
# SYN scan (stealth), detect OS and service versions, output to file
nmap -sS -sV -O -oN scan_results.txt 192.168.1.0/24

# Aggressive scan with script engine (NSE) — use only on authorized targets
nmap -A -T4 --script=vuln 192.168.1.100
```
**Why it matters:** Enumeration is step one of every pen test and vulnerability assessment. Know the flags: `-sS` (SYN/stealth), `-sV` (version), `-O` (OS detection), `-p` (port range), `-T4` (timing).

### Drill 2 — openssl: Inspect Certificates & Test TLS
```bash
# Inspect a server's TLS certificate and chain
openssl s_client -connect example.com:443 -showcerts

# Check certificate expiry date
echo | openssl s_client -connect example.com:443 2>/dev/null | openssl x509 -noout -dates

# Generate a self-signed certificate (lab use)
openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -days 365 -nodes
```
**Why it matters:** TLS misconfiguration is a top-10 finding. Exam tests your ability to identify weak ciphers, expired certs, and certificate chain issues.

### Drill 3 — netstat / ss: Active Connections & Listening Ports
```bash
# Show all listening TCP/UDP ports with PIDs (Linux)
ss -tulnp

# Windows equivalent — show all connections with owning process
netstat -ano

# Filter for established connections only
netstat -an | grep ESTABLISHED
```
**Why it matters:** Used for detecting backdoors, unauthorized listeners, and C2 connections. PBQ favorite — identify suspicious ports.

### Drill 4 — Nikto: Web Vulnerability Scanner
```bash
# Basic web server scan
nikto -h http://192.168.1.100

# Scan with SSL and output to file
nikto -h https://192.168.1.100 -ssl -output nikto_report.txt -Format txt
```
**Why it matters:** Application-layer vulnerability identification. Tests for outdated software, dangerous HTTP methods, default credentials, and known CVEs in web servers.

### Drill 5 — tcpdump: Packet Capture & Traffic Analysis
```bash
# Capture all traffic on interface eth0, save to file
tcpdump -i eth0 -w capture.pcap

# Read pcap file and filter for HTTP traffic
tcpdump -r capture.pcap port 80

# Capture DNS queries (common for C2 detection)
tcpdump -i eth0 udp port 53 -v
```
**Why it matters:** Core skill for network forensics, detecting MitM attacks, and validating firewall rules. Pairs with Wireshark for GUI analysis.

---

## Self-Test Questions
1. What is the difference between a worm and a virus?
2. How does salting a password hash defend against a rainbow table attack?
3. What MITRE ATT&CK tactic does "Pass-the-Hash" fall under?
4. Name three IOCs an analyst might find after a ransomware infection.
5. What is the CVSS score threshold for Critical severity?
