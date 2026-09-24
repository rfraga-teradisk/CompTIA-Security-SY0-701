# Hardening

## Objectives
- 4.1 - Given a scenario, apply common security techniques to computing resources
- Understand how hardening reduces attack surface
- Identify hardening methods for systems, networks, cloud, and applications

## Table of Contents

1. [Hardening](#hardening)
2. [System Hardening](#system-hardening)
3. [Network Hardening](#network-hardening)
4. [Cloud Hardening](#cloud-hardening)
5. [Application Hardening](#application-hardening)
6. [Baseline Configuration](#baseline-configuration)
7. [Key Takeaways](#key-takeaways)

## Hardening

- **Hardening:** The process of securely configuring systems and removing unnecessary exposure.
- Hardening reduces the number of ways an attacker can compromise a system.

Common hardening steps:
- Remove unused software
- Disable unused services
- Apply patches
- Change default passwords
- Disable default accounts if possible
- Enable logging
- Enforce MFA
- Restrict administrator access
- Use encryption

Hardening starts from an approved baseline and keeps only required functionality. Test changes so a security setting does not break a needed service; monitor for drift afterward.

## System Hardening

Examples:
- Patch operating systems
- Enable endpoint protection
- Configure host firewall
- Enforce account lockout
- Disable unnecessary ports
- Restrict local admin rights
- Enable audit logs
- Use a TPM where supported to protect keys and support measured boot; pair it with endpoint detection and response (EDR), which monitors and responds to endpoint activity. XDR correlates endpoint signals with other sources; neither a TPM nor an EDR product hardens a device by itself. See [Microsoft's TPM guidance](https://learn.microsoft.com/en-us/windows/security/hardware-security/tpm/how-windows-uses-the-tpm).
- Encrypt data at rest and in transit. Protecting **data in use** requires additional controls such as an attested trusted execution environment; ordinary disk or transport encryption does not protect data while it is processed. See [Microsoft's confidential computing overview](https://learn.microsoft.com/en-us/azure/confidential-computing/overview).

## Network Hardening

Examples:
- Review firewall rules
- Disable unused switch ports
- Use secure management protocols
- Segment networks
- Update firmware
- Secure wireless settings
- Disable insecure protocols
- Allow only required TCP/UDP services and management paths. Use SSHv2 rather than Telnet or SSHv1; do not retain SSHv1 as an acceptable fallback.
- Filter ICMP by type and purpose rather than blocking it wholesale. Some ICMP errors, including ICMPv6 Packet Too Big, are needed for network operation and path MTU discovery. See [RFC 4890](https://www.rfc-editor.org/rfc/rfc4890.html).
- Configure endpoint-facing switch ports as access ports and disable unneeded dynamic trunk negotiation; explicitly configure links that must carry VLAN trunks. See [Cisco's switch-port guidance](https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst3750/software/release/12-2_50_se/command/reference/cr/cli3.pdf).

## Cloud Hardening

Examples:
- Use least-privilege IAM
- Keep storage private by default
- Restrict security groups
- Enable cloud audit logs
- Encrypt data
- Rotate access keys
- Monitor configuration changes

## Application Hardening

Examples:
- Validate input
- Protect secrets
- Use secure headers
- Patch dependencies
- Enforce authentication and authorization
- Log security events
- Avoid detailed error messages

### Credentials and Software

- Replace vendor default passwords and disable or rename default accounts where supported. A Windows workgroup name is not an authentication secret; changing it is not a substitute for credential controls.
- Use long, unique passwords or supported passwordless methods such as passkeys, FIDO2 security keys, or Windows Hello for Business. See [Microsoft Entra passwordless options](https://learn.microsoft.com/en-us/entra/architecture/auth-passwordless).
- Inventory installed software and remove or restrict applications that are unneeded or unauthorized. Assess business need before removing a hypervisor, cloud client, or agent; ephemeral ports alone do not establish that software is malicious.

## Baseline Configuration

- **Baseline:** Minimum approved configuration for a system.
- Baselines help keep systems consistent and secure.

Examples:
- Windows server baseline
- Linux server baseline
- Firewall baseline
- Cloud IAM baseline
- Browser security baseline

## Key Takeaways

- Hardening is preventive security.
- Secure baselines help make systems consistent, auditable, and easier to maintain.