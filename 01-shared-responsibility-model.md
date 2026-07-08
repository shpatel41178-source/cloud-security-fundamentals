# Shared Responsibility Model

The Shared Responsibility Model defines which security tasks belong to the **cloud provider** and which belong to the **customer**. The split changes depending on the service model — IaaS, PaaS, or SaaS.

## The core idea

```
Provider is always responsible for: "Security OF the cloud"
Customer is always responsible for: "Security IN the cloud"
```

The provider secures the physical data centers, hardware, and the core infrastructure running the service. The customer secures their data, access controls, and how they configure the services they use.

## Responsibility by service model

### IaaS (Infrastructure as a Service)
Example: AWS EC2, GCP Compute Engine, Azure Virtual Machines

| Layer | Responsible party |
|---|---|
| Physical data center, hardware | Provider |
| Networking infrastructure | Provider |
| Hypervisor / virtualization | Provider |
| Operating system patching | **Customer** |
| Network firewall configuration | **Customer** |
| Application-level security | **Customer** |
| Data encryption & classification | **Customer** |
| Identity & access management | **Customer** |

Customer has the most responsibility here since they control almost everything above the physical hardware.

### PaaS (Platform as a Service)
Example: AWS Elastic Beanstalk, GCP App Engine, Azure App Service

| Layer | Responsible party |
|---|---|
| Physical infrastructure | Provider |
| OS patching & runtime | Provider |
| Middleware | Provider |
| Application code | **Customer** |
| Data | **Customer** |
| Access control to the app | **Customer** |

The provider takes on OS and runtime management, so the customer's responsibility shrinks to their code, data, and identity settings.

### SaaS (Software as a Service)
Example: Google Workspace, Microsoft 365, Salesforce

| Layer | Responsible party |
|---|---|
| Everything below the application | Provider |
| Application configuration | Provider (mostly) |
| User access management | **Customer** |
| Data classification & sharing settings | **Customer** |

Customer responsibility is smallest here — mainly who has access and how data is shared.

## Why this matters for security analysts

Most real-world cloud breaches (like exposed S3 buckets or overly permissive IAM roles) happen on the **customer** side of this line — not because the provider's infrastructure failed. A security analyst's job is largely about correctly executing the customer's half of this model: configuring access, monitoring for misconfigurations, and enforcing least privilege.

## Quick reference diagram

```
IaaS:  [Customer: OS, App, Data, IAM, Network config]
       [Provider: Hardware, Virtualization, Physical security]

PaaS:  [Customer: App, Data, IAM]
       [Provider: OS, Runtime, Middleware, Hardware]

SaaS:  [Customer: Access management, Data sharing settings]
       [Provider: Everything else]
```
