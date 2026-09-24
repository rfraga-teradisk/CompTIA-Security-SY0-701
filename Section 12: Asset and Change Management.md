# Asset and Change Management

## Objectives
- Understand why asset inventory is important for security
- Explain asset lifecycle management
- Understand how change management reduces operational and security risk

## Table of Contents

1. [Asset Management](#asset-management)
2. [Asset Inventory](#asset-inventory)
3. [Asset Classification](#asset-classification)
4. [Asset Lifecycle](#asset-lifecycle)
5. [Configuration Management](#configuration-management)
6. [Change Management](#change-management)
7. [Change Records](#change-records)
8. [Security Impact of Poor Change Management](#security-impact-of-poor-change-management)
9. [Key Takeaways](#key-takeaways)

## Asset Management

- **Asset Management:** The process of tracking, protecting, maintaining, and retiring organizational assets.
- Assets include hardware, software, data, cloud services, accounts, licenses, network devices, and business processes.
- Security teams cannot protect systems they do not know exist.

## Asset Inventory

- **Asset Inventory:** A list of assets and their important details.
- Asset inventory supports patching, vulnerability management, incident response, audits, and lifecycle planning.

Common inventory fields:
- Asset name
- Asset ID
- Owner
- Department
- Location
- IP address
- Hostname
- Operating system
- Software installed
- Business function
- Criticality
- Data classification
- Patch status
- Warranty or support status

## Asset Classification

- **Classification:** Labeling assets based on importance, sensitivity, or business impact.
- Classification helps decide how strongly an asset should be protected.

Examples:
- Public
- Internal
- Confidential
- Restricted
- Critical

Example:
- A public website and payroll database should not have the same level of access control because the payroll database contains more sensitive data.

## Asset Lifecycle

Asset lifecycle stages:
1. **Procurement:** Asset is purchased or approved.
2. **Deployment:** Asset is configured and placed into service.
3. **Maintenance:** Asset is patched, monitored, and supported.
4. **Review:** Ownership, access, and configuration are checked.
5. **Decommissioning:** Asset is removed from active use.
6. **Disposal:** Asset is securely wiped, destroyed, recycled, or returned.

**Decommissioning** retires an asset or service: remove its access and network exposure, preserve required records or data, update inventory and dependencies, and sanitize storage before reuse or disposal. Personnel **offboarding** handles a person's departure and access; it may include collecting assigned assets, but the processes have different scopes. See [Personnel Offboarding](<Section 17: Identity and Access Management (IAM) Solutions.md#personnel-offboarding>).

## Configuration Management

- **Configuration management (CM):** Maintains an accurate, approved record of system components, settings, versions, and dependencies throughout their lifecycle. It supports secure baselines, change impact analysis, incident response, troubleshooting, and vulnerability and patch management. See [NIST SP 800-128](https://csrc.nist.gov/pubs/sp/800/128/upd1/final).
- A **configuration item (CI)** is a component or service managed as part of that record, such as a server, application, network device, cloud resource, or software version. Record its owner, status, configuration, and relevant relationships.
- A **configuration management database (CMDB)** stores CI records and relationships. A **configuration management system (CMS)** includes the data, tools, and processes that maintain and use those records. See [CMS and CMDB definitions in Section 02](<Section 02: Fundamentals of Security.md#documentation-and-version-control>).
- Keep records current by linking discovery, deployment, change approval, and retirement processes. Consistent identifiers and labels help connect records; a universal key-value schema or a particular database engine is not required.
- A CMDB helps identify affected systems and dependencies, but accurate records do not guarantee that a penetration test will fail or that every vulnerability is known.

## Change Management

- **Change Management:** A formal process for requesting, reviewing, approving, implementing, and documenting changes.
- Change management reduces downtime, misconfiguration, and unauthorized changes.
- Changes can include software updates, firewall rule changes, system upgrades, cloud configuration changes, and access control changes.

## Change Records

A good change record includes:
- Change description
- Business reason
- Systems affected
- Risk and impact
- Approval
- Implementation steps
- Testing plan
- Backout plan
- Scheduled window
- Post-change validation

## Security Impact of Poor Change Management

Poor change management can cause:
- Outages
- Exposed services
- Broken logging
- Weak firewall rules
- Lost data
- Privilege mistakes
- Failed backups
- Security tool misconfiguration

## Key Takeaways

- Asset management gives visibility into what must be protected.
- Change management controls how systems are modified.
- Both processes support security, audit readiness, and incident response.