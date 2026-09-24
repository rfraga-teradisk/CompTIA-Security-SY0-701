# Audits and Assessments

## Objectives
- Understand the purpose of audits and assessments
- Compare common security assessment types
- Know what evidence is used to prove control effectiveness

## Table of Contents

1. [Audits](#audits)
2. [Assessments](#assessments)
3. [Assessment Types](#assessment-types)
4. [Audit Evidence](#audit-evidence)
5. [Findings](#findings)
6. [Remediation Tracking](#remediation-tracking)
7. [Key Takeaways](#key-takeaways)

## Audits

- **Audit:** A formal review used to verify whether controls, policies, procedures, standards, regulations, or contracts are being followed.
- Audits may be internal or external.
- Audit results may create findings that require remediation.

Common audit goals:
- Verify compliance
- Confirm control operation
- Identify gaps
- Support regulatory requirements
- Provide evidence to leadership or customers

## Assessments

- **Assessment:** A review used to understand risk, control effectiveness, technical weaknesses, or security posture.
- Assessments are usually broader and more improvement-focused than audits.

## Assessment Types

- **Risk Assessment:** Identifies and prioritizes risks.
- **Vulnerability Assessment:** Finds and prioritizes technical weaknesses.
- **Penetration Test:** Attempts to exploit weaknesses to prove real-world impact.
- **Configuration Review:** Compares systems against secure baselines.
- **Access Review:** Checks whether accounts and effective permissions still match approved job duties and data-owner decisions.
- **Tabletop Exercise:** Walks through a scenario to test response decisions.
- **Compliance Assessment:** Checks alignment with a standard or regulation.

### Reviewing Access

- Compare accounts, group and role memberships, service accounts, and inherited permissions with current responsibilities. Check access changes when people join, move roles, or leave; remove stale or excessive privileges (**privilege creep**).
- Include sensitive data stores, cloud storage sharing and policies, code repositories, privileged accounts, and physical badge permissions as applicable. Record the reviewer, decision, date, and evidence that changes were completed.
- Configuration and vulnerability scans or penetration tests may reveal exposed resources, but they do not replace a review of who is authorized to use them. See [NIST SP 800-53, AC-2 and AC-6](https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final).

## Audit Evidence

- **Evidence:** Proof that a control exists or is operating correctly.

Examples of evidence:
- Policy document
- Procedure document
- Screenshot of configuration
- Access review export
- Vulnerability scan report
- Patch report
- Backup test result
- Log sample
- Incident report
- Training completion record

## Findings

- **Finding:** A documented issue discovered during an audit or assessment.

A finding should include:
- Description
- Affected system or process
- Evidence
- Risk or impact
- Recommendation
- Owner
- Due date
- Status

## Remediation Tracking

- Findings should be tracked until validated as fixed.
- Remediation should include proof, not only a statement that the issue was resolved.

Example:
- Finding: Local admin access is too broad.
- Recommendation: Remove unnecessary local administrator rights.
- Evidence of closure: Updated group membership export and access review approval.

## Key Takeaways

- Audits verify whether requirements are being followed.
- Assessments help identify weaknesses and improvement areas.
- Evidence is important because it proves that security controls are working.