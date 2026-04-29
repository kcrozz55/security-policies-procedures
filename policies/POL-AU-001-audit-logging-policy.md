# Audit Logging and Accountability Policy
## MedCore Health Systems

---

**Policy ID:** POL-AU-001
**Version:** 2.4
**Effective Date:** January 15, 2026
**Review Date:** January 2027
**Policy Owner:** Jonathan E. Steele, CISO
**Approved By:** Marcus T. Hargrove, CEO
**NIST Control Mapping:** AU-1, AU-2, AU-3, AU-6, AU-9, AU-11, AU-12
**HIPAA Mapping:** 45 CFR §164.312(b) — Audit Controls; §164.308(a)(1)(ii)(D) — Information System Activity Review
**Classification:** INTERNAL

---

## 1. Purpose

This Audit Logging and Accountability Policy establishes the requirements for capturing, protecting, reviewing, and retaining audit logs across all MedCore Health Systems information systems. Audit logs are essential for detecting security incidents, supporting forensic investigations, demonstrating regulatory compliance, and maintaining individual accountability for actions involving ePHI.

---

## 2. Scope

This policy applies to all MedCore-owned and managed information systems that process, store, or transmit ePHI or support MedCore's business operations, including cloud-hosted, on-premises, and hybrid systems.

---

## 3. Policy Statement

### 3.1 Audit Events — Required Logging

All MedCore information systems must log the following security-relevant events:

**Authentication and Access Events:**
- Successful and failed login attempts (user ID, timestamp, source IP, system)
- Multi-factor authentication challenges and outcomes
- Account lockouts and unlocks
- Privileged account usage and administrative actions
- Session creation and termination

**ePHI Access Events:**
- All access to patient records (view, create, modify, delete)
- Bulk queries or exports of ePHI data
- Access to special categories of ePHI (mental health, substance abuse, HIV)
- Break-glass emergency account access

**System and Administrative Events:**
- User account lifecycle events (creation, modification, disablement, deletion)
- Permission and access control changes
- Security control configuration changes
- System startup, shutdown, and restart events
- Application error conditions and exceptions

**Network and Security Events:**
- Firewall allow and deny events (inbound/outbound on critical paths)
- VPN connection events
- Network intrusion detection system alerts
- Security tool alerts (EDR, SIEM, vulnerability scanner findings)

### 3.2 Audit Log Content — Required Fields

Each audit log entry must contain at minimum:
- Timestamp (synchronized with NTP; UTC-based)
- User identity (user ID or service account name)
- Event type and description
- Source IP address or system identifier
- Affected resource (file, record, system, account)
- Success or failure indicator
- System/application generating the log

### 3.3 Audit Log Protection

Audit logs must be protected against unauthorized access, modification, and deletion:
- Log data must be forwarded to the centralized SIEM (Splunk) in near real-time
- SIEM access is restricted to authorized SOC analysts (read-only) and the ISSO (read/write for configuration)
- AWS CloudTrail logs are delivered to an S3 bucket with Object Lock (WORM) enabled — deletion is blocked at the bucket policy level
- Cryptographic integrity protection (HMAC-SHA-256) is applied to log records at SIEM ingestion
- Local log modification on source systems is detected via SIEM — tampering generates an immediate alert
- No user, including administrators, has the ability to modify or delete audit logs from the SIEM

### 3.4 Audit Log Retention

All audit logs must be retained for the following minimum periods:

| Log Category | Minimum Retention | Rationale |
|-------------|------------------|-----------|
| ePHI access logs | 7 years | HIPAA (6 yr min) + MedCore records retention policy |
| Authentication logs | 7 years | Consistent with ePHI access; investigation support |
| System event logs | 7 years | Forensic investigation support |
| Security alert logs | 7 years | Incident investigation and regulatory defense |
| Network flow logs (VPC) | 2 years | Threat hunting and incident response |

Active logs (current year + 1) are maintained in Splunk for immediate query access. Logs older than 2 years are archived to AWS S3 Glacier Instant Retrieval with a 4-hour retrieval SLA.

### 3.5 Audit Log Review

Audit logs must be reviewed on the following schedule:

| Review Type | Frequency | Responsible | Focus Areas |
|------------|-----------|------------|------------|
| Automated alerting | Continuous | SOC (SIEM alerts) | High-priority security events |
| Manual alert triage | Daily | SOC Analyst | SIEM queue; unresolved alerts |
| ePHI access anomaly review | Weekly | ISSO | Bulk access; off-hours access; unusual patterns |
| Privileged access review | Weekly | ISSO | Admin account activity; unusual privileged actions |
| Full log review summary | Monthly | ISSO | All categories; trends; anomalies; monthly ConMon report |

The ISSO documents monthly log review findings in the Continuous Monitoring monthly report. Anomalies that cannot be explained as legitimate business activity are escalated as security incidents.

### 3.6 Audit Failure Response

If audit logging fails or is interrupted on any ePHI-handling system:
- Alert is generated to the ISSO within 15 minutes of logging interruption
- The ISSO investigates the cause immediately
- If audit capability cannot be restored within 4 hours: CISO is notified
- System continues operating during audit failure for up to 4 hours to support patient care continuity
- If audit failure extends beyond 4 hours: System Owner is consulted about temporary access restriction

---

## 4. Roles and Responsibilities

| Role | Responsibility |
|------|---------------|
| SOC Analysts | Monitor SIEM alerts 24/7; triage daily queue; escalate anomalies to ISSO |
| Cloud Security Engineer | Maintain CloudTrail; SIEM ingestion pipelines; Splunk infrastructure |
| Systems Administrator | Maintain on-premises log forwarding; ensure all systems are sending to SIEM |
| ISSO | Weekly and monthly log review; manage audit program; respond to audit failures |
| CISO | Approve log review policy; receive critical anomaly escalations |
| All System Owners | Ensure their systems are configured to generate required audit events |

---

## 5. Related Documents

- POL-AC-001: Access Control Policy
- POL-IR-001: Incident Response Policy
- EHRP SSP — AU Family Control Implementations
- MedCore EHRP ConMon Strategy — step-6-monitor/continuous-monitoring-strategy.md

---

## 6. Revision History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 2.4 | January 2026 | J. Steele, CISO | Added HMAC integrity protection requirement; updated retention table; added audit failure response section |
| 2.3 | January 2025 | A. Osei, ISSO | Updated SIEM platform references; added ePHI access anomaly review requirement |

---

*MedCore Health Systems — INTERNAL*
*POL-AU-001 v2.4 | Effective January 15, 2026*
