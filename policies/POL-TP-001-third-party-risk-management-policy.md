# Third-Party Risk Management Policy
## MedCore Health Systems

---

**Policy ID:** POL-TP-001
**Version:** 2.0
**Effective Date:** January 15, 2026
**Review Date:** January 2027
**Policy Owner:** Jonathan E. Steele, CISO
**Co-Owner:** Dr. Rachel Feinberg, Privacy Officer
**Approved By:** Marcus T. Hargrove, CEO
**NIST Control Mapping:** SA-9, SA-12, CA-3, IR-7
**HIPAA Mapping:** 45 CFR §164.308(b) — Business Associate Contracts; §164.314 — Organizational Requirements
**Classification:** INTERNAL

---

## 1. Purpose

This Third-Party Risk Management (TPRM) Policy establishes the requirements for identifying, assessing, and managing security and privacy risks introduced by third parties — including vendors, business associates, contractors, and service providers — that have access to MedCore Health Systems' systems, data, or facilities. The protection of ePHI extends to all parties who create, receive, maintain, or transmit ePHI on MedCore's behalf.

---

## 2. Scope

This policy applies to all third parties that:
- Have or request access to MedCore information systems or data, including ePHI
- Provide services or products that are integrated into or support MedCore's information systems
- Process, store, or transmit ePHI or other sensitive MedCore data on MedCore's behalf
- Connect their systems to MedCore's systems via network interconnections

---

## 3. Policy Statement

### 3.1 Business Associate Agreements (BAAs)

Any entity that creates, receives, maintains, or transmits ePHI on behalf of MedCore is a Business Associate under HIPAA and must execute a Business Associate Agreement (BAA) before any ePHI is shared or accessible.

- BAAs are required without exception for all Business Associates
- BAA templates are maintained by the Privacy Officer and Legal Counsel
- BAAs must include provisions for safeguarding ePHI, reporting breaches, and returning or destroying ePHI upon contract termination
- Existing BAAs are reviewed annually and upon any significant change to the scope of services
- The BAA Register is maintained by the Privacy Officer and is reviewed quarterly

### 3.2 Vendor Risk Tiering

All MedCore vendors and third parties are classified into one of three risk tiers:

| Tier | Criteria | Assessment Requirement | Review Frequency |
|------|----------|----------------------|-----------------|
| Tier 1 — Critical | Access to ePHI; integrated into EHRP systems; cloud infrastructure providers; security tool providers | Full security questionnaire + right-to-audit; annual SOC 2 Type II or equivalent | Annual |
| Tier 2 — High | Access to Confidential (non-ePHI) data; network connectivity to MedCore; SaaS tools with user data | Security questionnaire; review of available security documentation | Annual |
| Tier 3 — Standard | No data access; physical goods/services; no system access | Attestation of compliance with applicable requirements | Biennial |

### 3.3 Vendor Security Assessment Process

Before onboarding any new Tier 1 or Tier 2 vendor, the following must be completed:

1. **Risk Classification:** Procurement team submits a Third-Party Risk Intake Form to the ISSO for classification
2. **Security Questionnaire:** ISSO sends the MedCore Third-Party Security Questionnaire to the vendor; responses reviewed within 10 business days
3. **Documentation Review:** Review of vendor's SOC 2 Type II report, penetration test summary, vulnerability disclosure policy, and incident response procedures
4. **BAA Execution:** Privacy Officer executes BAA before any ePHI access is granted
5. **ISA/MOU:** ISSO executes an Interconnection Security Agreement (ISA) for any vendor with network connectivity to MedCore systems
6. **ISSO Approval:** ISSO documents findings and approves or conditionally approves vendor onboarding; CISO approval required for Tier 1 vendors
7. **Ongoing Monitoring:** Vendor registered in TPRM system with scheduled review dates

### 3.4 Interconnection Security Agreements (ISAs)

All third parties with network connections to MedCore systems must have a documented ISA:
- ISAs define the technical details of the connection, authorized data flows, security requirements, and monitoring responsibilities
- ISAs are reviewed annually or when the nature of the connection changes
- Any new interconnection requires ISSO approval before implementation
- ISA Register maintained by the ISSO and reviewed quarterly

### 3.5 Ongoing Vendor Monitoring

Ongoing monitoring of Tier 1 and Tier 2 vendors includes:
- Annual security reassessment using the MedCore Third-Party Security Questionnaire
- Review of vendor's annual SOC 2 Type II report or equivalent assurance document (within 6 months of report date)
- Monitoring of vendor security breach notifications and public disclosures
- Review of vendor's CISA Known Exploited Vulnerability (KEV) exposure for critical software
- Immediate reassessment triggered by: vendor breach disclosure, significant service changes, regulatory action against vendor, or intelligence indicating vendor compromise

### 3.6 Vendor Incident Notification Requirements

All Tier 1 and Tier 2 vendors must notify MedCore of any security incident that may affect MedCore systems or data:
- Notification must occur within 24 hours of the vendor's incident declaration if ePHI may be involved
- Notification must occur within 72 hours for other security incidents
- Notification requirements must be contractually specified in the BAA and/or vendor agreement
- The ISSO initiates MedCore's incident response process upon receiving vendor breach notification

### 3.7 Vendor Offboarding

Upon termination of a vendor relationship:
- All MedCore system access must be revoked within 24 hours of contract termination
- Vendor must return or certify destruction of all MedCore data per BAA terms
- Network connections (VPN, ISA) must be terminated
- The Privacy Officer confirms ePHI return/destruction and closes the BAA
- Offboarding is documented and retained in the vendor record for 7 years

---

## 4. EHRP Third-Party Register (Current Tier 1 Vendors)

| Vendor | Service | BAA | ISA | Last Assessment | Next Review |
|--------|---------|-----|-----|----------------|-------------|
| Amazon Web Services | Cloud infrastructure (AWS GovCloud) | Yes | Yes | January 2026 | January 2027 |
| Okta | Identity and Access Management | Yes | Yes | January 2026 | January 2027 |
| CrowdStrike | Endpoint Detection and Response | Yes | Yes | January 2026 | January 2027 |
| Qualys | Vulnerability Management | Yes | Yes | January 2026 | January 2027 |
| Splunk | SIEM / Log Management | Yes | Yes | January 2026 | January 2027 |
| Surescripts | e-Prescribing (e-Rx) | Yes | Yes | January 2026 | January 2027 |
| External HIE | Health Information Exchange | Yes | Yes | January 2026 | January 2027 |
| IBM (Legacy HL7 support) | Interface Engine maintenance | Yes | N/A | January 2026 | January 2027 |

---

## 5. Roles and Responsibilities

| Role | Responsibility |
|------|---------------|
| Procurement Team | Submit third-party intake forms; ensure legal agreements are executed |
| ISSO | Conduct security assessments; maintain TPRM system; ISA management; ongoing monitoring |
| CISO | Approve Tier 1 vendor onboarding; review TPRM program; escalate significant vendor risks |
| Privacy Officer | Execute and maintain BAAs; BAA Register; ePHI return/destruction verification |
| Legal Counsel | Review vendor contracts for security and data protection terms |
| System Owner | Approve vendor system access within their system boundary |

---

## 6. Related Documents

- POL-AC-001: Access Control Policy
- POL-RA-002: Remote Access Policy
- MedCore BAA Template: MedCore-FORM-PV-001
- MedCore Third-Party Security Questionnaire: MedCore-FORM-TP-001
- Interconnection Security Agreement Template: MedCore-FORM-TP-002

---

## 7. Revision History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 2.0 | January 2026 | J. Steele / R. Feinberg | Major revision — added risk tiering; updated ongoing monitoring requirements; added Tier 1 vendor register |
| 1.5 | January 2025 | A. Osei, ISSO | Added ISA requirements; updated vendor offboarding section |

---

*MedCore Health Systems — INTERNAL*
*POL-TP-001 v2.0 | Effective January 15, 2026*
