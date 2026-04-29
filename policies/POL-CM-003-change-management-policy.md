# Change Management Policy
## MedCore Health Systems

---

**Policy ID:** POL-CM-003
**Version:** 2.3
**Effective Date:** January 15, 2026
**Review Date:** January 2027
**Policy Owner:** Jonathan E. Steele, CISO
**Approved By:** Marcus T. Hargrove, CEO
**NIST Control Mapping:** CM-3, CM-5, CM-9, SA-10
**HIPAA Mapping:** 45 CFR §164.308(a)(8) — Evaluation; §164.312(a)(1) — Access Controls
**Classification:** INTERNAL

---

## 1. Purpose

This Change Management Policy establishes the requirements for planning, reviewing, approving, testing, implementing, and documenting changes to MedCore Health Systems' information technology systems. Controlled change management protects the security, integrity, and availability of ePHI and ensures that changes do not introduce vulnerabilities or disrupt patient care operations.

---

## 2. Scope

This policy applies to all changes to hardware, software, configurations, network infrastructure, and procedures that could affect any MedCore information system — including cloud-hosted, on-premises, and hybrid systems within the EHRP authorization boundary.

---

## 3. Change Categories

### Standard Change
Pre-approved, low-risk, routine changes with a defined, tested implementation procedure.
- Examples: Monthly OS patches (within approved patch baselines), minor application configuration updates, user access provisioning
- Approval: Pre-approved by CAB; no individual approval required for each occurrence
- Lead time: Can be scheduled as needed within approved maintenance windows

### Normal Change
A change that requires individual review and approval before implementation.
- Examples: New software deployment, firewall rule modifications, new integrations, significant configuration changes
- Approval: Change Advisory Board (CAB) review and approval required
- Lead time: Minimum 5 business days before planned implementation date

### Emergency Change
An unplanned change required urgently to restore service or address an active security threat.
- Examples: Emergency security patching of actively exploited vulnerability, hotfix for patient-impacting production issue
- Approval: CISO (security emergency) or CIO (operational emergency) approval required before implementation
- Lead time: As short as possible; minimum notification to ISSO before implementation
- Post-implementation: Full change documentation required within 24 hours

### Significant Change (Security Impact)
A change that substantially alters the security posture of an ePHI system.
- Examples: Adding a new system to the EHRP authorization boundary, major architecture redesign, new external interconnection
- Approval: ISSO conducts Security Impact Analysis (SIA); CISO approval; AO notification required before implementation
- Lead time: Minimum 10 business days; SIA must be completed before CAB review

---

## 4. Change Management Process

### 4.1 Change Request Submission

All Normal and Significant changes require a Change Request (CR) submitted in ServiceNow (change.medcorehealthsystems.internal). The CR must include:
- Description of the change and business justification
- Systems and components affected
- Risk assessment (Low / Medium / High)
- Implementation plan with step-by-step instructions
- Rollback plan (mandatory for production changes)
- Testing results from non-production environment
- Scheduled implementation window
- Requestor and technical owner

### 4.2 Security Impact Analysis (SIA)

For all Significant Changes and any Normal Change affecting ePHI systems, the ISSO must complete a Security Impact Analysis before the change proceeds to CAB:

**SIA Evaluates:**
- Does the change alter the system's authorization boundary?
- Does the change affect existing security controls?
- Does the change introduce new vulnerabilities or risks?
- Does the change require updates to the SSP, POA&M, or other RMF documentation?
- Does the change require AO notification or re-authorization?

**SIA Outcomes:**
- No security concern: Change proceeds to standard CAB
- Minor security concern: Additional controls required; change proceeds with conditions
- Significant security concern: Full ISSO review; may require AO notification; change may be delayed
- Re-authorization trigger: AO must approve before implementation

### 4.3 Change Advisory Board (CAB)

The CAB meets weekly (Wednesdays, 10:00 AM EST) to review Normal and Significant change requests.

**CAB Membership:**
- CISO (Chair for security-impacting changes)
- CIO / System Owner
- ISSO
- Lead Systems Administrator
- Cloud Security Engineer
- Clinical Operations Representative (for changes affecting patient-facing systems)

**CAB Decisions:**
- Approve: Change may proceed as submitted
- Approve with conditions: Change may proceed with specific modifications or additional controls
- Defer: Change requires additional information or testing before re-submission
- Reject: Change is denied; requestor may resubmit after addressing concerns

### 4.4 Testing Requirements

All Normal and Significant changes must be tested in the EHRP staging environment before production deployment:
- Staging environment mirrors production configuration for all critical components
- Testing must confirm the change achieves its intended purpose without breaking existing functionality
- Security controls must be verified to remain effective after the change
- Test results must be documented in the Change Request

### 4.5 Implementation and Documentation

- All changes must be implemented during approved maintenance windows unless emergency
- Implementation must follow the approved change plan step-by-step
- Any deviation from the plan must be immediately communicated to the ISSO
- Post-implementation verification must confirm successful completion
- Change record must be updated with actual implementation time, outcome, and any issues encountered

### 4.6 Rollback

Every production change must have a documented and tested rollback plan:
- Rollback plan must be executed if the change fails or causes unexpected issues
- Decision to rollback must be made within the maintenance window timeframe
- Rollback execution must be documented in the Change Request

---

## 5. Unauthorized Changes

Changes implemented without following this policy are considered unauthorized changes and are treated as security incidents:
- The ISSO will investigate all unauthorized changes detected through SIEM monitoring or AWS Config
- Unauthorized changes to ePHI systems are automatically escalated to the CISO
- Personnel responsible for unauthorized changes are subject to disciplinary action
- All unauthorized changes must be reversed or remediated immediately

---

## 6. Roles and Responsibilities

| Role | Responsibility |
|------|---------------|
| Change Requestor | Submit complete change requests; implement approved changes as planned |
| ISSO | Conduct SIAs; participate in CAB; monitor for unauthorized changes |
| CISO | Chair CAB; approve Emergency and Significant changes; AO notification for re-auth triggers |
| CAB Members | Review and approve change requests |
| Systems Administrator / Cloud Eng. | Implement and document approved changes |
| System Owner | Approve changes affecting their system; accept residual risk |

---

## 7. Related Documents

- POL-CM-002: Patch Management Policy
- POL-VM-001: Vulnerability Management Policy
- EHRP SSP — CM-3, CM-5 Implementations
- MedCore Change Request Form: ServiceNow Change Module

---

## 8. Revision History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 2.3 | January 2026 | J. Steele, CISO | Added Significant Change category and SIA requirements; updated CAB membership; aligned with NIST RMF re-authorization triggers |
| 2.2 | January 2025 | A. Osei, ISSO | Updated emergency change process; added unauthorized change section |

---

*MedCore Health Systems — INTERNAL*
*POL-CM-003 v2.3 | Effective January 15, 2026*
