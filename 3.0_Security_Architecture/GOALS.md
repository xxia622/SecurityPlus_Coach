# Domain 3.0 — Security Architecture
**Exam Weight: 18% | Study Window: Days 19–26**

---

## Top 10 Must-Know Concepts & Acronyms

### 1. Cloud Security Models
- **IaaS:** Infrastructure as a Service — customer manages OS up (EC2, Azure VMs)
- **PaaS:** Platform as a Service — customer manages apps and data (Heroku, App Engine)
- **SaaS:** Software as a Service — vendor manages everything (Office 365, Salesforce)
- **Shared Responsibility Model:** vendor secures the cloud, customer secures IN the cloud
- **FaaS/Serverless:** Function as a Service — event-driven, ephemeral compute

### 2. Cloud Deployment Models
- **Public cloud:** shared infrastructure, multi-tenant (AWS, Azure, GCP)
- **Private cloud:** dedicated infrastructure, single org
- **Hybrid cloud:** combination of public + private
- **Community cloud:** shared by organizations with common requirements (government)
- **Key risks:** data sovereignty, vendor lock-in, shared tenancy, shadow IT

### 3. Network Segmentation & DMZ
- **DMZ:** Demilitarized Zone — public-facing servers between two firewalls
- **VLAN:** Layer 2 segmentation — logical network separation on same physical hardware
- **Microsegmentation:** granular east-west traffic control (SDN, Zero Trust)
- **Air gap:** complete physical isolation (ICS/SCADA, classified systems)
- **Bastion host:** hardened jump server for accessing private network segments

### 4. Firewall Types
- **Packet filter:** Layer 3/4, stateless, ACL-based — fast but limited
- **Stateful inspection:** tracks connection state (SYN, SYN-ACK, ACK)
- **Application-layer (proxy):** deep packet inspection, understands protocols
- **NGFW:** Next-Gen Firewall — combines stateful + app-aware + IPS + SSL inspection
- **WAF:** Web Application Firewall — Layer 7, protects against SQLi, XSS, OWASP Top 10

### 5. VPN Technologies
- **IPSec:** Layer 3, tunnel mode (encrypts full packet) vs. transport mode (encrypts payload)
  - AH: Authentication Header — integrity only
  - ESP: Encapsulating Security Payload — encryption + integrity
- **SSL/TLS VPN:** clientless or thin-client, uses port 443 (easier through firewalls)
- **Split tunneling:** only specific traffic routes through VPN — vs. full tunnel
- **Site-to-site vs. remote access VPN**

### 6. Identity & Access Management (IAM) Infrastructure
- **LDAP:** Lightweight Directory Access Protocol — directory queries (port 389, 636 for LDAPS)
- **Active Directory:** Microsoft's LDAP + Kerberos implementation
- **Kerberos:** ticket-based authentication (KDC, TGT, TGS)
- **SAML:** Security Assertion Markup Language — XML-based SSO federation
- **OAuth 2.0:** authorization delegation (not authentication)
- **OpenID Connect:** authentication layer on top of OAuth 2.0

### 7. Secure Network Design Principles
- **Least privilege:** minimum access required
- **Defense in depth:** layered security controls
- **Fail secure/fail safe:** system defaults to secure state on failure
- **Separation of duties:** no single person controls entire process
- **Network address translation (NAT):** hides internal addressing, not a security control by itself

### 8. Wireless Security Protocols
- **WEP:** Wired Equivalent Privacy — broken, do not use
- **WPA2:** CCMP/AES — currently acceptable, vulnerable to KRACK
- **WPA3:** SAE (Simultaneous Authentication of Equals) — replaces PSK, forward secrecy
- **802.1X:** port-based network access control — requires RADIUS for enterprise wireless
- **EAP variants:** EAP-TLS (most secure, mutual cert auth), PEAP, EAP-TTLS

### 9. Data Security & Encryption in Architecture
- **Data states:** at rest (disk encryption — AES-256), in transit (TLS 1.2/1.3), in use (TEE, SGX)
- **DLP:** Data Loss Prevention — network DLP, endpoint DLP, cloud DLP
- **DRM:** Digital Rights Management — controls usage after delivery
- **Tokenization:** replace sensitive data with non-sensitive token (PCI-DSS)
- **Masking:** obfuscate data for non-production environments

### 10. Resilience & High Availability Architecture
- **RPO:** Recovery Point Objective — max acceptable data loss (how far back to restore)
- **RTO:** Recovery Time Objective — max acceptable downtime
- **MTTR:** Mean Time to Repair
- **MTBF:** Mean Time Between Failures
- **Hot site:** fully operational duplicate — fastest recovery, most expensive
- **Warm site:** partially equipped — balanced cost/recovery
- **Cold site:** facility only — cheapest, slowest recovery
- **Active/active vs. active/passive clustering**

---

## Acronym Quick-Reference

| Acronym | Expansion |
|---|---|
| IaaS | Infrastructure as a Service |
| PaaS | Platform as a Service |
| SaaS | Software as a Service |
| DMZ | Demilitarized Zone |
| VLAN | Virtual Local Area Network |
| NGFW | Next-Generation Firewall |
| WAF | Web Application Firewall |
| VPN | Virtual Private Network |
| IPSec | Internet Protocol Security |
| LDAP | Lightweight Directory Access Protocol |
| SAML | Security Assertion Markup Language |
| RPO | Recovery Point Objective |
| RTO | Recovery Time Objective |
| MTTR | Mean Time to Repair |
| MTBF | Mean Time Between Failures |
| DLP | Data Loss Prevention |
| TEE | Trusted Execution Environment |

---

## Self-Test Questions
1. In the Shared Responsibility Model, who is responsible for patching the OS in IaaS vs. SaaS?
2. What is the difference between RPO and RTO? Which is harder to achieve?
3. Why is WEP considered broken? What replaced it?
4. When would you use a warm site vs. a hot site?
5. How does 802.1X differ from a standard PSK Wi-Fi setup?
