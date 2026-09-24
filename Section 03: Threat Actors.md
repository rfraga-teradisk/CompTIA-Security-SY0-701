# Threat Actors

## Objectives

- 2.1 - Compare and contrast common threat actors and motivations
- 2.2 - Explain common threat vectors and attack surfaces
- Understand attacker types, motivations, resources, and behavior
- Describe the supply chain, application, operating system, web, hardware, virtualization, cloud, and mobile vulnerabilities introduced in the supplied course

## Table of Contents

1. [Threat Actor](#threat-actor)
2. [Threat Actor Types](#threat-actor-types)
3. [Threat Actor Attributes](#threat-actor-attributes)
4. [Threat Actor Motivations](#threat-actor-motivations)
5. [Internal and External Threats](#internal-and-external-threats)
6. [Threat Vectors](#threat-vectors)
7. [Human Vectors and Social Engineering](#human-vectors-and-social-engineering)
8. [Attack Surface](#attack-surface)
9. [Supply Chain Vulnerabilities](#supply-chain-vulnerabilities)
10. [Application Vulnerabilities](#application-vulnerabilities)
11. [Operating System and Web Vulnerabilities](#operating-system-and-web-vulnerabilities)
12. [Hardware and Virtualization Vulnerabilities](#hardware-and-virtualization-vulnerabilities)
13. [Cloud Vulnerabilities](#cloud-vulnerabilities)
14. [Mobile Device Vulnerabilities](#mobile-device-vulnerabilities)
15. [Deception and Disruption Technologies](#deception-and-disruption-technologies)
16. [Key Takeaways](#key-takeaways)

## Threat Actor

- **Threat Actor:** A person, group, or organization whose actions can harm systems, data, or operations.
- Actors may act deliberately or contribute to an incident through mistakes or negligence.
- Automated tools, bots, and malware can carry out an actor's actions at scale.
- Understanding the actor helps identify likely targets, methods, and impact.
- Not every threat requires a malicious actor: equipment failures and natural events can also cause harm.

### Structured and Unstructured Attacks

- **Structured Attack:** Planned, organized, and often persistent, with multiple stages such as reconnaissance, initial access, and data theft.
- **Unstructured Attack:** Usually opportunistic and less organized, often using readily available tools or known weaknesses.
- Either can originate internally or externally. An unstructured attack can still be intentional and malicious.
- Accidental incidents, such as opening a malicious attachment or exposing a file, should be distinguished from the attacker's intent.

## Threat Actor Types

| Actor | Typical Characteristics | Common Motivation or Example |
| --- | --- | --- |
| **Unskilled Attacker** | Limited technical knowledge; relies on existing scripts, exploit kits, or purchased services. Also called a script kiddie. | Curiosity, notoriety, disruption, or financial gain. |
| **Hacktivist** | Uses attacks to advance a political, social, or ideological cause; capabilities vary. | Website defacement, data leaks, or denial of service to draw attention to a cause. |
| **Organized Crime Syndicates** | Coordinated groups with funding, specialized roles, and a focus on risk versus reward. | Ransomware, extortion, fraud, or selling stolen data. |
| **Nation-State Actor** | Government-sponsored or government-aligned actor; may have substantial resources and long-term objectives. | Espionage, strategic disruption, intellectual property theft, or military objectives. |
| **Insider Threat** | Current or former employee, contractor, or trusted partner with access or organizational knowledge. | Theft, revenge, coercion, negligence, or misuse of a compromised account. |
| **Competitor** | Seeks a business advantage through unauthorized access to valuable information. | Theft of trade secrets, product plans, or customer information. |

- **Advanced Persistent Threat (APT):** A capable adversary that maintains a sustained effort to gain and retain access to a target.
- APT activity is commonly associated with nation-state operations; other well-resourced actors can also conduct persistent campaigns.
- **Malware as a Service:** Ready-made malicious tools or services lower the technical barrier to launching attacks.
- Low attacker skill does not necessarily mean low impact when powerful tools are readily available.

## Threat Actor Attributes

Evaluate actors using several attributes together:

- **Internal or External:** Whether the actor operates from within a trusted relationship or outside the organization.
- **Resources and Funding:** Money, infrastructure, personnel, time, and access to tools or exploits.
- **Sophistication and Capability:** Technical skill, planning, ability to evade detection, and ability to develop or adapt attacks.
- **Access and Knowledge:** Existing privileges, credentials, knowledge of internal processes, and access to sensitive systems.

Example:

- An unskilled external attacker may scan public services using a downloaded tool.
- A nation-state actor may invest months in a targeted intrusion.
- A privileged insider may need little technical sophistication to copy sensitive data already available to their account.

## Threat Actor Motivations

| Motivation | Meaning or Example |
| --- | --- |
| **Financial Gain** | Obtain money through fraud, ransomware, or the sale of stolen information. |
| **Data Exfiltration** | Remove data without authorization, often to support resale, espionage, or extortion. |
| **Espionage** | Secretly collect government, military, or business intelligence. |
| **Service Disruption** | Interrupt availability, such as taking a customer portal offline. |
| **Blackmail and Extortion** | Threaten disclosure or continued disruption to force payment or another action. |
| **Political Beliefs** | Promote an ideology or protest an organization's actions. |
| **Ethical Beliefs** | Act based on a perceived moral cause; this belief does not itself authorize access. |
| **Revenge** | Retaliate against an employer, coworker, or organization. |
| **Disruption or Chaos** | Cause confusion, damage, or loss of confidence. |
| **War** | Support conflict through intelligence gathering, sabotage, or disruption. |
| **Notoriety** | Seek recognition, attention, or status. |

- A single campaign can have several motivations.
- Authorized ethical security testing requires permission and an agreed scope.

## Internal and External Threats

- **Internal Threat:** Arises from someone with trusted access or an internal role.
  - Example: An employee copies confidential files to personal storage.
- **External Threat:** Originates outside the organization.
  - Example: An attacker attempts to compromise a public VPN login page.

Insider threats can be:

- **Malicious:** Deliberately steals, damages, or abuses access.
- **Negligent:** Ignores policies or handles information carelessly.
- **Accidental:** Makes an unintended mistake, such as sending data to the wrong recipient.
- **Compromised:** Has an account or device taken over by an attacker, or is coerced into assisting one.

Privileged insiders can cause significant harm because they may access sensitive data, change controls, or create additional access paths.

Useful safeguards:

- Least privilege and separation of duties
- Privileged access management and access reviews
- Monitoring and logging of sensitive actions
- Prompt revocation of access during offboarding
- Security awareness and clear reporting procedures

## Threat Vectors

- **Threat Vector:** The path or method used to reach a target or deliver an attack.
- **Vulnerability:** A weakness that an attack may exploit.
- **Attack Surface:** The collection of exposed points where an attacker could attempt access or cause harm.

Common vectors:

- Email, attachments, and malicious links
- SMS, messaging applications, and voice calls
- Websites, web applications, and APIs
- Removable media, such as USB drives and memory cards
- Wireless networks and remote access portals
- Cloud services and third-party connections
- Compromised software packages or updates

Example:

- A phishing email is the delivery vector.
- A public login portal forms part of the attack surface.
- Weak authentication can help an attacker use a stolen password to gain access.

## Human Vectors and Social Engineering

- **Social Engineering:** Manipulating people into disclosing information or performing actions that weaken security.
- Attacks often exploit trust, urgency, authority, fear, or curiosity.

| Technique | Description |
| --- | --- |
| **Phishing** | A deceptive message attempts to obtain information or induce an action, such as opening an attachment. |
| **Spear Phishing** | A targeted phishing attempt tailored to a particular person or group. |
| **Whaling** | Spear phishing aimed at senior executives or other high-value individuals. |
| **Smishing** | Phishing delivered through SMS or text messages. |
| **Vishing** | Social engineering using voice calls or voice services. |
| **Business Email Compromise (BEC)** | Uses spoofed or compromised business identities to request fraudulent payments or sensitive information. |
| **Pretexting** | Uses a fabricated story or situation to gain trust and elicit an action. |
| **Impersonation** | Pretends to be a trusted person, such as an executive, technician, or vendor. |
| **Brand Impersonation** | Copies a recognizable organization's branding to make a message or site seem legitimate. |
| **Typosquatting** | Uses a domain resembling a legitimate one, often with a small spelling difference. |
| **Hoax** | Uses a false claim or warning to mislead a victim. |
| **Disinformation** | Intentionally spreads false information to influence beliefs or behavior. |
| **Watering Hole** | Compromises a website that the intended targets are likely to visit. |
| **Shoulder Surfing** | Observes a screen, keyboard, or document to obtain information. |
| **Dumpster Diving** | Retrieves sensitive information from discarded materials. |

### Phishing Indicators

- Unexpected requests for credentials, money, or sensitive data
- Urgent demands or pressure to bypass normal procedures
- Suspicious sender domains or links whose destinations differ from their displayed text
- Unexpected attachments, vague greetings, or unusual wording
- Copied logos or sender names that appear legitimate but do not prove authenticity

Good grammar and familiar branding do not guarantee that a message is safe.

### Reducing Social Engineering Risk

- Train users to recognize and report suspicious requests.
- Verify payment or account-change requests through a known, independent contact method.
- Establish and enforce acceptable use policies.
- Use email filtering, endpoint protection, MFA, and data loss prevention where appropriate.
- Encourage prompt reporting so security teams can investigate and contain incidents.

## Attack Surface

Common exposed areas and weaknesses include:

- **Removable Devices:** Can introduce malicious files or allow unauthorized data copying.
- **Vulnerable Software:** Unpatched applications or untrusted downloads can expose systems.
- **Client-based and Agentless Services:** Installed agents and services accessed without a local agent both require secure configuration, updates, and access controls.
- **Unsupported Systems and Applications:** May no longer receive security fixes.
- **Default Credentials:** Unchanged vendor passwords can provide easy access.
- **Insecure Networks:** Weak wireless protection, poor segmentation, or exposed management interfaces increase access opportunities.
- **Open Service Ports:** Expose reachable services; unnecessary services expand the attack surface.
- **Overprivileged Accounts:** Increase the damage possible after an account is compromised.
- **Messaging and Social Media:** Provide opportunities for malicious links, impersonation, and influence campaigns.
- **Shadow IT:** Hardware, software, or cloud services used without organizational approval or oversight.

A virtual machine or a USB-based application is not automatically shadow IT; the issue is whether it is managed and authorized.

## Supply Chain Vulnerabilities

- **Supply Chain Attack:** Compromises a supplier, product, service, or delivery process to reach another organization.
- Trusted vendor access and widely distributed software can give one compromise a broad impact.

Potential entry points:

- Managed service providers (MSPs)
- Vendors, suppliers, and original equipment manufacturers (OEMs)
- Internet and cloud service providers
- Software as a Service (SaaS) providers
- Hardware, firmware, software packages, and update channels

Example:

- An attacker compromises a software provider's update process, and customers install the resulting malicious update.

Risk reduction includes vendor assessment, limited third-party privileges, segmentation, monitoring, and verification of software provenance and integrity. Zero Trust reduces reliance on a vendor relationship alone as proof that access is safe.

## Application Vulnerabilities

### Memory Injection

- **Memory Injection:** Places malicious code into a process's memory so it can execute within that process.
- **Process:** An executing instance of a program.
- **Thread:** A sequence of execution within a process.
- **Dynamic Link Library (DLL):** A library of functions that programs can load and use.
- **Shellcode:** A small code payload used in an exploit.
- **Process Hollowing:** Starts a legitimate process in a suspended state, replaces or alters its in-memory content, and resumes execution with malicious code.
- **Reflective DLL Injection:** Loads a DLL into memory using its own loader logic, avoiding the normal loading path.

Legitimate system functions can be abused for injection. Trusted distribution and code-signature checks help reduce risk, but a valid signature alone does not guarantee that code is harmless.

### Other Application Weaknesses

| Concept | Description |
| --- | --- |
| **Buffer Overflow** | Data exceeds a buffer's capacity and overwrites adjacent memory, potentially causing a crash or code execution. |
| **Race Condition** | An outcome depends on the timing or order of concurrent operations, which may allow unsafe behavior. |
| **Time-of-Check/Time-of-Use (TOC/TOU)** | A resource changes between a security check and its use, invalidating the earlier check. |
| **Malicious Update** | A software update introduces malicious code, potentially through a compromised supplier or update channel. |
| **Zero-Day Vulnerability** | A previously unknown vulnerability for which defenders have had no opportunity to prepare a fix; exploitation may occur before a patch is available. |

A **logic bomb** executes when a specified condition is met. It is distinct from a zero-day vulnerability.

## Operating System and Web Vulnerabilities

### Operating System and Configuration Issues

- Missing patches and outdated or unsupported software
- Default, weak, or shared credentials
- Excessive permissions and unnecessary services
- Debugging features or diagnostic information exposed in production
- Insecure database, network device, or API configuration

Disable debugging features in production or secure them appropriately to prevent exposure of sensitive information or privileged functionality.

Patch management should include testing, deployment planning, rollback options, and fallback plans to maintain service if an update fails.

### SQL Injection (SQLi)

- Untrusted input changes the meaning of a database query.
- Depending on permissions and the environment, an attacker may read, alter, or delete data or perform administrative actions.
- Examples include reading data with `SELECT` and modifying it with `INSERT`, `UPDATE`, or `DELETE`. Database capabilities and excessive privileges may also allow database shutdown, file access, or operating system command execution.
- Parameterized queries and limited database privileges reduce exposure.

### Cross-Site Scripting (XSS)

- Unsafe handling of untrusted content allows attacker-controlled scripts to execute in a user's browser in the context of a trusted site.
- Possible effects include stealing browser-readable cookies, session tokens, or other sensitive information, or performing actions as the user.

Variants:

- **Reflected XSS:** Malicious input is included in an immediate response, often through a crafted link.
- **Stored XSS (Persistent):** Malicious content is saved, such as in a database or file, and served to users later. Blog comments and review or feedback forms are common examples.
- **DOM-based XSS:** Unsafe client-side code processes attacker-controlled data into an executable browser context. DOM means Document Object Model; this flaw can affect ordinary websites and is not limited to local files, gadgets, or widgets.

Context-appropriate output encoding, safe DOM handling, and sanitization where HTML is permitted help prevent XSS.

### Cross-Site Request Forgery (CSRF/XSRF)

- Tricks a user's browser into sending an unwanted request to a site where the user is authenticated.
- Exploits credentials the browser includes automatically, such as session cookies, when the application does not adequately verify that the user intended the action. A malicious page can trigger a request without the user clicking a link.
- Can cause state changes, such as transferring funds or changing an email address or password, if the application accepts the forged request. The impact depends on the victim's privileges; an administrator's session can expose administrative functions.
- Anti-CSRF tokens, appropriate cookie settings, and verification for sensitive actions help mitigate the risk.

Quick comparison:

- **SQLi:** Manipulates database queries.
- **XSS:** Executes malicious script in a browser.
- **CSRF:** Abuses an authenticated browser session to submit an unwanted request.

## Hardware and Virtualization Vulnerabilities

### Hardware and Firmware

- **Firmware:** Software embedded in a device that provides low-level control.
- Firmware vulnerabilities may permit authentication bypass, memory corruption, or unauthorized code execution.
- Unsupported hardware and legacy systems may lack available fixes or compatible replacement components.
- Untrusted drivers, compromised suppliers, and poorly managed IoT devices create additional exposure.

### Hypervisors

- **Hypervisor:** Software that creates and manages virtual machines and allocates hardware resources.
- **Type I (Bare Metal):** Runs directly on the hardware.
- **Type II (Hosted):** Runs on a host operating system.

Common virtualization risks:

- **VM Sprawl:** Uncontrolled growth of virtual machines or images, resulting in unmanaged, unpatched, or forgotten assets.
- **VM Escape:** A guest breaks out of its isolation and affects the host or hypervisor.
- **VM Hopping:** An attacker moves from one virtual machine to another, for example through weak isolation or network controls.
- **Hyperjacking:** Compromise or malicious use of the hypervisor layer to control or observe guest activity.
- **Resource Reuse:** Sensitive data remains in storage or other resources that are later assigned to another workload.

Maintain inventories, patch hosts and guests, restrict management access, isolate workloads, and sanitize resources before reuse.

## Cloud Vulnerabilities

The supplied course uses the CSA **Treacherous 12** as a framework for discussing cloud threats. The following summarizes that named list rather than presenting it as a current ranking:

1. **Data Breaches:** Unauthorized disclosure of sensitive cloud data.
2. **Weak Identity, Credential, and Access Management:** Poor control of accounts, secrets, or permissions.
3. **Insecure Interfaces and APIs:** Exposed or weakly protected service interfaces.
4. **System Vulnerabilities:** Exploitable weaknesses in cloud systems and applications.
5. **Account Hijacking:** Attackers take control of legitimate accounts.
6. **Malicious Insiders:** Trusted people deliberately misuse access.
7. **Advanced Persistent Threats:** Sustained intrusions aimed at long-term access.
8. **Data Loss:** Data is deleted, corrupted, or otherwise becomes unrecoverable.
9. **Insufficient Due Diligence:** Inadequate understanding of a provider, service, or security responsibilities.
10. **Abuse of Cloud Services:** Cloud resources are used to support malicious activity.
11. **Denial of Service:** Attacks exhaust resources or interrupt availability.
12. **Shared Technology Vulnerabilities:** Weak isolation or shared infrastructure flaws expose multiple customers or workloads.

Security measures include strong identity controls, protected APIs, monitoring, patching, data protection, and tested backups. Provider and customer responsibilities depend on the service model and agreement.

## Mobile Device Vulnerabilities

- **Sideloading:** Installing an application outside the platform's normal official store distribution path. Risk depends on the source, validation, and device policy.
- **Jailbreaking:** Bypassing platform restrictions, commonly associated with iOS devices.
- **Rooting:** Obtaining elevated administrative access, commonly associated with Android devices.
- Jailbreaking and rooting can weaken platform protections and violate organizational device requirements.
- Additional risks include outdated operating systems, untrusted applications, excessive application permissions, and lost devices.

Management controls:

- **Enterprise Mobility Management (EMM):** Broader management of mobile devices, applications, and enterprise data.
- **Mobile Device Management (MDM):** Applies device policies, compliance checks, configuration, and supported remote lock or wipe capabilities.
- **Mobile Application Management (MAM):** Controls business applications and their data.
- Use strong authentication, updates, application controls, and restrictions on noncompliant devices.

## Deception and Disruption Technologies

- **Honeypot:** Decoy system used to attract attackers and observe behavior.
- **Honeynet:** Network of honeypots.
- **Honeyfile:** Decoy file used to detect unauthorized access.
- **Honeytoken:** Fake data or credential used to detect misuse.

Deception resources should be isolated and monitored so suspicious interaction produces useful alerts without exposing production assets.

## Key Takeaways

- Compare threat actors by motivation, funding, sophistication, and access; actor labels do not determine every behavior.
- Organized crime commonly seeks money, nation-state actors often pursue strategic intelligence, and hacktivists promote a cause.
- Insider threats include malicious, negligent, accidental, and compromised users.
- A vector is a route of attack; the attack surface is the collection of exposed entry points; a vulnerability is a weakness.
- Social engineering exploits human trust and can bypass purely technical defenses.
- Supply chain compromises can spread through trusted relationships and updates.
- Distinguish SQLi, XSS, and CSRF by what each attack manipulates.
- Hardware, virtual machines, cloud services, and mobile devices all need lifecycle management and access controls.
- Least privilege, secure configuration, patching, monitoring, and awareness work together to reduce exposure.

