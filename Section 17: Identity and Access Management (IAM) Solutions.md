# Identity and Access Management (IAM) Solutions

## Objectives
- 4.6 - Given a scenario, implement identity and access management
- Understand authentication, authorization, and accounting
- Compare common access control models

## Table of Contents

1. [IAM](#iam)
2. [AAA](#aaa)
3. [Authentication Factors](#authentication-factors)
4. [MFA](#mfa)
5. [Access Control Models](#access-control-models)
6. [File Permissions](#file-permissions)
7. [Least Privilege and Separation of Duties](#least-privilege-and-separation-of-duties)
8. [Identity Lifecycle](#identity-lifecycle)
9. [Privileged Access Management](#privileged-access-management)
10. [Key Takeaways](#key-takeaways)

## IAM

- **Identity and Access Management (IAM):** Processes and technologies used to manage identities and control access to systems and data.
- IAM answers two main questions:
  - Who are you?
  - What are you allowed to access?

## AAA

- **Authentication:** Verifies identity.
- **Authorization:** Determines what the identity can access.
- **Accounting:** Tracks activity for logs, audits, and investigations.

Example:
- A user logs in with a password and MFA. That is authentication.
- The user can access only the finance folder. That is authorization.
- The system logs file access. That is accounting.

## Authentication Factors

- **Something you know:** Password or PIN.
- **Something you have:** Token, smart card, authenticator app.
- **Something you are:** Biometric factor.
- **Somewhere you are:** Location-based factor.
- **Something you do:** Behavior-based factor.

## MFA

- **MFA:** Multi-Factor Authentication uses two or more different factor types.
- MFA reduces the risk of account compromise if a password is stolen.

Examples:
- Password + authenticator app
- Smart card + PIN
- Password + biometric

## Access Control Models

- **DAC:** Discretionary Access Control; owner decides who gets access.
- **MAC:** Mandatory Access Control; access is based on labels and classifications.
- **RBAC:** Role-Based Access Control; access is based on job role.
- **ABAC:** Attribute-Based Access Control; access is based on attributes such as user, device, time, location, or risk.
- **Rule-Based Access:** Access is controlled by defined rules.

### Physical and Network Access Systems

- A **physical access control system (PACS)** grants and records entry to facilities. It may use badges, smart cards, or biometrics and may receive identity lifecycle data from HR or a directory. A certificate authority can issue certificates used to authenticate credentials.
- **PIV** means Personal Identity Verification: a federal identity credential that can be used with a PACS. **IEEE 802.1X** controls network port access, and **EAP-TLS** is a certificate-based network authentication method. These systems can share identity data, but facility and network access have separate authorization decisions. See [NIST SP 800-116 Rev. 1](https://csrc.nist.gov/pubs/sp/800/116/r1/final) and [RFC 9190](https://www.rfc-editor.org/rfc/rfc9190.html).

## File Permissions

- **Read** allows viewing file contents; **write** allows modifying them; **execute** allows running an executable file or program. Directory permissions have different effects, such as listing entries or traversing the directory.
- Windows can grant permissions to users and groups through file-system access control entries. On Linux, owner, group, and other mode bits control basic read, write, and execute access; chmod changes those mode bits.
- Grant only the access required for the task and review inherited or group permissions when troubleshooting access.

## Least Privilege and Separation of Duties

- **Least privilege:** Give users, service accounts, and processes only the access needed for assigned tasks. Review privileges when roles change and remove access that is no longer needed. **Need to know** applies this idea to access to particular information; a clearance or job title alone does not grant access. See [NIST's least-privilege definition](https://csrc.nist.gov/glossary/term/least_privilege).
- **Separation of duties (SoD):** Divide sensitive steps so one person cannot complete a risky transaction alone. For example, one employee creates a purchase order and another approves payment. This reduces fraud and error risk but does not prevent collusion.
- **Static SoD:** Do not assign conflicting roles to the same person, such as both preparing and approving payments.
- **Dynamic SoD / two-person rule:** Check the particular transaction when it occurs and require approval by a different authorized person. A second signature, approval, or key can enforce dual control where the process requires it. See [NIST's SoD definition](https://csrc.nist.gov/glossary/term/separation_of_duty).
- Temporary privilege elevation should use an approved, time-limited workflow with authentication and logging. Routine privileged access can be managed through PAM; not every elevation requires a full change-control ticket or an ITIL process.
- **Rotation of duties and mandatory absence** are related detective controls: another person performs the work, making hidden irregularities easier to find. A consecutive two-week absence is an example in some banking guidance, not a universal Security+ requirement. See the [OCC fraud-risk guidance](https://occ.treas.gov/news-issuances/bulletins/2019/bulletin-2019-37.html).

## Identity Lifecycle

1. Create account after approval.
2. Assign least-privilege access.
3. Review access regularly.
4. Modify access when role changes.
5. Disable or remove access during offboarding.

### Personnel Offboarding

- **Offboarding** is the coordinated process for an employee or contractor who leaves or changes roles. HR, the manager, IT, physical security, and other owners should agree on the effective time and responsibilities. **Decommissioning** usually means retiring a system, device, or service; the terms are not interchangeable.
- At the effective time, disable accounts and revoke sessions, tokens, keys, badges, remote access, and privileges as appropriate. Check local accounts and third-party SaaS or cloud access as well as centrally managed SSO accounts. Rotate shared secrets the person knew; preserve audit records rather than automatically deleting accounts. See [CIS Control 6.2](https://cas.docs.cisecurity.org/en/latest/source/Controls6/).
- Recover company devices, identification cards, and other property. Transfer ownership of needed files, repositories, services, and business records through an approved process, including any retention or legal-hold requirements. Track completion and verify that access was removed. See [NIST SP 800-53 PS-4](https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final).
- Apply ordinary, policy-based monitoring to sensitive actions; escalate based on evidence or specific risk. Do not classify every departing person as a threat actor.

## Privileged Access Management

- **PAM:** Privileged Access Management controls and monitors high-privilege accounts.
- Privileged accounts should have:
  - MFA
  - Strong logging
  - Approval workflow
  - Session recording when needed
  - Time-limited access

## Key Takeaways

- IAM is one of the most important security controls.
- Compromised accounts are common in real attacks, so identity must be protected carefully.