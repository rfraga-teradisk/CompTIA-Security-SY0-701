# Security Infrastructure

## Objectives
- Understand common security infrastructure components
- Explain how tools support prevention, detection, and response
- Know common network, endpoint, and monitoring controls

## Table of Contents

1. [Security Infrastructure](#security-infrastructure)
2. [Network Security Tools](#network-security-tools)
3. [Endpoint Security Tools](#endpoint-security-tools)
4. [Monitoring Tools](#monitoring-tools)
5. [Identity and Access Tools](#identity-and-access-tools)
6. [Data Protection Tools](#data-protection-tools)
7. [Key Takeaways](#key-takeaways)

## Security Infrastructure

- **Security Infrastructure:** The tools, systems, platforms, and configurations used to protect an organization.
- Infrastructure controls help prevent attacks, detect suspicious activity, and support incident response.

## Network Security Tools

- **Firewall:** Allows or blocks traffic based on rules.
- **IDS:** Intrusion Detection System; detects suspicious traffic and alerts.
- **IPS:** Intrusion Prevention System; detects and blocks suspicious traffic. A network IPS must be inline with traffic it is expected to stop. It may be integrated with a firewall or placed at a network boundary on either side of one; placement depends on what traffic needs inspection. See [NIST's IDPS placement guidance](https://csrc.nist.gov/pubs/sp/800/94/final).
- **VPN:** Creates encrypted remote access.
- **Proxy:** Intermediary system that filters or monitors web traffic.
- **WAF:** Web Application Firewall; protects web applications from common web attacks.
- **NAC:** Network Access Control; controls which devices can connect to the network.

### Network ACLs and Cloud Security Groups

- A packet-filtering **access control list (ACL)** is an ordered set of permit or deny entries evaluated against fields such as source and destination IP addresses, protocols, and ports. A first matching rule normally decides the result; an unmatched packet is commonly denied. Sequence numbers and defaults depend on the platform. A packet ACL is generally stateless, while a stateful firewall also tracks connections.
- IPv4 and IPv6 rules must be considered separately. An allow-all entry ahead of narrower rules makes those later rules ineffective for matching traffic. An ACL must also be attached to the relevant interface, VLAN, or subnet as the platform requires.
- Apply least privilege to management ports such as SSH and RDP. Permit them only from trusted administration sources where needed, rather than exposing them to every address.

| Cloud control | Scope and rule behavior |
| --- | --- |
| **AWS VPC network ACL (NACL)** | Applies to associated **subnets**; stateless; numbered inbound and outbound allow/deny rules are checked from the lowest number to the first match. Return traffic needs an explicit rule. The default VPC NACL has an allow-all rule 100, followed by a final deny; a new custom NACL starts with deny-only rules. See [AWS network ACL documentation](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-network-acls.html). |
| **AWS security group** | Applies to supported resources through their network interfaces; stateful; rules allow traffic, with unmatched traffic denied. Rules are not evaluated in numbered first-match order, and return traffic is automatically allowed. See [AWS security group documentation](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-security-groups.html). |
| **Azure network security group (NSG)** | Can be associated with a subnet, network interface, or both; stateful; **allow and deny** rules have numeric priorities and are processed until a match. Azure also provides default rules. An NSG is not simply an AWS security group applied to a whole virtual network. See [Azure NSG documentation](https://learn.microsoft.com/en-us/azure/virtual-network/network-security-groups-overview). |

## Endpoint Security Tools

- **Antivirus:** Detects and removes known malware.
- **EDR:** Endpoint Detection and Response; monitors endpoint behavior and supports investigation.
- **Host Firewall:** Controls traffic on one system.
- **Disk Encryption:** Protects data if a device is lost or stolen.
- **Application Control:** Allows only approved applications to run.

## Monitoring Tools

- **SIEM:** Collects, searches, and correlates logs for security monitoring.
- **SOAR:** Automates and orchestrates response workflows.
- **Syslog Server:** Collects logs from systems and network devices.
- **Packet Capture:** Records network traffic for analysis.

## Identity and Access Tools

- Directory services
- MFA systems
- Single sign-on
- Privileged access management
- Identity governance tools

## Data Protection Tools

- **DLP:** Data Loss Prevention; helps stop unauthorized movement of sensitive data.
- Encryption platforms
- Backup systems
- Key management systems
- Rights management tools

## Key Takeaways

- Infrastructure tools should work together.
- A firewall alone is not enough; security needs endpoint, identity, logging, and data protection controls.