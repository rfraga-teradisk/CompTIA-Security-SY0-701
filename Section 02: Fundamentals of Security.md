# Fundamentals of Security

## Objectives

- 1.1 - Compare and contrast various types of security controls
- 1.2 - Summarize fundamental security concepts
- Understand the CIA triad, AAA, non-repudiation, and Zero Trust
- Explain the Zero Trust control plane and data plane
- Compare deception technologies and physical security controls
- Describe change management, documentation, and version control

## Table of Contents

1. [Information Security](#information-security)
2. [CIA Triad](#cia-triad)
3. [Non-Repudiation](#non-repudiation)
4. [Authentication, Authorization, and Accounting](#authentication-authorization-and-accounting)
5. [Security Control Categories](#security-control-categories)
6. [Security Control Types](#security-control-types)
7. [Threats, Vulnerabilities, and Risk](#threats-vulnerabilities-and-risk)
8. [Gap Analysis](#gap-analysis)
9. [Zero Trust](#zero-trust)
10. [Deception Technologies](#deception-technologies)
11. [Preventive Physical Security Controls](#preventive-physical-security-controls)
12. [Detective Physical Security Controls](#detective-physical-security-controls)
13. [Change Management](#change-management)
14. [Change Management Technical Considerations](#change-management-technical-considerations)
15. [Documentation and Version Control](#documentation-and-version-control)
16. [Key Takeaways](#key-takeaways)

## Information Security

- **Information Security:** Protecting data and information from unauthorized access, disclosure, modification, disruption, or destruction.
- **Information Systems Security:** Protecting systems that store, process, or transmit information.

Examples:
- Protecting customer records
- Securing servers and endpoints
- Restricting access to sensitive folders
- Monitoring logs for suspicious activity

## CIA Triad

- **Confidentiality:** Ensures information is only accessible to authorized users.
  - Example: Encryption, access control, data masking.

- **Integrity:** Ensures data remains accurate, complete, and unchanged unless modified by an authorized user.
  - Example: Hashing, checksums, digital signatures.

- **Availability:** Ensures systems and data are accessible when needed.
  - Example: Redundancy, backups, failover, disaster recovery.

## Non-Repudiation

- **Non-Repudiation:** Provides proof that an action or transaction cannot be denied later.
- Digital signatures are commonly used for non-repudiation.

Example:
- If a user digitally signs a document, the signature helps prove who signed it and that the document was not changed.

## Authentication, Authorization, and Accounting

- **Authentication:** Verifies identity.
- **Authorization:** Determines what access is allowed.
- **Accounting:** Tracks user actions for logs, audits, and investigations.

Example:
- Logging in with a password and MFA is authentication.
- Accessing only assigned folders is authorization.
- System logs showing file access are accounting.

## Security Control Categories

- **Technical Controls:** Technology-based controls.
  - Example: Firewall, encryption, MFA.

- **Managerial Controls:** Administrative or governance controls.
  - Example: Risk assessment, security policy, audit.

- **Operational Controls:** Day-to-day security processes.
  - Example: Security awareness, incident response, change management.

- **Physical Controls:** Controls that protect physical assets.
  - Example: Locks, cameras, guards, badges.

## Security Control Types

- **Preventive:** Stops an event before it happens.
- **Detective:** Identifies an event or suspicious activity.
- **Corrective:** Fixes or restores after an event.
- **Deterrent:** Discourages unwanted behavior.
- **Compensating:** Alternative control when the preferred control cannot be used.
- **Directive:** Tells users what is expected.

## Threats, Vulnerabilities, and Risk

- **Threat:** Anything that can cause harm.
- **Vulnerability:** A weakness that can be exploited.
- **Risk:** The possibility that a threat will exploit a vulnerability and cause impact.

Example:
- Threat: Attacker
- Vulnerability: Unpatched server
- Risk: Server compromise

## Gap Analysis

- **Gap Analysis:** A structured comparison of an organization's current security state with a desired future state, industry requirement, guideline, or best practice.
- It identifies missing or weak technical, managerial, operational, and physical controls.
- It helps an organization understand its cybersecurity risks, vulnerabilities, and residual risk.
- The results show which additional physical or logical safeguards may be required.

Example:
- Current state: No MFA on admin accounts.
- Desired state: MFA required for all admin accounts.
- Gap: Admin MFA is missing.

Common security gaps:
- Weak or shared credentials
- Untested or ineffective patch management
- Violations of least privilege or need to know
- Missing or unenforced acceptable use policies
- Weak physical security
- Configuration and deployment errors caused by poor change management
- Limited visibility, logging, or auditing

## Zero Trust

- **Zero Trust (ZT):** A security model that grants no implicit trust based only on a user's network location, physical location, device ownership, or previous access.
- It shifts security away from a static network perimeter and focuses protection on users, assets, data, and resources.
- Authentication and authorization are separate decisions that occur before a session to an enterprise resource is established.
- Zero Trust Network Access (**ZTNA**) applies Zero Trust principles to resource access.

Core ideas:
- Verify explicitly before granting access
- Apply least privilege and need to know
- Use separation of duties
- Continuously monitor activity and evaluate risk
- Segment resources into explicit trust zones
- Assume a breach may already have occurred
- Grant access to specific resources rather than trusting an entire network

### Adaptive Identity

- **Adaptive Identity:** Also called adaptive authentication or risk-based authentication; it adjusts authentication and access requirements according to context and risk.
- Decisions may consider the user, device, location, behavior, requested resource, and sensitivity of the data.
- A request for intellectual property, for example, may require stronger proof than access to a general intranet page.
- Adaptive identity supports users and systems whose roles or risk levels change over time.

### Threat Scope Reduction

- Zero Trust limits the resources available through any single account or session.
- Least privilege and segmentation reduce lateral movement and the potential blast radius of a compromise.
- A data- and asset-centric approach helps control complex environments with many communication patterns.

### Zero Trust Control Plane

- The **control plane** makes and administers access decisions. It is separate from the traffic-carrying data plane.
- The **Policy Decision Point (PDP)** contains the Policy Engine and Policy Administrator.

Control plane components:
- **Policy Engine (PE):** Evaluates enterprise policy and external signals to grant, deny, or revoke access to a resource.
- **Policy Administrator (PA):** Establishes or terminates the communication path by sending instructions to a Policy Enforcement Point.
- **Policy-driven access control:** Uses identity, device posture, resource sensitivity, threat intelligence, and other contextual information to make access decisions.

### Zero Trust Data Plane

- The **data plane** carries application and network traffic between a subject and an enterprise resource after policy is enforced.
- A **subject** may be a user, device, service, or non-person entity (**NPE**).
- The subject remains untrusted until the access request is evaluated and enforced.
- A **Policy Enforcement Point (PEP)** allows, monitors, or terminates the connection according to instructions from the control plane.

Examples of network PEPs:
- Edge routers and firewalls
- Software-defined perimeter access gateways
- Layer 2 and multilayer switches
- Authentication proxy servers

Examples of application PEPs or protected resource boundaries:
- API gateways
- Resource groups
- VLANs
- Code repositories
- Trusted cloud services

Explicitly segmented zones may include:
- Data centers
- Demilitarized zones (**DMZs**)
- Public Internet connections
- Private or VPN-only cloud subnets and VLANs
- Honeynets

Typical access flow:
1. A subject requests an enterprise resource through a PEP.
2. The PEP sends the request to the PDP through the control plane.
3. The Policy Engine evaluates identity, policy, context, and risk.
4. The Policy Administrator instructs the PEP to grant, deny, or terminate access.
5. If access is granted, authorized traffic passes through the data plane.

## Deception Technologies

- **Deception Technology:** A decoy resource designed to attract, detect, redirect, or study malicious activity.
- Deception systems can slow attackers, reveal lateral movement, and provide defenders with information about attack methods.
- Decoys must be isolated and monitored so they do not become a path into production systems.

### Honeypot

- A **honeypot** is a single decoy system, service, or resource made attractive to attackers.
- Examples include a decoy web server, FTP server, SharePoint server, or file.
- Honeypots are often virtual machines placed near, but separated from, public-facing systems.

### Honeynet

- A **honeynet** is a network of honeypots containing intentionally vulnerable decoy systems and services.
- It resembles a production environment and can redirect or delay attackers.
- Security teams use it to observe attack patterns, tactics, and kill-chain activity without exposing real assets.

### Honeyfiles and Honeytokens

- A **honeyfile** is a decoy file whose access or use triggers an alert.
- A **honeytoken** is fake data or a credential-like artifact that has no legitimate use; any activity involving it is suspicious.
- Examples include decoy cloud access keys, credentials, database records, or links to fake resources.
- They can reveal malicious insiders or external attackers performing enumeration, privilege escalation, or lateral movement.
- They should support a legitimate investigation and monitoring program, not be used to entrap employees.

## Preventive Physical Security Controls

- Preventive physical controls stop or restrict unauthorized physical access to people, facilities, systems, and data.

### Fences and Gates

- **Fences** establish a perimeter and deter or prevent unauthorized entry and exit.
- Internal fencing can protect generators, junction boxes, dumpsters, and document-destruction collection points.
- Height, construction, barbed wire, electrification, and warning signs should match the property's risk.
- **Gates** control vehicle or pedestrian entry and may include guards, barricades, or one-way tire barriers.

### Bollards

- **Bollards** are permanent or temporary posts that guide pedestrians or prevent vehicles from entering protected areas.
- They are commonly made of concrete or reinforced metal; advanced bollards may retract or contain cameras and sensors.

### Access Control Vestibules and Mantraps

- An **access control vestibule** is a fortified entryway, typically using two interlocking doors and forced-entry-resistant materials.
- A **mantrap** allows only one door to open at a time and may limit entry to one person.
- These controls reduce tailgating and piggybacking while allowing identity checks before entry.
- Supporting technologies may include badge readers, biometrics, cameras, intercoms, security glazing, and electronic locks.

### Access Badges and Cards

- An access badge is a **something you have** authentication factor.
- Permanent and temporary badges should identify the holder and restrict access according to role and need.
- Visitors should register, provide identification when required, receive temporary credentials, and be recorded in a visitor log.
- Organizations should enforce a no-tailgating or no-piggybacking policy for employees, contractors, and guests.

### Security Guards

- Guards can act as preventive, deterrent, and detective controls and may provide rapid incident response.
- Planning considerations include staffing hours, location, training, background checks, licensing, employment arrangement, and whether guards are armed.

## Detective Physical Security Controls

### Video Surveillance

- Video surveillance and closed-circuit television (**CCTV**) monitor and record activity around a facility.
- Cameras are primarily detective controls, although their visible presence can also deter attackers.
- Alerts should be generated if a camera is disabled, and recordings should be transferred to secure storage.
- Indoor, outdoor, visible, and concealed cameras should be positioned to minimize blind spots.

### Lighting

- Lighting improves the effectiveness of cameras, guards, and sensors, beginning at the perimeter and continuing through layers of physical defense.
- Common technologies include LED, mercury-vapor, sodium-vapor, and quartz lighting.

Lighting modes:
- **Continuous:** Regular, always-on outdoor lighting.
- **Standby:** Activates automatically or manually when primary lighting fails or more light is required.
- **Movable:** Searchlights or floodlights used temporarily or to supplement other lighting.
- **Emergency:** Battery- or generator-powered lighting used during an outage or emergency.

### Sensors and Alarms

- **Photoelectric:** Detects interruption of a light beam.
- **Passive infrared:** Detects changes in infrared energy.
- **Vibration or pressure:** Detects movement or force on a protected surface.
- **Acoustic:** Detects changes in sound waves.
- **Microwave:** Detects changes in high-frequency radio waves.
- **Ultrasonic:** Uses high-frequency sound waves to detect motion.
- **Electromechanical:** Detects a broken circuit when a door or window opens.
- **Electrostatic:** Detects changes in an electrostatic field.
- **Environmental:** Detects temperature, moisture, smoke, or other hazardous conditions.

Sensors may trigger:
- A light, bell, horn, or display-panel alert
- A text message, email, or phone notification
- A silent alarm to security personnel or law enforcement

## Change Management

- **Change Management:** A methodical process for controlling modifications to organizational goals, processes, configurations, and technologies.
- It is also called **change control** and helps reduce outages, security weaknesses, unauthorized changes, and failed migrations.
- Configuration management normally establishes a known baseline before normal, standard, or emergency changes are made.

Typical lifecycle:
1. Submit a change request.
2. Review its business need, risk, impact, dependencies, and ownership.
3. Obtain approval from the appropriate authority.
4. Document the implementation, testing, and rollback procedures.
5. Test the change and record the results.
6. Implement it during an approved maintenance window.
7. Validate the result and complete an after-action review.

### Business Processes

- **Approval:** The review process should be documented and may be iterative as details and risks are resolved.
- **Ownership:** The asset owner, custodian, or controller must be identified and involved according to the access control model.
- **Stakeholders:** Use a **RACI** matrix to identify who is Responsible, Accountable, Consulted, and Informed. A task has at least one responsible party and only one accountable party.
- **Impact analysis:** Compares the current and proposed states to identify what will change, who will be affected, and what must be communicated.
- **Test results:** Provide evidence that the change works and does not create unacceptable security or operational problems.
- **Backout plan:** A rollback or fallback procedure restores the previous state if testing or implementation fails. It must exist before implementation.
- **Maintenance window:** An approved time period for making a change while minimizing disruption.
- **Standard Operating Procedure (SOP):** Detailed, repeatable instructions for completing a task consistently. Automation and orchestration can improve reliability.
- Prefer small, controlled changes over combining several high-impact modifications.

## Change Management Technical Considerations

- **Allow lists and deny lists:** Define which subjects, applications, addresses, or actions are permitted or prohibited during a change.
- **Restricted activities:** Least privilege and separation of duties limit who can request, approve, implement, and validate changes.
- **Downtime:** Planned and unplanned downtime affect availability and must be considered before changes and migrations.
- **Service and application restarts:** A change may require a restart; dependencies and secure startup states must be understood first.
- **Legacy applications:** Older software may have compatibility, support, or security limitations that make changes more risky.
- **Dependencies:** Changes to one component can affect connected services, libraries, drivers, APIs, networks, or business processes.
- Post-change validation should confirm security controls, logging, interoperability, and availability still operate as expected.

## Documentation and Version Control

- Security and configuration records should use a consistent tagging and labeling scheme.
- A **Configuration Management Database (CMDB)** records configuration items and their relationships.
- A **Configuration Management System (CMS)** is the broader collection of data, tools, utilities, and processes used to support configuration management.
- Current configuration data supports asset, change, patch, incident, problem, availability, release, and deployment management.
- Version control provides a history of changes, identifies who made them, supports review, and enables rollback to a known version.

Version-controlled items may include:
- Operating system builds
- Application updates
- Device drivers
- License changes
- Patches and upgrades
- Source code
- Container packages and microservices
- Firmware and trusted platform module updates
- Infrastructure and configuration files

## Key Takeaways

- The CIA triad is the foundation of security.
- AAA explains identity and access activity.
- Security controls should be layered to prevent, detect, and correct security problems.
- Gap analysis identifies the difference between the current and desired security state.
- Zero Trust separates policy decisions in the control plane from enforcement and traffic in the data plane.
- Deception technologies expose suspicious behavior without risking genuine resources.
- Physical security combines preventive, detective, and deterrent safeguards.
- Controlled, documented, tested, and reversible changes reduce security and availability risk.
