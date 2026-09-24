# Malicious Activity

## Objectives
- 2.4 - Given a scenario, analyze indicators of malicious activity
- Identify common indicators of compromise
- Understand basic alert triage and log review

## Table of Contents

1. [Malicious Activity](#malicious-activity)
2. [Indicators of Compromise](#indicators-of-compromise)
3. [Common Log Sources](#common-log-sources)
4. [Suspicious Authentication Activity](#suspicious-authentication-activity)
5. [Endpoint Indicators](#endpoint-indicators)
6. [Network Indicators](#network-indicators)
7. [Interpreting Activity Indicators](#interpreting-activity-indicators)
8. [Triage Questions](#triage-questions)
9. [Key Takeaways](#key-takeaways)

## Malicious Activity

- **Malicious Activity:** Any action intended to steal data, gain unauthorized access, disrupt systems, damage files, or avoid detection.
- Malicious activity may appear in logs, alerts, endpoint behavior, network traffic, email, or cloud audit events.

## Indicators of Compromise

- **IOC:** Evidence that a system, account, network, or application may be compromised.

Examples:
- Malware hash
- Suspicious IP address
- Malicious domain
- Unknown process
- Unusual outbound traffic
- Repeated failed logons
- Successful login from unusual location
- New unauthorized admin account
- Disabled security tools
- Suspicious scheduled task

## Common Log Sources

- Windows Security logs
- Linux authentication logs
- Firewall logs
- DNS logs
- VPN logs
- Proxy logs
- EDR alerts
- Email security logs
- Cloud audit logs
- Web server logs

## Suspicious Authentication Activity

Examples:
- Many failed logins followed by one success
- Login outside normal working hours
- Login from unusual country
- MFA push fatigue attempts
- Disabled account login attempt
- New admin account created unexpectedly

## Endpoint Indicators

Examples:
- Unknown process running
- Security tool disabled
- Suspicious PowerShell command
- Unexpected file encryption
- New persistence mechanism
- Unusual parent-child process relationship

## Network Indicators

Examples:
- Connection to known malicious IP
- Unusual DNS queries
- Large outbound data transfer
- Beaconing pattern
- Traffic to rare external destination

## Interpreting Activity Indicators

| Indicator | Possible Concern | Context to Check |
| --- | --- | --- |
| **Account Lockout** | Password guessing or credential abuse | Mistyped passwords, stale service credentials, and failure patterns across accounts. |
| **Concurrent Sessions** | Stolen credentials or session tokens | Legitimate use of multiple devices or applications. |
| **Impossible Travel** | Geographically distant sign-ins too close together for realistic travel | VPNs, proxies, mobile networks, and inaccurate IP geolocation. |
| **Blocked Content** | Attempted malware delivery or contact with malicious infrastructure | Whether the control blocked the attempt before execution; a block alone does not prove infection. |
| **Resource Consumption** | Cryptojacking, denial of service, or unauthorized cloud workloads | Backups, updates, demand spikes, and approved deployments. |
| **Out-of-Cycle Activity** | Activity outside expected hours or schedules | Time zones, maintenance, automation, and changed work patterns. |
| **Missing or Altered Logs** | Disabled logging, deletion, or timestamp manipulation to hide activity | Retention settings, storage failures, collection outages, and clock synchronization. |

IoCs can include files, registry entries, memory artifacts, and network or identity events. Correlate multiple sources and preserve relevant evidence. Being logged in on-site and through a VPN is not automatically impossible travel. See [Microsoft's anomaly-investigation guidance](https://learn.microsoft.com/en-us/defender-cloud-apps/investigate-anomaly-alerts).

## Triage Questions

- What triggered the alert?
- Which user, host, IP, or process is involved?
- Is the activity expected?
- What happened before and after the event?
- Is there evidence of lateral movement?
- Is containment needed?

## Key Takeaways

- Malicious activity analysis requires evidence and context.
- Logs help build timeline, scope, and impact.
