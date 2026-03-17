# AWS S3 Data Breach Simulation & Remediation

## Overview
This project simulates a real cloud security incident involving an exposed Amazon S3 bucket.

I intentionally misconfigured the bucket to allow public access, demonstrated how sensitive data could be accessed without authentication, and then used AWS security services to detect and remediate the issue.

---

## Objectives
- Simulate a cloud data breach using S3 misconfiguration
- Detect the issue using AWS Config
- Remediate the vulnerability using security best practices
- Validate that access is properly restricted

---

## Architecture
- Amazon S3 (data storage)
- AWS Config (compliance monitoring)
- Public bucket policy (attack vector)

---

## Phase 1: Creating the Vulnerability

A publicly accessible S3 bucket was created by disabling block public access settings and applying a permissive bucket policy.

### Evidence

**Public access enabled during bucket creation**
![Bucket Created](images/bucket-created.png)

**Public bucket policy allowing unrestricted access**
![Bucket Policy](images/bucket-policy.png)

---

## Phase 2: Data Exposure

A sensitive file (`employee_data.csv`) was uploaded and made publicly accessible.

### Evidence

**File uploaded to S3**
![Upload](images/upload.png)

**Object URL accessible publicly**
![URL](images/url.png)

**File downloaded without authentication**
![Download](images/download.png)

**Sensitive data exposed**
![Data](images/data.png)

---

## Phase 3: Detection

AWS Config was configured with a managed rule to detect public S3 access.

### Evidence

**Config rule created**
![Rule](images/config-rule.png)

**Non-compliant resource detected**
![Noncompliant](images/noncompliant.png)

**Compliance summary**
![Compliance](images/compliance.png)

---

## Phase 4: Remediation

The vulnerability was resolved by:
- Enabling block public access
- Removing the public bucket policy
- Enabling server-side encryption

### Evidence

**Public access blocked**
![Blocked](images/blocked.png)

**Bucket policy removed**
![Policy Removed](images/policy-removed.png)

**Encryption enabled**
![Encryption](images/encryption.png)

---

## Phase 5: Validation

Access to the object was re-tested and successfully blocked.

### Evidence

**Access denied after remediation**
![Denied](images/access-denied.png)

**AWS Config now shows compliance**
![Compliant](images/compliant.png)

---

## Key Takeaways

- Misconfigured S3 buckets are a leading cause of cloud data breaches
- Public access policies can expose sensitive data instantly
- AWS Config provides effective continuous compliance monitoring
- Enforcing least privilege and encryption is critical for cloud security

---

## Skills Demonstrated

- AWS S3 security configuration
- Cloud misconfiguration exploitation
- AWS Config rule implementation
- Security remediation and hardening
- Incident validation and verification
