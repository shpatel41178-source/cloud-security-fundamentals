# Cloud Security Audit Checklist

A practical checklist covering the three areas most cloud misconfigurations occur in: **IAM, storage, and networking**. Written to be usable against AWS, GCP, or Azure with minor naming adjustments.

## 1. Identity & Access Management (IAM)

- [ ] No use of root/owner account for daily operations
- [ ] Multi-factor authentication (MFA) enabled for all privileged accounts
- [ ] No wildcard permissions (`*:*` or equivalent) on IAM policies unless explicitly justified
- [ ] Roles follow least privilege — access matches job function, not convenience
- [ ] Unused IAM users/roles/service accounts are identified and removed
- [ ] Access keys are rotated on a defined schedule
- [ ] Group-based (not individual) permission assignment where possible

## 2. Storage Security

- [ ] No storage buckets (S3 / Cloud Storage / Blob) with public read/write access unless intentional
- [ ] Encryption at rest enabled by default
- [ ] Encryption in transit enforced (HTTPS/TLS only)
- [ ] Versioning enabled on buckets holding critical data
- [ ] Logging enabled for storage access (who read/wrote what, and when)
- [ ] Lifecycle policies configured to avoid unnecessary long-term exposure of stale data

## 3. Network Security

- [ ] Security groups / firewall rules deny-by-default, allow only required ports
- [ ] No SSH (22) or RDP (3389) open to `0.0.0.0/0`
- [ ] Private subnets used for databases and internal services
- [ ] VPC flow logs / network logging enabled
- [ ] Load balancers terminate TLS, not passed through in plaintext

## 4. Monitoring & Logging

- [ ] Centralized audit logging enabled (CloudTrail / Cloud Audit Logs / Azure Activity Log)
- [ ] Alerts configured for high-risk events (root login, IAM policy changes, security group changes)
- [ ] Log retention meets compliance/organizational requirements
- [ ] Logs are protected from tampering (write-once or shipped to a separate account/project)

## 5. General Hygiene

- [ ] Regular patching schedule for any self-managed compute resources
- [ ] Tagging/labeling in place so ownership of every resource is clear
- [ ] Documented incident response plan exists and is known to the team

---

**How to use this:** Treat each checked item as a finding to report on, not just a box to tick. In an actual audit, each unchecked item becomes a line in a findings report with a suggested remediation and priority (High/Medium/Low).
