# Domain 1.0 — General Security Concepts
**Exam Weight: 12% | Study Window: Days 1–8**

---

## Top 10 Must-Know Concepts & Acronyms

### 1. CIA Triad
**Confidentiality, Integrity, Availability** — the three pillars of information security.
- Confidentiality: only authorized users access data (encryption, access control)
- Integrity: data is accurate and unaltered (hashing, digital signatures)
- Availability: systems are accessible when needed (redundancy, failover)

### 2. AAA Framework
**Authentication, Authorization, Accounting**
- Authentication: verify identity (MFA, passwords, biometrics)
- Authorization: grant permissions based on identity (RBAC, ABAC)
- Accounting: log and audit actions (SIEM, audit trails)
- Protocols: RADIUS, TACACS+, Diameter

### 3. Zero Trust Architecture
"Never trust, always verify" — assumes breach, verifies every request.
- Key components: identity verification, least privilege, microsegmentation
- Contrast with legacy perimeter-based "castle and moat" model
- NIST SP 800-207 is the reference framework

### 4. Cryptography Fundamentals
- **Symmetric:** same key to encrypt/decrypt (AES-256, 3DES) — fast, key distribution problem
- **Asymmetric:** public/private key pair (RSA, ECC) — slower, solves key distribution
- **Hashing:** one-way, integrity only (SHA-256, SHA-3, MD5 — MD5 broken)
- **PKI:** Public Key Infrastructure — CAs, certificates, CRLs, OCSP

### 5. Authentication Types & MFA Factors
- **Something you know:** password, PIN
- **Something you have:** smart card, hardware token, OTP
- **Something you are:** biometrics (fingerprint, retina, facial)
- **Somewhere you are:** geolocation
- **Something you do:** behavioral (keystroke dynamics)

### 6. Access Control Models
- **DAC** (Discretionary): owner sets permissions (Windows NTFS)
- **MAC** (Mandatory): system enforces labels (government/military, SELinux)
- **RBAC** (Role-Based): permissions tied to roles (most enterprise systems)
- **ABAC** (Attribute-Based): policies based on attributes (most flexible)
- **Rule-Based:** if/then rules (firewall ACLs)

### 7. Security Control Categories & Types
- **Categories:** Technical, Managerial, Operational, Physical
- **Types:** Preventive, Detective, Corrective, Deterrent, Compensating, Directive
- Know how to classify a given control into both a category AND a type

### 8. Gap Analysis & Risk Terminology
- **Vulnerability:** weakness that can be exploited
- **Threat:** potential cause of harm
- **Risk:** likelihood × impact
- **Exploit:** mechanism that leverages a vulnerability
- **Attack surface:** total sum of exploitable entry points

### 9. Non-repudiation
Proof that a specific entity performed an action — cannot deny it later.
- Achieved via: digital signatures (asymmetric crypto), audit logs, PKI
- Distinct from authentication — non-repudiation provides legal-grade proof

### 10. Key Security Frameworks & Standards
- **NIST CSF:** Identify, Protect, Detect, Respond, Recover
- **ISO/IEC 27001:** ISMS standard
- **SOC 2:** Trust service criteria (Type I vs. Type II)
- **PCI-DSS:** payment card security
- **HIPAA:** healthcare data
- **GDPR:** EU data privacy

---

## Acronym Quick-Reference

| Acronym | Expansion |
|---|---|
| AAA | Authentication, Authorization, Accounting |
| CIA | Confidentiality, Integrity, Availability |
| DAC | Discretionary Access Control |
| MAC | Mandatory Access Control |
| RBAC | Role-Based Access Control |
| ABAC | Attribute-Based Access Control |
| PKI | Public Key Infrastructure |
| CA | Certificate Authority |
| CRL | Certificate Revocation List |
| OCSP | Online Certificate Status Protocol |
| MFA | Multi-Factor Authentication |
| SSO | Single Sign-On |
| NIST | National Institute of Standards and Technology |
| CSF | Cybersecurity Framework |
| ISMS | Information Security Management System |

---

## Self-Test Questions
1. What is the difference between authentication and authorization?
2. Which access control model is most commonly used in military/government systems?
3. Name three controls that provide non-repudiation.
4. AES is symmetric or asymmetric? What about RSA?
5. Map the NIST CSF five functions to a real-world incident response scenario.
