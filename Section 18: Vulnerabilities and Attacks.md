# Vulnerabilities and Attacks

## Objectives
- 2.3 - Explain various types of vulnerabilities
- 2.4 - Given a scenario, analyze indicators of malicious activity
- Understand common attacks and mitigation methods

## Table of Contents

1. [Vulnerabilities](#vulnerabilities)
2. [Attack Surface](#attack-surface)
3. [Common Vulnerabilities](#common-vulnerabilities)
4. [Common Attacks](#common-attacks)
5. [Denial-of-Service Attacks](#denial-of-service-attacks)
6. [DNS and Wireless Attacks](#dns-and-wireless-attacks)
7. [Replay and Privilege Escalation](#replay-and-privilege-escalation)
8. [Web Application Attacks](#web-application-attacks)
9. [Password Attacks](#password-attacks)
10. [Mitigations](#mitigations)
11. [Key Takeaways](#key-takeaways)

## Vulnerabilities

- **Vulnerability:** A weakness in software, hardware, configuration, process, or design.
- Vulnerabilities may allow unauthorized access, data theft, service disruption, privilege escalation, or malware execution.

## Attack Surface

- **Attack Surface:** All possible points where an attacker can try to enter, interact with, or affect a system.

Examples:
- Public website
- VPN login page
- Email inbox
- User accounts
- APIs
- Cloud storage
- Wireless network
- Remote desktop service
- Third-party integration

## Common Vulnerabilities

- Missing patches
- Weak passwords
- Default credentials
- Misconfigured firewall
- Public cloud storage
- Excessive permissions
- Unencrypted sensitive data
- Insecure APIs
- Poor input validation
- Unsupported software
- Open ports and services

## Common Attacks

- **Phishing:** Tricks users into revealing information or running malicious content.
- **Malware:** Software designed to harm systems or steal data.
- **Ransomware:** Malware that encrypts files and demands payment.
- **DoS/DDoS:** Attack that disrupts service availability.
- **Privilege Escalation:** Gaining higher permissions than originally assigned.
- **Man-in-the-Middle:** Intercepting or altering communication between two parties.

## Denial-of-Service Attacks

- **Denial of Service (DoS):** An attack that prevents or degrades legitimate access to a system, application, or network. It primarily targets **availability**.
- **Distributed Denial of Service (DDoS):** A DoS attack using multiple distributed sources, making filtering and containment more difficult.
- Attacks can exhaust bandwidth, connection capacity, CPU, memory, or application resources, or exploit a flaw that crashes a service. Not every DoS requires a large traffic flood.
- Targets include websites, DNS services, authentication systems, email, and internal services. Motives include disruption, hacktivism, competition, and extortion.
- Botnets can generate attack traffic, but DDoS does not require malware on the target or a botnet. Legitimate servers can also be abused as reflectors. Ransomware and DDoS are separate attacks, although criminals may combine them in an extortion campaign.

### Common Methods

| Method | How It Disrupts Availability |
| --- | --- |
| **Volumetric Flood** | Large volumes of traffic, such as UDP or ICMP packets, saturate network capacity. |
| **Protocol / State Exhaustion** | Consumes connection or protocol-handling resources; a TCP SYN flood can exhaust capacity for pending connections. |
| **Application-Layer Attack** | Overloads application functions, such as an HTTP endpoint or an expensive database-backed operation. Requests may resemble legitimate traffic. |
| **DNS Query Flood** | Overwhelms DNS infrastructure with queries. Repeated queries for nonexistent names can increase lookup work and exhaust resources; NXDOMAIN is the response indicating a nonexistent domain, not proof of an attack by itself. |
| **Wireless Jamming** | Radio interference prevents legitimate wireless communication. |

### Reflection and Amplification

- **Reflection:** An attacker spoofs the victim's source IP address in requests to third-party servers, causing replies to be sent to the victim.
- **Amplification:** A small request produces a larger response, increasing the traffic delivered to the victim. Reflection and amplification are related but distinct concepts.
- **DNS Example:** An attacker abuses accessible DNS resolvers to send larger responses to a spoofed victim address. The resolvers need not be infected or controlled by the attacker.
- DNS uses both UDP and TCP; UDP-based DNS reflection is one particular attack mechanism. See [CISA's UDP amplification guidance](https://www.cisa.gov/ncas/alerts/ta14-017a).

### Indicators and Mitigation

- Indicators include sudden traffic or request spikes, many incomplete connections, exhausted resources, increased latency, timeouts, and service failures.
- Compare traffic with normal patterns and correlate network and application telemetry. A legitimate surge in users or a configuration fault can produce similar symptoms.
- Use rate limiting, connection limits, and application-layer filtering where appropriate, and patch flaws that can trigger service crashes.
- Coordinate with an ISP or DDoS protection provider for upstream filtering or traffic scrubbing. A local firewall cannot restore availability if the upstream connection is already saturated.
- Use distributed capacity, caching, and resilient DNS to reduce impact; redundancy and scaling alone do not guarantee protection.
- Restrict recursive DNS service to authorized clients and apply source-address validation to reduce abuse as a reflector or source of spoofed traffic.
- Prepare and test a response plan with monitoring thresholds and provider contacts. See the [CISA, FBI, and MS-ISAC DDoS guide](https://www.cisa.gov/sites/default/files/publications/understanding-and-responding-to-ddos-attacks_508c.pdf).

## DNS and Wireless Attacks

### DNS Attacks

| Attack | Meaning |
| --- | --- |
| **DNS Spoofing / Cache Poisoning** | Supplies false DNS information; cache poisoning stores false records in a resolver's cache. It need not affect every query. |
| **DNS Hijacking** | Changes DNS records, account settings, or resolver configuration without authorization to redirect resolution. |
| **Pharming** | Redirects users to a fraudulent site, often through DNS manipulation or changes to a local hosts file. |
| **DNS Tunneling** | Encodes data in DNS queries and responses to carry command-and-control traffic or exfiltrate information. |

DNS tunneling abuses a permitted protocol; receiving a DNS response alone does not automatically infect a host. Monitor unusual query patterns and restrict clients to approved resolvers. Protect DNS administration with MFA, access controls, and change monitoring. DNSSEC validation helps detect forged signed DNS data but does not encrypt queries or prevent all DNS attacks. See [MITRE's DNS technique](https://attack.mitre.org/techniques/T1071/004/).

### Wireless and Local Network Attacks

- **Rogue Access Point:** An unauthorized AP, whether maliciously deployed or installed by an employee without approval.
- **Evil Twin:** An AP impersonating a trusted wireless network, often using the same SSID to attract users. It does not need the same hardware model or operating system.
- **Deauthentication / Disassociation Attack:** Abuses management frames to disconnect clients. Protected Management Frames (PMF) protect certain management frames where negotiated; they do not stop radio jamming. See [Cisco's PMF guidance](https://www.cisco.com/c/en/us/td/docs/wireless/controller/9800/17-5/config-guide/b_wl_17_5_cg/m_mfp.html).
- **DHCP Starvation:** Exhausts available address leases, preventing legitimate clients from receiving configuration. An attacker may also introduce a rogue DHCP server to supply malicious gateway or DNS settings; that is a separate step, not a requirement for every wireless attack.
- Use managed wireless profiles, validate authentication-server certificates for enterprise Wi-Fi, detect unauthorized APs, and apply DHCP snooping and access-port controls where supported.

## Replay and Privilege Escalation

- **On-Path Attack:** An attacker intercepts or alters communication between parties. Also called man-in-the-middle (MITM); authenticated encryption and correct certificate validation help defend against it.
- **Replay Attack:** Captures a valid message or authentication exchange and resends it to obtain an unauthorized result. The attacker may not need to decrypt it or remain on the communication path during replay.
- Use authenticated freshness checks, such as nonces, sequence numbers, or timestamps with replay tracking. Encryption or a firewall alone does not guarantee replay resistance.
- **Vertical Privilege Escalation:** Gains greater privileges, such as moving from a standard user account to administrator.
- **Horizontal Privilege Escalation:** Gains unauthorized access to another user's resources at a similar privilege level.
- **Lateral Movement:** Moves between systems or accounts within an environment. It may use existing privileges and is distinct from gaining higher privileges.
- Prevent escalation with server-side authorization checks, least privilege, patching, and secure service and account configurations.

## Web Application Attacks

- **SQL Injection:** Injecting SQL commands into an application to access or modify database data.
- **XSS:** Cross-site scripting; running malicious scripts in a victim browser.
- **CSRF:** Cross-site request forgery; tricking a user browser into performing an unwanted action.
- **Directory Traversal:** Accessing files outside the intended directory.

### Application Attack Details

- **Buffer Overflow:** Writes beyond a buffer's bounds, potentially corrupting memory, crashing an application, or changing execution flow. Bounds checking and memory-safe implementation approaches address the cause; exploit mitigations provide additional protection.
- **Injection:** Untrusted data is interpreted as instructions, such as SQL, operating system commands, or LDAP expressions. Use safe APIs and parameterization where available rather than constructing instructions from raw input.
- **Path Traversal:** Manipulates a file path, often using parent-directory sequences, to access files outside the permitted location. It can affect applications beyond web servers; command execution is not an automatic consequence.
- Prefer mapping approved file identifiers to server-controlled paths, enforce canonical-path boundaries, and restrict filesystem permissions. See [OWASP's path-traversal guidance](https://owasp.org/www-community/attacks/Path_Traversal).
- SQLi, XSS, and CSRF are explained further in [Section 03](<Section 03: Threat Actors.md#operating-system-and-web-vulnerabilities>).

## Password Attacks

- **Brute Force:** Trying many password combinations.
- **Password Spraying:** Trying one or a few common passwords across many accounts.
- **Credential Stuffing:** Using leaked usernames and passwords from another breach.
- **Dictionary Attack:** Trying passwords from a wordlist.

### Password Attack Distinctions

- **Hybrid Attack:** Combines a wordlist with predictable changes, such as added digits or character substitutions.
- **Online Guessing:** Submits attempts to a live authentication service; rate limits, monitoring, and MFA can limit success.
- **Offline Cracking:** Tests candidates against stolen password hashes without contacting the login service. Account lockout does not constrain this activity.
- Password spraying targets live logins with one or a few common passwords across many accounts, often pacing attempts to avoid per-account lockout thresholds; it is not usually an offline hash-cracking attack. Credential stuffing instead reuses known username/password pairs from breaches. See [OWASP's comparison of automated login attacks](https://cheatsheetseries.owasp.org/cheatsheets/Credential_Stuffing_Prevention_Cheat_Sheet.html).
- **Rainbow Table:** A precomputed structure used to recover password candidates from hashes; unique salts make reusable tables impractical. See [password-hash protection in Section 08](<Section 08: Cryptographic Solutions.md#password-hash-protection>).
- Long, unique passwords, compromised-password screening, MFA, and rate limiting provide complementary defenses. Routine password rotation alone does not stop guessing; [NIST guidance](https://pages.nist.gov/800-63-4/sp800-63b.html) calls for changes when compromise is evidenced rather than arbitrary periodic changes.

### Tools Mentioned in the Lesson

| Tool | Main Use |
| --- | --- |
| [Hashcat](https://hashcat.net/hashcat/) and [John the Ripper](https://www.openwall.com/john/) | Test password candidates against hashes or encrypted files offline. John's jumbo version also supports archives, documents, and some web-application hash formats. |
| [THC Hydra](https://github.com/vanhauser-thc/thc-hydra) and [Medusa](https://github.com/jmk-foofus/medusa) | Test logins against live network services; these are online attempts subject to monitoring and rate limits. |
| [Wfuzz](https://github.com/xmendez/wfuzz) | Fuzz web requests, including form and authentication inputs; its uses extend beyond password guessing. |
| [RainbowCrack](https://project-rainbowcrack.com/) and [Ophcrack](https://ophcrack.sourceforge.io/) | Use precomputed rainbow tables against suitable hashes; unique salts defeat reuse of general-purpose tables. |
| [Aircrack-ng](https://www.aircrack-ng.org/documentation) | Audit Wi-Fi security, including WEP and WPA/WPA2 pre-shared-key password testing. |

Brutus and L0phtCrack are also named in the lesson's historical tool list. Treat the ranking, platform claims, and hash-format counts as a snapshot rather than exam facts. NTLM and Kerberos are different Windows authentication protocols; [Kerberos is preferred in Active Directory, but NTLM remains supported](https://learn.microsoft.com/en-us/windows-server/security/kerberos/ntlm-overview).

## Mitigations

- Patch systems
- Enforce MFA
- Use least privilege
- Validate input
- Segment networks
- Encrypt sensitive data
- Monitor logs
- Disable unused services
- Apply secure configuration baselines
- Train users to recognize phishing

## Key Takeaways

- Vulnerabilities create opportunities for attacks.
- DoS targets availability; DDoS uses distributed sources. Distinguish resource exhaustion, reflection, and amplification when selecting defenses.
- Reducing attack surface and applying layered controls lowers risk.
