# Domain 5.0 — Security Program Management & Oversight
**Exam Weight: 20% | Study Window: Days 37–42**

---

## Top 10 Must-Know Concepts & Acronyms

### 1. Risk Management Fundamentals
- **Risk = Threat × Vulnerability × Impact** (qualitative model)
- **Quantitative risk:** AV × EF = SLE; SLE × ARO = ALE
  - **AV:** Asset Value
  - **EF:** Exposure Factor (% of asset lost)
  - **SLE:** Single Loss Expectancy
  - **ARO:** Annualized Rate of Occurrence
  - **ALE:** Annualized Loss Expectancy
- **Risk responses:** Accept, Transfer (insurance), Avoid, Mitigate
- **Residual risk:** risk remaining after controls are applied
- **Risk appetite vs. risk tolerance:** strategic threshold vs. acceptable deviation

### 2. Governance Frameworks & Standards
- **NIST CSF:** Identify, Protect, Detect, Respond, Recover — US standard
- **ISO/IEC 27001:** ISMS standard — certifiable, globally recognized
- **COBIT:** IT governance framework — aligns IT with business objectives
- **ITIL:** IT service management framework — service lifecycle
- **SOC 2 Type I vs. Type II:** point-in-time vs. over-time operational effectiveness
- **FedRAMP:** US government cloud authorization program

### 3. Policies, Standards, Procedures & Guidelines
- **Policy:** high-level directive (mandatory) — "what" and "why"
- **Standard:** specific requirements that implement policy — "how much / what exactly"
- **Procedure:** step-by-step implementation instructions
- **Guideline:** recommended (not mandatory) best practices
- **AUP:** Acceptable Use Policy — employee system usage rules
- **Data classification policy:** public, internal, confidential, restricted/top secret

### 4. Compliance & Legal Frameworks
- **GDPR:** EU — data privacy, 72-hour breach notification, right to erasure
- **HIPAA:** US healthcare — PHI protection, administrative/physical/technical safeguards
- **PCI-DSS:** payment card data — 12 requirements, SAQ vs. full audit
- **SOX:** financial reporting controls (public companies)
- **GLBA:** financial institutions — data sharing and safeguard rules
- **CCPA:** California consumer privacy — US analog to GDPR
- **FISMA:** US federal agencies — NIST-based security programs

### 5. Third-Party & Supply Chain Risk
- **Vendor risk assessment:** security questionnaire, SOC 2 report review, pen test results
- **Right-to-audit clause:** contract right to audit vendor security controls
- **SLA:** Service Level Agreement — uptime, response time, security obligations
- **MSP/MSSP risk:** your vendor has access to your environment
- **Software supply chain:** compromised libraries/dependencies (SolarWinds, Log4Shell)
- **SBOM:** Software Bill of Materials — inventory of software components

### 6. Security Awareness & Training
- **Phishing simulations:** baseline → train → resimulate → measure improvement
- **Role-based training:** developers get SSDLC training, execs get social engineering training
- **Insider threat program:** monitor + report suspicious behavior
- **Security culture:** tone from the top, security champions, gamification
- **Onboarding/offboarding procedures:** NDA signing, access provisioning/deprovisioning

### 7. Data Privacy & Classification
- **PII:** Personally Identifiable Information — name, SSN, DOB, email
- **PHI:** Protected Health Information — HIPAA-covered medical records
- **Data owner:** business unit responsible for data (defines classification)
- **Data custodian:** IT — implements controls specified by owner
- **Data processor vs. data controller:** GDPR distinction
- **Data retention policy:** how long to keep data, when to destroy (and how)

### 8. Business Continuity & Disaster Recovery Planning
- **BCP:** Business Continuity Plan — how the organization continues operating
- **DRP:** Disaster Recovery Plan — how IT systems recover
- **BIA:** Business Impact Analysis — identifies critical processes, RTOs, RPOs
- **Tabletop exercise:** discussion-based scenario — tests plan without real disruption
- **Functional drill / full-scale exercise:** progressive testing levels
- **COOP:** Continuity of Operations Plan (federal agencies)

### 9. Security Metrics & Reporting
- **KPI:** Key Performance Indicator — measures security program effectiveness
- **KRI:** Key Risk Indicator — early warning of risk threshold breach
- **Patch compliance rate:** % of systems patched within SLA
- **Mean time to detect (MTTD) / mean time to respond (MTTR)**
- **Phishing click rate:** before and after training
- **Vulnerability remediation SLA compliance**
- **Executive dashboard:** risk posture at-a-glance (not technical detail)

### 10. Audit, Assessment & Attestation
- **Internal audit:** self-assessment — identifies gaps before external audit
- **External audit:** independent third party — SOC 2, ISO 27001, PCI QSA
- **Penetration test vs. vulnerability assessment vs. audit:** scope and purpose differ
- **Attestation:** formal declaration that controls are effective
- **Gap analysis:** current state vs. desired state (framework compliance)
- **Continuous monitoring:** ongoing automated control verification vs. point-in-time audit

---

## Acronym Quick-Reference

| Acronym | Expansion |
|---|---|
| ALE | Annualized Loss Expectancy |
| ARO | Annualized Rate of Occurrence |
| SLE | Single Loss Expectancy |
| AV | Asset Value |
| EF | Exposure Factor |
| BIA | Business Impact Analysis |
| BCP | Business Continuity Plan |
| DRP | Disaster Recovery Plan |
| AUP | Acceptable Use Policy |
| KPI | Key Performance Indicator |
| KRI | Key Risk Indicator |
| SLA | Service Level Agreement |
| SBOM | Software Bill of Materials |
| PHI | Protected Health Information |
| PII | Personally Identifiable Information |
| GDPR | General Data Protection Regulation |
| HIPAA | Health Insurance Portability and Accountability Act |

---

## Business Risk & ROI: An Architect-Level Perspective

> This section translates technical security controls into the language of business risk, financial impact, and return on investment — essential for CISO-level communication and architect-level certification alignment.

---

### Translating Controls into Business Risk Language

Security architects must communicate upward (to executives and board) and outward (to auditors and clients). The translation framework:

| Technical Control | Business Risk Mitigated | Financial Impact |
|---|---|---|
| MFA deployment | Credential theft / account takeover | Avg. breach cost: $4.88M (IBM 2024) — MFA blocks ~99.9% of automated attacks |
| EDR deployment | Ransomware / malware infection | Avg. ransomware recovery cost: $2.73M; EDR reduces dwell time significantly |
| Data encryption at rest | Data breach / regulatory fine | GDPR fines up to 4% of global annual revenue or €20M |
| Patch management program | Exploited known vulnerabilities | 60%+ of breaches exploit known, unpatched CVEs |
| SIEM / SOC | Undetected breaches | Avg. dwell time without MDR: 204 days; with: ~21 days |
| Security awareness training | Phishing / social engineering | Phishing is the #1 initial access vector; training reduces click rates 60–80% |
| Vendor risk management | Third-party breach | 62% of organizations experienced a supply chain attack in 2023 |

---

### ROI Framework for Security Investments

**Formula: ROI = (ALE Before − ALE After − Cost of Control) / Cost of Control**

**Example — Deploying MFA:**
- Asset value (email system + data): $5,000,000
- EF (credential attack): 30% → SLE = $1,500,000
- ARO (attacks per year): 0.4 → ALE Before = $600,000
- MFA reduces ARO by 90% → ALE After = $60,000
- Annual MFA licensing cost: $50,000
- **ROI = ($600,000 − $60,000 − $50,000) / $50,000 = 980%**

Use this model when justifying security budget to non-technical leadership.

---

### CSBA-Aligned Control Mapping (Architect Perspective)

The **Cloud Security Business Alignment (CSBA)** framework maps security investment to four business value drivers:

**1. Risk Reduction**
- Implement NIST CSF Identify + Protect functions first — highest ROI
- Prioritize controls that address the highest-probability, highest-impact risks (use risk matrix)
- Quantify residual risk in dollar terms for executive reporting

**2. Regulatory Compliance Avoidance**
- GDPR non-compliance: up to €20M or 4% global revenue
- HIPAA: $100 — $50,000 per violation, up to $1.9M per category/year
- PCI-DSS: $5,000 — $100,000/month fines + loss of card processing privileges
- Compliance programs are insurance policies — cost of compliance << cost of fine

**3. Operational Resilience**
- Downtime cost: average $9,000/minute for enterprise systems (Gartner)
- BCP/DRP investment: measured against RTO/RPO commitments in SLAs
- Redundant architecture: hot site ROI = (downtime cost × incidents prevented) − site cost
- Resilience enables revenue protection, not just cost avoidance

**4. Competitive Advantage & Trust**
- SOC 2 Type II certification: reduces customer security questionnaire burden, accelerates sales cycles
- ISO 27001 certification: opens government and enterprise procurement channels
- Security as a differentiator: 73% of buyers consider vendor security posture in purchasing decisions
- Data: breach disclosure causes avg. 7% stock price drop (Comparitech, 2023)

---

### Presenting Security to the Board: The Architect's Toolkit

**Do:**
- Translate risk to financial exposure (ALE, regulatory fines, breach cost benchmarks)
- Use industry benchmarks (IBM Cost of a Data Breach, Verizon DBIR)
- Frame investments as risk transfer vs. control (insurance analogy)
- Present a risk register with top 5 risks, likelihood, impact, and mitigation status
- Show security posture trend over time (improving = program working)

**Don't:**
- Lead with CVE counts or vulnerability numbers (no context for executives)
- Use technical jargon without translation
- Present security as a cost center — frame it as risk management and value protection

---

## Self-Test Questions
1. Calculate ALE: Asset Value = $2M, EF = 25%, ARO = 0.5
2. What is the difference between a BCP and a DRP?
3. Name three compliance frameworks and their primary industry focus.
4. How would you present the ROI of a SIEM deployment to a CFO?
5. What is residual risk, and how does it appear on an executive risk register?
