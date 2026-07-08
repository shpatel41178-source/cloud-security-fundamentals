# CIA Triad — Mapped to Real Cloud Services

The CIA Triad (**Confidentiality, Integrity, Availability**) is the foundational model for information security. This document maps each principle to concrete AWS, GCP, and Azure services, rather than treating it as an abstract concept.

## Confidentiality
*Ensuring only authorized users/systems can access data.*

| Cloud | Services that enforce confidentiality |
|---|---|
| AWS | IAM (identity policies), KMS (encryption keys), S3 bucket policies, VPC security groups |
| GCP | Cloud IAM, Cloud KMS, VPC firewall rules, Private Google Access |
| Azure | Azure AD, Azure Key Vault, Network Security Groups (NSGs) |

**Example control:** Restricting an S3 bucket to a specific IAM role instead of allowing public read access — a single misconfigured checkbox is one of the most common real-world confidentiality failures.

## Integrity
*Ensuring data isn't altered or corrupted, accidentally or maliciously.*

| Cloud | Services that enforce integrity |
|---|---|
| AWS | S3 Object Versioning, CloudTrail (audit logging), AWS Config (config drift detection) |
| GCP | Cloud Audit Logs, Object Versioning in Cloud Storage, Binary Authorization |
| Azure | Azure Monitor, Activity Log, Blob storage immutability policies |

**Example control:** Enabling versioning on a storage bucket so any unauthorized modification can be detected and rolled back, paired with audit logs showing *who* made the change.

## Availability
*Ensuring systems and data remain accessible when needed.*

| Cloud | Services that enforce availability |
|---|---|
| AWS | Auto Scaling, Elastic Load Balancing, Multi-AZ deployments, Route 53 failover |
| GCP | Managed Instance Groups, Cloud Load Balancing, multi-region storage |
| Azure | Azure Load Balancer, Availability Zones, Azure Site Recovery |

**Example control:** Multi-AZ database deployment so a single data center outage doesn't take the application down — directly supports uptime SLAs.

## Putting it together: a mini scenario

Imagine auditing a cloud-hosted web application:

1. **Confidentiality check** — Are IAM roles following least privilege? Is the database publicly accessible when it shouldn't be?
2. **Integrity check** — Is audit logging enabled? Would you know if someone modified a file outside the normal deploy pipeline?
3. **Availability check** — Is there redundancy across availability zones? Is there a tested backup/recovery plan?

This three-question framework is a simplified version of what a SOC or cloud security analyst actually walks through during a security review.
