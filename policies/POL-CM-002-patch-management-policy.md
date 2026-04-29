# Patch Management Policy
## MedCore Health Systems

---

**Policy ID:** POL-CM-002
**Version:** 3.1
**Effective Date:** January 15, 2026
**Review Date:** January 2027
**Policy Owner:** Jonathan E. Steele, CISO
**Approved By:** Marcus T. Hargrove, CEO
**NIST Control Mapping:** SI-2, CM-6, CM-3, RA-5
**HIPAA Mapping:** 45 CFR §164.308(a)(8) — Evaluation; §164.312(a)(2)(ii) — Emergency Access Procedure
**Classification:** INTERNAL

---

## 1. Purpose

This Patch Management Policy establishes the requirements for identifying, evaluating, testing, approving, and deploying security patches and software updates across all MedCore Health Systems information technology assets. Timely patch management is a fundamental defense against known vulnerabilities and is essential to maintaining the security and availability of systems that support patient care and protect ePHI.

---

## 2. Scope

This policy applies to all MedCore-owned and managed systems, including servers, workstations, mobile devices, network infrastructure, cloud resources, and embedded systems within the EHRP authorization boundary. It applies to all software including operating systems, applications, firmware, and third-party libraries.

---

## 3. Policy Statement

### 3.1 Patch Identification

MedCore uses the following sources to identify applicable patches and security updates:
- Vendor security advisories (Microsoft, Red Hat, AWS, Oracle, and all other software vendors in use)
- CISA Known Exploited Vulnerabilities (KEV) Catalog
- NVD (National Vulnerability Database) and CVE feeds
- Qualys Vulnerability Management weekly scan results
- AWS Inspector findings for cloud-hosted components
- ISAC (Health-ISAC) threat intelligence feeds

The Systems Administrator and Cloud Security Engineer are responsible for monitoring these sources and evaluating applicability to MedCore systems.

### 3.2 Patch Classification and Remediation SLAs

All patches are classified by severity using the CVSS v3.1 base score and contextual factors specific to MedCore's environment. The following remediation SLAs are mandatory:

| Severity | CVSS Score | Active Exploit? | Remediation Deadline |
|----------|-----------|-----------------|----------------------|
| Critical | 9.0 – 10.0 | Any | Within 15 calendar days of discovery |
| Critical | 9.0 – 10.0 | Yes (KEV listed) | Within 7 calendar days of discovery |
| High | 7.0 – 8.9 | Any | Within 30 calendar days of discovery |
| Moderate | 4.0 – 6.9 | No | Within 90 calendar days of discovery |
| Low | 0.1 – 3.9 | No | Within 180 calendar days or next scheduled maintenance |

Patches affecting ePHI processing systems are prioritized at the top of each severity category due to the direct patient safety and regulatory implications.

### 3.3 Patch Testing and Approval

**Test Environment Requirement:**
All patches rated High or above must be tested in the MedCore staging environment before deployment to production, unless an emergency exception is granted per Section 3.5. The staging environment mirrors the production configuration for all critical EHRP components.

**Test Period:**
- Critical patches: Minimum 24-hour test window (waivable for KEV-listed vulnerabilities with CISO approval)
- High patches: Minimum 48-hour test window
- Moderate/Low patches: Included in monthly maintenance window testing

**Approval:**
All production patch deployments require a Change Request submitted through the MedCore Change Management process (MedCore-PROC-CM-001). Emergency patches (Critical/KEV) follow the Emergency Change process.

### 3.4 Patch Deployment

**Standard Deployment Windows:**
Routine patch deployment for production systems occurs during approved maintenance windows:
- Cloud infrastructure (AWS): Sundays, 2:00 AM – 5:00 AM EST
- On-premises servers: Sundays, 2:00 AM – 5:00 AM EST (same window, coordinated)
- Workstations: Tuesday and Thursday, 8:00 PM – 11:00 PM EST

**Automated Patching:**
AWS Systems Manager Patch Manager automates patch deployment for cloud instances during approved windows. Patch baselines are defined and approved by the Systems Administrator and Cloud Security Engineer.

**Verification:**
After patch deployment, the Systems Administrator verifies:
- Patch was successfully applied (scan confirmation)
- System rebooted if required
- All system functions operating normally
- Patch compliance scan result updated in Qualys

### 3.5 Emergency Patch Process

For Critical vulnerabilities with known active exploitation (CISA KEV listed or confirmed threat intelligence):

1. ISSO notified immediately upon identification
2. CISO approves emergency change within 4 hours
3. Abbreviated testing in staging environment (minimum 2 hours, or waived by CISO for imminent threat)
4. Emergency deployment outside standard maintenance window
5. Post-deployment verification within 2 hours
6. Full change documentation completed within 24 hours of deployment

### 3.6 Patch Deferral and Exceptions

Patches may be deferred beyond SLA only with documented CISO approval and a compensating control plan:
- Deferral requests must include business/technical justification and risk assessment
- All deferred patches become POA&M items tracked by the ISSO
- Maximum deferral period: 30 days for Critical, 60 days for High (no extensions without AO awareness)
- Deferred patches must have compensating controls documented and implemented

### 3.7 End-of-Life Software

Software that has reached vendor end-of-life (EOL) with no available patches is treated as a HIGH risk finding:
- EOL software must be documented in the system inventory with planned replacement date
- A POA&M item must be created for all EOL software in production
- EOL software must be isolated to the greatest extent possible until replaced
- The CISO must be notified of any EOL software handling ePHI

### 3.8 Patch Compliance Reporting

The ISSO reports patch compliance status monthly as part of the Continuous Monitoring program:
- Percentage of systems patched within SLA by severity category
- Number and list of patches overdue beyond SLA (target: 0)
- Deferred patches and associated POA&M items
- AWS Config rule compliance for patch-related rules

---

## 4. Roles and Responsibilities

| Role | Responsibility |
|------|---------------|
| Systems Administrator | Monitor patch sources; test, deploy, and verify patches (on-premises) |
| Cloud Security Engineer | Manage AWS patch baselines; deploy and verify cloud patches; AWS Inspector review |
| ISSO | Monitor patch compliance; manage POA&M for deferred/overdue patches; report monthly |
| CISO | Approve emergency patches; approve deferrals; escalate to AO for significant exceptions |
| System Owner | Provide maintenance window approval for clinical systems; accept risk for deferrals |
| Change Advisory Board | Review and approve standard change requests for patch deployments |

---

## 5. Related Documents

- POL-CM-003: Change Management Policy
- POL-VM-001: Vulnerability Management Policy
- MedCore Patch Management Procedures: MedCore-PROC-CM-002
- EHRP SSP — SI-2 Control Implementation

---

## 6. Revision History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 3.1 | January 2026 | J. Steele, CISO | Added KEV-specific 7-day SLA; updated emergency patch process; added EOL section |
| 3.0 | January 2025 | A. Osei, ISSO | Full rewrite aligned to CVSS v3.1; updated automation section for AWS Systems Manager |
| 2.4 | January 2024 | T. Bridwell | Updated maintenance windows; added cloud patching procedures |

---

*MedCore Health Systems — INTERNAL*
*POL-CM-002 v3.1 | Effective January 15, 2026*
