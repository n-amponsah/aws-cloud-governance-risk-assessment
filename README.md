# aws-cloud# AWS Cloud Governance Risk Assessment
Configuration Review & NIST Control Mapping

---

## Executive Summary

This project documents a configuration-based governance assessment conducted within an AWS environment. The objective was to identify common cloud security misconfigurations and align findings with NIST SP 800-53 control families. The assessment focused on identity management, storage governance, and network exposure risks.

---

## Scope of Assessment

Services evaluated:

- IAM (Identity and Access Management)
- Amazon S3
- EC2 Security Groups

Region: us-east-1  
Assessment Type: Configuration Review  
Framework Reference: NIST SP 800-53 (High-Level Mapping)

---

## Findings Summary

| Finding | Risk Level | Control Area | Status |
|----------|------------|--------------|--------|
| IAM user without MFA | Medium | AC-2, IA-2 | Remediated |
| S3 governance gaps | Medium | CP-9, AU-2, SC-28 | Remediated |
| Open SSH exposure (0.0.0.0/0) | High | SC-7 | Remediated |

---

## Detailed Findings

### Finding 1 – IAM User Without MFA

**Risk Description:**  
An IAM user was configured with console access but without multi-factor authentication (MFA).

**Impact:**  
Increased likelihood of unauthorized access if credentials are compromised.

**Control Mapping:**  
- AC-2 (Account Management)  
- IA-2 (Identification and Authentication)

**Recommendation:**  
Enforce MFA for all IAM console users and disable unused accounts.
**Evidence:**

![IAM No MFA](./Screen%20Shot%202026-02-17%20at%2010.07.40%20PM.png)

---

### Finding 2 – S3 Governance Gaps

**Risk Description:**  
An S3 bucket was created without versioning or access logging enabled.

**Impact:**  
Reduced ability to recover deleted objects and limited audit visibility.

**Control Mapping:**  
- CP-9 (Information System Backup)  
- AU-2 (Audit Events)  
- SC-28 (Protection of Information at Rest)

**Recommendation:**  
Enable versioning, server access logging, and lifecycle policies.
**Evidence:**

**Evidence:**

![S3 Governance Gap 1](./Screen%20Shot%202026-02-17%20at%2010.13.25%20PM.png)

![S3 Governance Gap 2](./Screen%20Shot%202026-02-17%20at%2010.14.09%20PM.png)

![S3 Governance Gap 3](./Screen%20Shot%202026-02-17%20at%2010.15.20%20PM.png)


---

### Finding 3 – Open SSH Exposure

**Risk Description:**  
A security group allowed inbound SSH (port 22) access from 0.0.0.0/0.

**Impact:**  
Public exposure increases risk of brute-force attacks and unauthorized access attempts.

**Control Mapping:**  
- SC-7 (Boundary Protection)  
- AC-4 (Information Flow Enforcement)

**Recommendation:**  
Restrict SSH access to trusted IP ranges and implement bastion host architecture where appropriate.
**Evidence:**

![Open SSH Security Group 1](./Screen%20Shot%202026-02-17%20at%2010.19.03%20PM.png)

![Open SSH Security Group 2](./Screen%20Shot%202026-02-17%20at%2010.19.53%20PM.png)

---

## Remediation Actions

All identified misconfigurations were remediated after documentation. Test resources were deleted to prevent unnecessary cost exposure.

---

## Key Takeaways

This assessment demonstrates:

- Cloud configuration risk identification
- Governance-focused control mapping
- NIST framework alignment
- Practical AWS security analysis
- Responsible resource lifecycle management
-governance-risk-assessment
