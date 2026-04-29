# Access Control Policy
## MedCore Health Systems

---

**Policy ID:** POL-AC-001
**Version:** 3.2
**Effective Date:** January 15, 2026
**Review Date:** January 2027
**Policy Owner:** Jonathan E. Steele, CISO
**Approved By:** Marcus T. Hargrove, CEO
**NIST Control Mapping:** AC-1, AC-2, AC-3, AC-6, AC-7, AC-11, AC-14, AC-17, AC-20
**HIPAA Mapping:** 45 CFR §164.308(a)(3), §164.308(a)(4), §164.312(a)(1), §164.312(a)(2)
**Classification:** INTERNAL

---

## 1. Purpose

This Access Control Policy establishes the requirements for managing and controlling access to MedCore Health Systems' information assets, including electronic Protected Health Information (ePHI), information systems, applications, and network resources. The goal is to ensure that access to sensitive information and systems is granted only to authorized individuals based on legitimate business need, and that such access is appropriately managed throughout the user's relationship with MedCore.

---

## 2. Scope

This policy applies to all MedCore employees, contractors, business associates, and third parties who require access to MedCore information systems or data. It governs access to all MedCore-managed systems, including cloud-based systems (AWS GovCloud), on-premises systems, and any shared systems operated under formal agreements.

---

## 3. Policy Statement

### 3.1 Access Control Principles

All access to MedCore information systems and data is governed by the following core principles:

**Least Privilege:** Users are granted only the minimum level of access necessary to perform their assigned job functions. No user shall have greater access than required by their role.

**Need to Know:** Access to ePHI and sensitive data is granted only to individuals with a documented business need to access that information in performance of their duties.

**Separation of Duties:** Incompatible functions are divided among multiple individuals to prevent fraud and error. No single individual controls all aspects of a critical process.

**Individual Accountability:** All access is tied to a unique, individually identified account. Shared accounts are prohibited except for documented, approved emergency break-glass scenarios.

### 3.2 Account Management

**Account Provisioning:**
- All user accounts must be formally requested and approved before being created
- Access requests must include the requestor's name, role, business justification, and required access level
- Privileged access requests require additional approval from the ISSO and system owner
- Accounts are provisioned with the minimum permissions required and expanded only as documented needs arise

**Account Types:**
- Individual user accounts — standard access for named employees and contractors
- Privileged/administrative accounts — elevated access for IT and security personnel; separate from daily-use accounts
- Service accounts — non-interactive accounts for applications and automated processes
- Temporary accounts — time-limited accounts for contractors, visitors, or temporary staff (maximum 90 days)
- Emergency break-glass accounts — documented, procedurally controlled accounts for use only during system outages

**Account Review:**
- All active accounts are reviewed quarterly by account owners and the IAM Administrator
- Privileged accounts are reviewed monthly
- Accounts with 60 consecutive days of inactivity are flagged for review and potential disablement
- Temporary and contractor accounts automatically expire at the agreed end date

**Account Termination:**
- Standard user accounts must be disabled within 24 hours of employment or contract termination
- High-risk terminations (involuntary, HR-flagged) require account disablement within 1 hour of notification
- The ISSO and IAM Administrator must be notified immediately for all terminations involving privileged access

### 3.3 Privileged Access Management

Privileged accounts carry elevated risk and are subject to additional controls:

- All privileged actions must be performed using a separately named privileged account, not the user's daily account
- Privileged access sessions are logged and monitored; logs are reviewed weekly by the ISSO
- Multi-Factor Authentication (MFA) using FIDO2 hardware security keys is required for all privileged accounts
- Privileged accounts may not be used for general email, web browsing, or non-administrative tasks
- Remote privileged access is permitted only through the MedCore VPN and requires MFA

### 3.4 Multi-Factor Authentication (MFA)

MFA is required for all user access to MedCore systems:

- All standard users: TOTP-based authenticator (Okta Verify) as minimum
- All privileged users: FIDO2 hardware security key (YubiKey or equivalent) required
- All remote access: MFA required before VPN connection is established
- All cloud console access: MFA required at authentication
- Service accounts: certificate-based or API key authentication; MFA exception tracked in exception register

### 3.5 Session Management

- Workstations must lock automatically after 10 minutes of inactivity (3 minutes in patient-facing areas)
- Users must manually lock workstations before leaving them unattended
- Interactive sessions are terminated after 8 hours for standard users; 4 hours for privileged sessions
- Remote sessions are terminated after 30 minutes of inactivity

### 3.6 Remote Access

- Remote access to MedCore systems is permitted only via the authorized VPN with MFA
- Users must ensure their device meets MedCore security requirements before connecting remotely
- Public Wi-Fi networks must not be used to access MedCore systems without VPN protection
- Remote access is subject to the same monitoring and access controls as on-site access

### 3.7 Third-Party and Vendor Access

- Third-party access must be formally requested, documented in an access agreement, and approved by the System Owner and ISSO
- Third-party accounts are temporary (maximum 90 days) and subject to the same lifecycle controls as employee accounts
- Vendor access for maintenance purposes must be scheduled, supervised or logged, and terminated immediately upon completion
- Remote vendor access must use MedCore-controlled access paths (VPN or jump server); direct VPN from vendor networks is not permitted without CISO approval

---

## 4. Roles and Responsibilities

| Role | Responsibility |
|------|---------------|
| All Users | Protect credentials; report unauthorized access attempts; use minimum necessary access |
| Managers | Initiate access requests; notify HR/ISSO promptly on terminations |
| IAM Administrator | Provision, maintain, and review accounts; enforce access policy technically |
| ISSO | Oversee access control program; conduct audits; manage exceptions |
| CISO | Approve policy; set standards; review privileged access exceptions |
| System Owner | Approve access requests for their system; participate in quarterly reviews |

---

## 5. Compliance and Enforcement

Violations of this policy may result in disciplinary action up to and including termination. Access violations involving ePHI may also trigger HIPAA breach assessment and regulatory notification requirements. The ISSO will investigate all suspected access violations and maintain records of findings.

---

## 6. Exceptions

Exception requests must be submitted via the Policy Exception Request Form (MedCore-FORM-POL-001) to the ISSO and approved by the CISO. All exceptions are time-limited and subject to compensating controls.

---

## 7. Related Documents

- POL-IA-001: Identification and Authentication Policy
- POL-RA-002: Remote Access Policy
- POL-AU-001: Audit Logging and Accountability Policy
- POL-TP-001: Third-Party Risk Management Policy
- EHRP System Security Plan — AC Control Family

---

## 8. Revision History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 3.2 | January 2026 | J. Steele, CISO | Updated MFA requirements; added FIDO2 mandate for privileged accounts; quarterly review cycle formalized |
| 3.1 | January 2025 | A. Osei, ISSO | Added third-party access section; updated session timeout values |
| 3.0 | January 2024 | J. Steele, CISO | Full rewrite aligned to NIST SP 800-53 Rev 5 |

---

*MedCore Health Systems — INTERNAL*
*POL-AC-001 v3.2 | Effective January 15, 2026*
