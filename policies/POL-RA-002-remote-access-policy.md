# Remote Access Policy
## MedCore Health Systems

---

**Policy ID:** POL-RA-002
**Version:** 3.1
**Effective Date:** January 15, 2026
**Review Date:** January 2027
**Policy Owner:** Jonathan E. Steele, CISO
**Approved By:** Marcus T. Hargrove, CEO
**NIST Control Mapping:** AC-17, AC-17(1), AC-17(2), AC-17(3), IA-2, SC-8
**HIPAA Mapping:** 45 CFR §164.312(a)(2)(iii) — Automatic Logoff; §164.312(e) — Transmission Security
**Classification:** INTERNAL

---

## 1. Purpose

This Remote Access Policy establishes the requirements for securely accessing MedCore Health Systems' information resources from locations outside MedCore-controlled facilities. Remote access introduces elevated security risks, particularly for systems handling ePHI. This policy ensures that remote access is implemented and used in a manner that maintains the confidentiality, integrity, and availability of MedCore data.

---

## 2. Scope

This policy applies to all individuals who access MedCore systems remotely, including employees, contractors, business associates, and vendors. It covers all remote access methods including VPN, remote desktop, cloud console access, and mobile device access.

---

## 3. Policy Statement

### 3.1 Authorized Remote Access Methods

The following are the only authorized methods for remotely accessing MedCore systems:

| Method | Use Case | MFA Required | Device Requirement |
|--------|----------|--------------|-------------------|
| MedCore VPN (GlobalProtect) | General remote access to on-premises resources | Yes — TOTP or hardware key | MedCore-managed or MDM-enrolled |
| AWS Console / CLI (with SSO) | Cloud infrastructure management | Yes — hardware key for privileged roles | MedCore-managed preferred |
| Citrix Virtual Desktop (Tier 2 access) | Remote clinical application access for authorized users | Yes — TOTP minimum | Any device with MDM profile or MedCore VPN |
| Approved Remote Support Tool (BeyondTrust) | IT support and vendor maintenance | Yes — session-specific code | MedCore-managed |

All other remote access methods are prohibited, including but not limited to: consumer-grade remote desktop applications (TeamViewer personal, AnyDesk, Chrome Remote Desktop without IT oversight), personal VPN services, and direct RDP or SSH from the internet.

### 3.2 Device Requirements

**MedCore-Managed Devices:**
- Must have current MedCore security agent (CrowdStrike Falcon EDR) installed and operational
- Must have current OS patches applied (no more than 30 days behind)
- Must have disk encryption enabled (BitLocker or FileVault)
- Must have screen lock enabled with 10-minute timeout

**Personally Owned Devices (BYOD):**
- BYOD access is limited to Citrix Virtual Desktop for reading email and non-ePHI applications
- BYOD devices must enroll in MedCore Mobile Device Management (MDM) before access is granted
- ePHI must never be downloaded to or stored on personally owned devices
- Jailbroken or rooted devices are prohibited from accessing any MedCore resources

### 3.3 Authentication Requirements

- All remote access requires Multi-Factor Authentication (MFA) before any connection is established
- VPN connections cannot be established without successful MFA challenge
- MFA tokens must not be shared; users are responsible for the security of their authenticators
- Session tokens expire after 8 hours; re-authentication required for new sessions
- Remote sessions automatically terminate after 30 minutes of inactivity

### 3.4 Network Security Requirements

- Public Wi-Fi (coffee shops, hotels, airports, etc.) must never be used to access MedCore systems without first connecting to the MedCore VPN
- Home networks are permitted but users must ensure their home router uses WPA2 or WPA3 with a strong passphrase
- Users must not connect to MedCore systems via networks known to be untrusted or compromised
- Split tunneling is disabled on the MedCore VPN — all traffic is routed through MedCore when VPN is active

### 3.5 ePHI Handling During Remote Access

- ePHI must not be downloaded to local devices during remote access sessions
- Printing ePHI at home or remote locations is prohibited unless the user has a documented need and an approved secure printing setup
- Screen sharing applications must not be used while ePHI is displayed on screen
- Users must ensure physical privacy when accessing ePHI remotely — screens must not be visible to unauthorized individuals

### 3.6 Vendor and Third-Party Remote Access

- Vendor remote access must be formally requested by a MedCore sponsor, approved by the System Owner and ISSO, and time-limited to the duration of the work
- All vendor remote sessions must be conducted through the BeyondTrust remote support tool, which enforces session recording and real-time monitoring
- Vendors may not access MedCore systems via their own VPN or remote tools
- The ISSO must be notified 24 hours in advance of any scheduled vendor remote maintenance session
- Vendor accounts must be disabled immediately upon completion of the work session

### 3.7 Monitoring of Remote Access

All remote access sessions are logged and monitored:
- VPN connection logs including source IP, user, device, session duration, and data transferred
- Remote session recordings for IT support and vendor sessions via BeyondTrust
- Anomalous remote access patterns (unusual hours, unusual source locations, excessive data transfer) trigger SIEM alerts to the SOC
- Users have no expectation of privacy during remote access to MedCore systems

---

## 4. Roles and Responsibilities

| Role | Responsibility |
|------|---------------|
| All Users | Use only authorized remote access methods; protect MFA tokens; follow ePHI handling requirements |
| IT Helpdesk | Provision VPN access; enforce device compliance; assist with MDM enrollment |
| Network Engineer | Maintain VPN infrastructure; configure and monitor remote access logs |
| IAM Administrator | Manage remote access accounts; enforce MFA requirements; disable terminated accounts |
| ISSO | Monitor remote access logs; review anomalies; manage vendor access program |
| CISO | Approve exceptions; review policy annually |

---

## 5. Enforcement

Violations of this policy, including accessing MedCore systems via unauthorized methods or failing to protect ePHI during remote work, may result in immediate suspension of remote access privileges and disciplinary action up to and including termination.

---

## 6. Related Documents

- POL-AC-001: Access Control Policy
- POL-SC-002: Encryption Policy
- POL-AU-002: Acceptable Use Policy
- POL-TP-001: Third-Party Risk Management Policy

---

## 7. Revision History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 3.1 | January 2026 | J. Steele, CISO | Added BYOD section; updated vendor access requirements; added BeyondTrust as sole authorized vendor tool |
| 3.0 | January 2025 | A. Osei, ISSO | Full rewrite; added cloud console access section |

---

*MedCore Health Systems — INTERNAL*
*POL-RA-002 v3.1 | Effective January 15, 2026*
