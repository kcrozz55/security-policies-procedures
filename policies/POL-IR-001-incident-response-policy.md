# Incident Response Policy
## MedCore Health Systems

---

**Policy ID:** POL-IR-001
**Version:** 4.1
**Effective Date:** January 15, 2026
**Review Date:** January 2027
**Policy Owner:** Jonathan E. Steele, CISO
**Approved By:** Marcus T. Hargrove, CEO
**NIST Control Mapping:** IR-1, IR-4, IR-5, IR-6, IR-7, IR-8
**HIPAA Mapping:** 45 CFR §164.308(a)(6) — Security Incident Procedures; §164.308(a)(1)(ii)(D) — Information System Activity Review
**Classification:** INTERNAL

---

## 1. Purpose

This Incident Response Policy establishes the framework for detecting, reporting, analyzing, containing, eradicating, and recovering from information security incidents affecting MedCore Health Systems. It ensures that security incidents are handled in a consistent, timely, and effective manner that minimizes harm to patients, staff, and the organization, and meets all applicable regulatory reporting obligations including HIPAA Breach Notification Rule requirements.

---

## 2. Scope

This policy applies to all MedCore information systems, networks, and data — including ePHI, PII, and proprietary business information — and to all personnel with responsibility for detecting, reporting, or responding to security events.

---

## 3. Definitions

| Term | Definition |
|------|-----------|
| Security Event | Any observable occurrence in a system or network that may indicate a security issue; not all events are incidents |
| Security Incident | A violation or imminent threat of violation of information security policies, acceptable use policies, or standard security practices that adversely affects confidentiality, integrity, or availability of information |
| ePHI Breach | Impermissible acquisition, access, use, or disclosure of unsecured ePHI that compromises its security or privacy per HIPAA §164.402 |
| Severity 1 (Critical) | Active data breach, ransomware, or system compromise with confirmed ePHI exposure or patient care impact |
| Severity 2 (High) | Confirmed unauthorized access, malware infection, or significant data loss without confirmed ePHI exposure |
| Severity 3 (Medium) | Suspected unauthorized access, policy violations, or events requiring investigation |
| Severity 4 (Low) | Informational events, minor policy violations, or near-misses with no system impact |

---

## 4. Policy Statement

### 4.1 Incident Response Program

MedCore maintains a formal Incident Response capability including:
- A documented Incident Response Plan (MedCore-IRP-001) with detailed procedures for all incident categories
- A designated Incident Response Team (IRT) with defined roles and responsibilities
- 24/7 Security Operations Center (SOC) monitoring and initial triage capability
- Documented playbooks for the most probable incident scenarios
- Annual tabletop exercise and plan review

### 4.2 Incident Reporting Requirements

**Employee Reporting:**
All MedCore employees and contractors must report suspected security incidents immediately upon detection. Reports should be made to:
- The Security Operations Center (SOC): soc@medcorehealthsystems.org or ext. 5911 (24/7)
- The direct supervisor (in addition to the SOC, not instead of)
- Immediate physical response to ext. 5911 if a device has been stolen or patient data is visible to unauthorized persons

**Internal Escalation Timeline:**
| Severity | ISSO Notification | CISO Notification | AO / CEO Notification |
|----------|------------------|-------------------|----------------------|
| Severity 1 | Within 1 hour | Within 4 hours | Within 24 hours of confirmed incident |
| Severity 2 | Within 4 hours | Within 24 hours | If ePHI involved, within 24 hours |
| Severity 3 | Within 24 hours | Weekly summary | As warranted |
| Severity 4 | Weekly summary | Monthly summary | Not required |

**Regulatory Reporting:**
- **HHS Office for Civil Rights (OCR):** For breaches of unsecured ePHI affecting 500 or more individuals, MedCore must notify HHS OCR within 60 days of discovery. For breaches affecting fewer than 500 individuals, notification is required annually.
- **Affected Individuals:** Individuals affected by an ePHI breach must be notified without unreasonable delay and within 60 days of discovery per HIPAA §164.404.
- **Law Enforcement:** If criminal activity is suspected, the CISO will consult with Legal Counsel before contacting law enforcement.
- **Media:** For breaches affecting 500 or more individuals in a single state or jurisdiction, prominent media outlets must be notified within 60 days per HIPAA §164.406.

### 4.3 Incident Response Phases

**Phase 1 — Preparation:**
- Maintain IRP, playbooks, and contact lists in current state
- Conduct annual tabletop exercises
- Ensure all IR tools and communication channels are tested and available
- Maintain relationships with external IR support (forensics, legal, PR)

**Phase 2 — Detection and Analysis:**
- SOC analysts triage SIEM alerts and reported events
- Initial severity classification within 30 minutes of report receipt
- Evidence preservation begins immediately upon incident declaration
- Affected systems and users identified and documented

**Phase 3 — Containment:**
- Short-term containment to stop immediate damage (isolate systems, disable accounts)
- Long-term containment to allow operations to continue safely while eradication proceeds
- System snapshots taken for forensic preservation before any changes
- Communication to affected parties coordinated through CISO and Privacy Officer

**Phase 4 — Eradication:**
- Root cause identified and fully documented
- Malware, unauthorized access mechanisms, and vulnerabilities removed
- Systems verified clean before restoration

**Phase 5 — Recovery:**
- Systems restored from clean backups or rebuilt as needed
- Operations restored in a controlled, monitored manner
- Enhanced monitoring maintained for 30 days post-incident
- Verification that systems are functioning normally before full restoration

**Phase 6 — Post-Incident Activity:**
- Post-incident report completed within 14 days of incident closure
- Lessons learned documented and incorporated into IRP and controls
- POA&M updated with any control gaps identified
- CISO briefs AO on significant incidents

### 4.4 Evidence Handling

All evidence related to security incidents must be handled in accordance with evidence preservation requirements:
- No changes to affected systems before forensic imaging whenever possible
- Chain of custody documented for all evidence
- Evidence retained for a minimum of 7 years for ePHI-related incidents
- Evidence handling follows MedCore Forensics Evidence Procedures (MedCore-PROC-IR-002)

---

## 5. Roles and Responsibilities

| Role | Responsibility |
|------|---------------|
| All Employees | Report suspected incidents immediately to SOC; preserve potential evidence |
| SOC Analysts | 24/7 monitoring; initial triage; severity classification; ISSO notification |
| ISSO | Incident declaration and coordination; regulatory timeline tracking; POA&M updates |
| CISO | IRT leadership for Severity 1/2; AO notification; legal and regulatory coordination |
| Privacy Officer | ePHI breach analysis; notification requirements assessment; individual notification coordination |
| Legal Counsel | Legal privilege review; law enforcement liaison; regulatory filing support |
| IT Operations | Technical containment and recovery; evidence preservation; system restoration |
| HR | Employee-involved incidents; disciplinary process if applicable |

---

## 6. Related Documents

- Incident Response Plan: MedCore-IRP-001 v4.1
- Incident Response Playbooks: MedCore-PROC-IR-001 through IR-010
- Breach Notification Procedures: MedCore-PROC-PV-003
- Forensics Evidence Procedures: MedCore-PROC-IR-002

---

## 7. Revision History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 4.1 | January 2026 | J. Steele, CISO | Updated regulatory timelines; added Severity definitions table; aligned with NIST IR controls |
| 4.0 | January 2025 | A. Osei, ISSO | Major revision — added post-incident activity requirements; updated escalation timelines |

---

*MedCore Health Systems — INTERNAL*
*POL-IR-001 v4.1 | Effective January 15, 2026*
