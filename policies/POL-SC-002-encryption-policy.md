# Encryption and Cryptographic Controls Policy
## MedCore Health Systems

---

**Policy ID:** POL-SC-002
**Version:** 2.1
**Effective Date:** January 15, 2026
**Review Date:** January 2027
**Policy Owner:** Jonathan E. Steele, CISO
**Approved By:** Marcus T. Hargrove, CEO
**NIST Control Mapping:** SC-13, SC-28, SC-8, SC-8(1), IA-7
**HIPAA Mapping:** 45 CFR §164.312(a)(2)(iv) — Encryption and Decryption; §164.312(e)(2)(ii) — Encryption
**Classification:** INTERNAL

---

## 1. Purpose

This Encryption and Cryptographic Controls Policy establishes the requirements for the use of encryption and cryptographic mechanisms to protect the confidentiality and integrity of MedCore Health Systems' information assets, with particular emphasis on electronic Protected Health Information (ePHI). Proper encryption is a foundational control for HIPAA compliance and is essential to preventing unauthorized access to sensitive patient data.

---

## 2. Scope

This policy applies to all MedCore information systems, devices, and communications channels that process, store, or transmit Tier 1 (RESTRICTED) or Tier 2 (CONFIDENTIAL) data as defined in POL-DC-001. It covers encryption of data at rest, data in transit, and cryptographic key management.

---

## 3. Policy Statement

### 3.1 Approved Cryptographic Algorithms

MedCore requires the use of FIPS 140-2 (or FIPS 140-3) validated cryptographic modules for all encryption of ePHI and sensitive data. Only the following algorithms are approved for use on MedCore systems:

**Symmetric Encryption:**
- AES-256 — required for all data at rest encryption
- AES-128 — permitted only for legacy integrations with documented exception; target replacement within 2 years

**Asymmetric Encryption and Key Exchange:**
- RSA-4096 — for key exchange and digital signatures where ECC is not supported
- ECDSA with P-384 or P-256 — preferred for digital signatures
- ECDH with P-384 or P-256 — preferred for key exchange

**Hashing:**
- SHA-384 or SHA-256 — required for all cryptographic hashing operations
- HMAC-SHA-256 — required for message authentication codes

**Transport Layer Security:**
- TLS 1.3 — required for all new implementations
- TLS 1.2 — permitted for legacy integration partners with documented exception; TLS 1.3 upgrade required by December 31, 2026

**Prohibited Algorithms (must not be used):**
- MD5, SHA-1 (except legacy TLS certificate chains — mitigated by TLS configuration)
- DES, 3DES
- RC4, RC2
- TLS 1.0, TLS 1.1, SSL (all versions)
- RSA key sizes below 2048 bits

### 3.2 Encryption at Rest

**Required for all Tier 1 (RESTRICTED) data:**

| System / Storage Type | Required Encryption | Current Implementation |
|----------------------|--------------------|-----------------------|
| Clinical Database (PostgreSQL RDS) | AES-256 using AWS KMS CMK | Enabled — KMS key: mrk-ehrp-db-prod |
| Medical Imaging (S3) | AES-256 SSE-KMS | Enabled — KMS key: mrk-ehrp-imaging-prod |
| Session Cache (ElastiCache/Redis) | AES-256 using AWS KMS | Enabled |
| EC2 Instance Volumes (EBS) | AES-256 using AWS KMS | Enabled — all volumes |
| On-premises servers | AES-256 — BitLocker with TPM 2.0 | Enabled — all servers |
| Workstations (Windows) | AES-256 — BitLocker with TPM 2.0 | Enforced via Group Policy |
| Backup storage (S3 Glacier) | AES-256 SSE-KMS | Enabled |
| Email archives | AES-256 | Enabled — Microsoft Purview |

**Legacy HL7 Interface Engine Exception:**
A documented compensating control exists for the on-premises Legacy HL7 Interface Engine which cannot support native queue encryption (see Tailoring Decisions in EHRP SSP). Data minimization, full-disk encryption, and network isolation are applied as compensating controls.

### 3.3 Encryption in Transit

All transmission of Tier 1 or Tier 2 data must use encrypted channels:
- External-facing web services: TLS 1.3 mandatory; enforced at AWS API Gateway
- Internal service-to-service communication: TLS 1.2 minimum; TLS 1.3 preferred
- VPN connections: IPSec/IKEv2 with AES-256 and SHA-384
- Database connections: TLS required for all application-to-database connections
- External integrations (EDI, HIE, e-Rx): TLS 1.2 minimum; certificate validation required
- Email containing ePHI: S/MIME or secure messaging portal required for external recipients

### 3.4 Cryptographic Key Management

**Key Generation:**
- All cryptographic keys must be generated using a FIPS 140-2 approved random number generator
- AWS KMS customer-managed keys (CMKs) are used for all AWS-hosted encryption; key material is generated within the KMS HSM boundary
- On-premises keys are generated within approved HSM devices or BitLocker TPM modules

**Key Storage:**
- AWS KMS CMKs are stored within the AWS KMS service; key material never leaves the KMS HSM in plaintext
- On-premises private keys are stored in HSM devices or encrypted key stores; never stored in plaintext in files or databases
- Credentials and API keys are stored in AWS Secrets Manager with automatic rotation enabled

**Key Rotation:**
- AWS KMS CMKs: Automatic annual rotation enabled for all MedCore CMKs
- TLS certificates: 1-year maximum validity; automated renewal via AWS Certificate Manager
- Service account secrets: 90-day rotation via AWS Secrets Manager
- Workstation BitLocker keys: Backed up to Active Directory; rotated on device reassignment

**Key Revocation:**
- Compromised keys must be revoked immediately and the ISSO notified
- Revocation procedures are documented in MedCore Key Management Procedures (MedCore-PROC-SC-001)
- All data encrypted with a revoked key must be re-encrypted with a new key within 30 days

**Key Destruction:**
- Keys are destroyed according to NIST SP 800-57 Part 1 guidance when no longer needed
- AWS KMS key deletion has a minimum 7-day waiting period; approval required from CISO

### 3.5 Certificate Management

MedCore maintains a Certificate Inventory Register for all TLS/SSL certificates used on production systems:
- All certificates must be issued by a trusted Certificate Authority (CA)
- Self-signed certificates are prohibited on production systems
- AWS Certificate Manager (ACM) manages certificates for all AWS-hosted endpoints with automatic renewal
- Certificate expiration monitoring is enabled in CloudWatch with 30-day advance alerts
- The ISSO reviews the Certificate Inventory Register quarterly

---

## 4. Roles and Responsibilities

| Role | Responsibility |
|------|---------------|
| Cloud Security Engineer | Manage AWS KMS keys; ACM certificates; enforce cloud encryption policies |
| Systems Administrator | Manage on-premises encryption (BitLocker, database TLS); certificate management for on-prem |
| ISSO | Monitor encryption compliance; manage key management exception register; quarterly certificate review |
| CISO | Approve algorithm exceptions; review key revocation events; approve deviations |
| All Users | Never attempt to disable encryption; never store ePHI in unencrypted locations |

---

## 5. Related Documents

- POL-DC-001: Data Classification Policy
- POL-SC-001: System and Communications Protection Policy
- MedCore Key Management Procedures: MedCore-PROC-SC-001
- EHRP SSP — SC-13, SC-28, SC-8 Implementations

---

## 6. Revision History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 2.1 | January 2026 | J. Steele, CISO | Added TLS 1.3 mandate; prohibited TLS 1.0/1.1; added certificate management section; updated key rotation requirements |
| 2.0 | January 2025 | K. Robertson | Added FIPS 140-2 validation requirement; updated approved algorithm list |

---

*MedCore Health Systems — INTERNAL*
*POL-SC-002 v2.1 | Effective January 15, 2026*
