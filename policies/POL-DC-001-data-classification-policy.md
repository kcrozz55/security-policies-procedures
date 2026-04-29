# Data Classification Policy
## MedCore Health Systems

---

**Policy ID:** POL-DC-001
**Version:** 2.5
**Effective Date:** January 15, 2026
**Review Date:** January 2027
**Policy Owner:** Dr. Rachel Feinberg, Privacy Officer
**Co-Owner:** Jonathan E. Steele, CISO
**Approved By:** Marcus T. Hargrove, CEO
**NIST Control Mapping:** MP-1, RA-2, SI-12, AC-3
**HIPAA Mapping:** 45 CFR §164.308(a)(1)(ii)(A) — Risk Analysis; §164.310(d)(1) — Device and Media Controls
**Classification:** INTERNAL

---

## 1. Purpose

This Data Classification Policy establishes a framework for classifying MedCore Health Systems' information assets based on sensitivity, regulatory requirements, and potential impact of unauthorized disclosure, modification, or loss. Proper data classification enables appropriate and consistent security controls to be applied to information throughout its lifecycle — from creation to disposal.

---

## 2. Scope

This policy applies to all MedCore information in any format — electronic, paper, verbal, or other media — created, collected, processed, stored, transmitted, or disposed of by MedCore employees, contractors, business associates, and third parties on behalf of MedCore.

---

## 3. Data Classification Tiers

MedCore classifies all information into one of four tiers:

### Tier 1 — RESTRICTED (Highest Sensitivity)

**Definition:** Information whose unauthorized disclosure would cause severe harm to patients, individuals, or MedCore's legal standing. Disclosure may result in significant regulatory penalties, civil liability, or criminal charges.

**Examples:**
- Electronic Protected Health Information (ePHI) — patient clinical records, diagnoses, treatment plans, medication records, lab results, medical imaging
- Sensitive Categories of ePHI — mental health records, substance abuse treatment records, HIV/AIDS status, genetic information, reproductive health
- Social Security Numbers, financial account numbers, payment card data
- Patient biometric data
- Authentication credentials (passwords, private keys, certificates)
- Security assessment reports and vulnerability details

**Handling Requirements:**
- Access: Strictly limited to individuals with documented need and proper authorization
- Encryption: AES-256 at rest; TLS 1.3 in transit; mandatory — no exceptions
- Storage: Only on MedCore-approved systems; no personal devices, personal cloud storage
- Transmission: Only via encrypted, authorized channels; no personal email
- Printing: Minimize; store in locked cabinets; shred when no longer needed
- Disposal: Secure wipe (NIST 800-88) or physical destruction; documented certificate of destruction

### Tier 2 — CONFIDENTIAL

**Definition:** Information intended for internal use that, if disclosed, could cause moderate harm to MedCore's business operations, competitive position, or personnel.

**Examples:**
- Employee personally identifiable information (name, address, salary, performance reviews)
- Internal financial reports and budget documents
- Business contracts and vendor agreements
- Strategic plans and unreleased product information
- Internal audit findings
- Organizational charts and directory information beyond name/title
- Security policies and procedures (this document)

**Handling Requirements:**
- Access: Internal MedCore personnel with business need; limited third-party sharing under NDA/BAA
- Encryption: Recommended at rest; required in transit and for external sharing
- Storage: MedCore-approved systems; personal device use subject to MDM enrollment
- Transmission: Internal email/messaging acceptable; external sharing requires encryption
- Disposal: Secure delete or shredding

### Tier 3 — INTERNAL

**Definition:** Information for general internal use that is not sensitive but is not intended for public distribution.

**Examples:**
- General business communications
- Internal procedures and work instructions (non-security)
- Staff directories (name, title, department, work phone)
- Meeting notes without sensitive content
- Training materials

**Handling Requirements:**
- Access: All MedCore personnel; limited external sharing with management approval
- Encryption: Not required for internal systems; recommended for external email
- Disposal: Standard deletion; shredding for printed materials

### Tier 4 — PUBLIC

**Definition:** Information approved for public release and already or intended to be publicly available.

**Examples:**
- MedCore public website content
- Published press releases
- Job postings
- Patient-facing educational materials
- Publicly filed regulatory documents

**Handling Requirements:**
- Access: Unrestricted
- No special handling requirements
- Verify accuracy and proper review/approval before public release

---

## 4. Data Classification Responsibilities

### Data Owners
Each MedCore department head is the Data Owner for information created or managed by their department. Data Owners are responsible for:
- Identifying and classifying data within their domain
- Approving access to data under their ownership
- Ensuring data handling requirements are followed
- Participating in data inventory reviews

### Data Stewards
The Privacy Officer (Dr. Rachel Feinberg) and ISSO (Amara Osei) serve as Data Stewards for ePHI and information security-related data respectively. Stewards provide guidance on classification decisions and monitor compliance.

### All Users
All users are responsible for:
- Identifying the classification of information they handle
- Applying the appropriate handling requirements based on classification
- Not downgrading classification without Data Owner approval
- Reporting suspected misclassification or improper handling to the ISSO

---

## 5. Labeling and Marking

**Electronic Documents:** Classified documents should include the classification tier in the document header or footer (e.g., "RESTRICTED — FOR AUTHORIZED USE ONLY" or "CONFIDENTIAL — INTERNAL ONLY").

**Emails:** Emails containing Tier 1 or Tier 2 information should include the classification in the subject line or first line of the body when transmitted outside of secure MedCore systems.

**Physical Documents:** Printed documents containing Tier 1 or Tier 2 information must be labeled on the cover page and stored in a locked location.

---

## 6. Data Inventory

The ISSO maintains a Data Inventory Register identifying the primary data types processed by each MedCore system, including classification tier, data owner, storage locations, and applicable regulatory requirements. The inventory is reviewed annually and updated upon significant system changes.

---

## 7. Related Documents

- POL-PV-001: Privacy and Data Protection Policy
- POL-PV-002: Data Retention and Disposal Policy
- POL-MA-001: Media Protection Policy
- POL-SC-002: Encryption Policy
- MedCore HIPAA Privacy Program

---

## 8. Revision History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 2.5 | January 2026 | R. Feinberg / J. Steele | Added sensitive ePHI categories; updated disposal requirements to reference NIST 800-88; added labeling section |
| 2.4 | January 2025 | R. Feinberg | Clarified Tier 1 examples; added biometric data |
| 2.3 | January 2024 | J. Steele | Initial four-tier framework |

---

*MedCore Health Systems — INTERNAL*
*POL-DC-001 v2.5 | Effective January 15, 2026*
