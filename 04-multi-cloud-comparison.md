# Multi-Cloud Security Service Comparison

A side-by-side reference of equivalent security services across AWS, GCP, and Azure — useful for interviews that test multi-cloud awareness.

| Function | AWS | GCP | Azure |
|---|---|---|---|
| Identity & Access Management | IAM | Cloud IAM | Azure Active Directory (Entra ID) |
| Key Management | KMS | Cloud KMS | Key Vault |
| Network Isolation | VPC | VPC | Virtual Network (VNet) |
| Firewall / Traffic Control | Security Groups, NACLs | VPC Firewall Rules | Network Security Groups (NSGs) |
| Audit Logging | CloudTrail | Cloud Audit Logs | Activity Log |
| Config Compliance Monitoring | AWS Config | Security Command Center | Azure Policy |
| DDoS Protection | AWS Shield | Cloud Armor | Azure DDoS Protection |
| Secrets Management | Secrets Manager | Secret Manager | Key Vault |
| Object Storage | S3 | Cloud Storage | Blob Storage |
| Threat Detection | GuardDuty | Security Command Center (Premium) | Microsoft Defender for Cloud |

## Notable differences worth knowing

- **AWS IAM** is resource-attached (policies attach to users/roles/resources); **GCP IAM** uses a resource hierarchy (org → folder → project) where permissions inherit downward — a common interview trip-up point.
- **Azure's identity system (Entra ID)** is more deeply integrated with on-prem Active Directory, making it a common choice for enterprises already running Windows Server infrastructure.
- **GCP's Security Command Center** and **Azure's Defender for Cloud** both act as centralized posture-management dashboards, while AWS spreads similar functionality across GuardDuty, Config, and Security Hub.

## Why this comparison matters

Interviewers frequently ask "how would you do X in a different cloud" to test whether a candidate understands the *underlying security concept* rather than memorized console clicks. Knowing the AWS term is rarely enough — being able to say "that's the GCP equivalent of an NSG" shows real conceptual understanding.
