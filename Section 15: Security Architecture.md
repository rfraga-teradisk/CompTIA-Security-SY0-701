# Security Architecture

## Objectives
- 3.1 - Compare and contrast security implications of different architecture models
- Understand secure design principles
- Explain segmentation, zero trust, defense in depth, and least privilege

## Table of Contents

1. [Security Architecture](#security-architecture)
2. [Defense in Depth](#defense-in-depth)
3. [Zero Trust](#zero-trust)
4. [Segmentation](#segmentation)
5. [Least Privilege](#least-privilege)
6. [Cloud Architecture](#cloud-architecture)
7. [Serverless Technologies](#serverless-technologies)
8. [Containers and Microservices](#containers-and-microservices)
9. [Infrastructure as Code](#infrastructure-as-code)
10. [Application Architecture](#application-architecture)
11. [Architectural Considerations](#architectural-considerations)
12. [Key Takeaways](#key-takeaways)

## Security Architecture

- **Security Architecture:** The design of systems, networks, applications, cloud resources, and controls to protect confidentiality, integrity, and availability.
- Good architecture reduces attack paths and limits damage when one control fails.

## Defense in Depth

- **Defense in Depth:** Using multiple layers of security controls.
- If one control fails, another control may still reduce the attack.

Examples:
- Firewall
- MFA
- Endpoint protection
- Network segmentation
- Logging and monitoring
- Backups
- Security awareness

## Zero Trust

- **Zero Trust:** Security model based on never trusting by default and always verifying.
- Zero trust assumes threats may exist inside and outside the network.

Zero trust ideas:
- Verify identity
- Use least privilege
- Check device health
- Monitor activity
- Segment access
- Continuously evaluate risk

## Segmentation

- **Segmentation:** Dividing networks or systems into smaller areas and controlling traffic between them.
- Segmentation can reduce lateral movement and limit the impact of a compromise. It can also reduce unnecessary broadcast traffic, depending on the network design.
- **Isolation:** Restricting communication between areas. A VLAN separates Layer 2 traffic, but it does not by itself enforce a security policy when routing between VLANs is allowed.

Examples:
- Separate guest Wi-Fi from internal networks
- Separate servers from user workstations
- Separate payment systems from general systems
- Use VLANs, subnets, firewalls, and access control lists to enforce approved traffic paths

### Security Zones and DMZ

- A **security zone** groups systems with similar access requirements. One zone can contain multiple subnets or VLANs, and a VLAN is a Layer 2 segment rather than a routable network by itself. Zone boundaries and traffic rules are design choices, not fixed properties of VLANs. See [NIST's enterprise network guidance](https://tsapps.nist.gov/publication/get_pdf.cfm?pub_id=935714).
- A **DMZ**, also called a screened subnet, is a perimeter segment for services that must accept traffic from less trusted networks, such as public web or email servers. A firewall can restrict traffic from the DMZ to internal application and data systems. See [NIST's firewall guidance](https://csrc.nist.gov/pubs/sp/800/41/r1/final).
- In a three-interface firewall example, the interfaces may connect the Internet, the internal network, and the DMZ. Public-facing, application, data, and management tiers should communicate only on required ports and paths. Other valid designs use multiple firewalls, cloud controls, or more zones.
- The lesson's labels **PAZ** (public access zone) and **ZIP** (zone interface point) describe its example design; they are not required names or universal rules. A DMZ is not the only zone that can have controlled Internet access.
- A honeynet can be placed in a separate, monitored zone to observe suspicious activity. Keep it isolated from production systems; it is not a required component of the Internet-to-DMZ path. See [deception technologies in Section 02](<Section 02: Fundamentals of Security.md#deception-technologies>).

## Least Privilege

- **Least Privilege:** Users, service accounts, and processes should have only the access needed for assigned tasks.
- Reduces impact if an account or system is compromised. Review privileges as responsibilities change; see [least privilege and separation of duties in Section 17](<Section 17: Identity and Access Management (IAM) Solutions.md#least-privilege-and-separation-of-duties>).

## Cloud Architecture

Cloud architecture should consider:
- Shared responsibility model
- IAM roles and permissions
- Security groups
- Encryption
- Logging
- Key management
- Backup
- Public exposure

### Cloud Service Models

| Model | Provider supplies | Customer normally manages |
| --- | --- | --- |
| **IaaS** | Compute, storage, networking, and the underlying infrastructure | Guest operating systems, deployed applications, data, identities, and permitted network settings. |
| **PaaS** | A managed application platform plus the underlying infrastructure | Deployed application code, data, identities, and available platform configuration. |
| **SaaS** | A finished application and its supporting stack | Data, users, permissions, and available tenant settings. |

These are [NIST's service models](https://csrc.nist.gov/pubs/sp/800/145/final), not a fixed classification for every database, container service, serverless function, or security product. Check the specific service's responsibility matrix. The provider secures its infrastructure; customers retain responsibilities for their data, accounts, endpoints, and configuration even with SaaS. An IaaS customer usually maintains its guest OS, while a managed service may shift that task to the provider. See [Azure's responsibility matrix](https://learn.microsoft.com/en-us/azure/security/fundamentals/shared-responsibility) and [AWS's shared responsibility model](https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/shared-responsibility.html).

### Cloud Deployment Models

- **Public cloud:** Infrastructure is offered for open use by the general public. A customer's workloads can still be private and reachable only through approved paths; a public-facing website does not determine the deployment model.
- **Private cloud:** Cloud infrastructure is reserved for one organization and can run on or off premises. A private subnet or virtual private cloud inside a shared public-cloud service is not automatically a private cloud.
- **Community cloud:** Infrastructure is reserved for a defined group of organizations with shared requirements, such as regulatory or mission concerns; it is not merely an online community.
- **Hybrid cloud:** Two or more distinct private, community, or public cloud infrastructures remain separate but are linked for data or application portability. On-premises virtualization alone does not make a private cloud, and edge computing is a separate architectural pattern. See [NIST SP 800-145](https://csrc.nist.gov/pubs/sp/800/145/final).

### Cloud Partners and Connectivity

- Brokers, managed security service providers (MSSPs), cloud access security brokers (CASBs), and independent auditors have different roles. A SOC 2 report is an attestation, not a generic “SOC certification”; [CSA STAR](https://cloudsecurityalliance.org/star) has separate certification and attestation paths.
- Dedicated connections such as AWS Direct Connect, Google Cloud Interconnect, and Azure ExpressRoute connect sites to providers without relying on a normal Internet transit path. Capacity depends on the service and configuration; a private circuit does not necessarily encrypt traffic. For example, [AWS Direct Connect does not encrypt transit traffic by default](https://docs.aws.amazon.com/directconnect/latest/UserGuide/encryption-in-transit.html).

## Serverless Technologies

- **Serverless** means the provider operates the underlying servers; scaling may be automatic or require customer configuration. Application code still runs on servers. Customers remain responsible for code, data, identity, permissions, network settings, and service configuration where exposed.
- **Functions as a service (FaaS):** [AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html) and [Azure Functions](https://learn.microsoft.com/en-us/azure/azure-functions/functions-overview) run code in response to events. An IoT event could invoke a function that validates data and starts a workflow; the exact integrations must be configured.
- **Serverless containers:** [AWS Fargate](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/AWS_Fargate.html) runs ECS or EKS containers without customer-managed host instances. Customers still select CPU and memory, configure networking and IAM, and maintain container images. Fargate gives tasks separate isolation boundaries; that does not remove application security duties. See [AWS's Fargate responsibility model](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/security-shared-model.html).
- **Serverless databases:** [Amazon Aurora Serverless v2](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/aurora-serverless-v2.how-it-works.html) scales database compute within a configured capacity range. Aurora is not always serverless; this is a specific configuration. Application code can read and write its tables, while CloudWatch can report metrics.
- **Limits and billing:** Scaling is constrained by quotas, configured limits, and service behavior. Charges depend on the service and plan: [Fargate bills for allocated task resources while tasks run](https://aws.amazon.com/fargate/pricing/), and [Azure Functions can bill for always-ready instances](https://learn.microsoft.com/en-us/azure/azure-functions/flex-consumption-plan). Plan for availability, observability, cold starts, and costs rather than assuming zero idle charges or unlimited capacity.

## Containers and Microservices

- A **container image** packages application code, its needed language runtime, and software dependencies. A running **container** is an isolated process created from that image. Images do not bundle physical hardware; CPU and memory requests or limits are set by the runtime or orchestrator. Containers usually share a host operating-system kernel, so their isolation and security depend on the runtime and host configuration. See [Kubernetes container concepts](https://kubernetes.io/docs/concepts/containers/), [Docker resource limits](https://docs.docker.com/engine/containers/resource_constraints), and [NIST SP 800-190](https://csrc.nist.gov/pubs/sp/800/190/final).
- Docker Engine is one way to build and run containers. Kubernetes orchestrates them using compatible runtimes such as containerd or CRI-O; it does not require Docker Engine. A managed service such as [AWS Fargate](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/AWS_Fargate.html) still runs on provider-managed hosts and gives each task a separate isolation boundary. Maintain image provenance, patch dependencies, limit privileges and resource use, and secure network access.
- **Microservices** split an application into independently deployable services with defined responsibilities and interfaces. They may communicate through APIs or asynchronous messages. Microservices describe the application's architecture; containers describe packaging and execution. Either can be used without the other. See [Azure's microservices architecture guidance](https://learn.microsoft.com/en-us/azure/architecture/microservices/).
- Independent deployment and scaling can help teams, but more services also increase network traffic, operational complexity, data-consistency work, and the number of interfaces to secure. A microservices design does not automatically improve speed or resilience.

## Infrastructure as Code

- **Infrastructure as code (IaC)** defines and provisions infrastructure through machine-readable configuration instead of repeated manual setup. Templates can describe networks, compute, storage, and application dependencies. Syntax depends on the tool: [AWS CloudFormation supports JSON and YAML](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/best-practices.html); [Terraform normally uses HCL and also supports JSON](https://developer.hashicorp.com/terraform/language/files); [Ansible playbooks use YAML](https://docs.ansible.com/projects/ansible/latest/playbook_guide/playbooks_intro.html).
- Reusable modules and variables help deploy related environments consistently. Put templates in version control, review changes, validate them, and deploy through an approved pipeline. Keep credentials out of templates. IaC can serve as an approved description of **desired state**, but it does not automatically make every live resource match that state.
- Direct console or API changes can cause **configuration drift**. Detect and reconcile drift; preview potentially disruptive changes before deployment. [CloudFormation change sets and drift detection](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/best-practices.html) support these checks.
- **Idempotence** means repeating a supported operation has the same intended result, not that all deployments are identical. Ansible notes that most modules are idempotent but not every module or playbook is. Test repeat runs and account for different inputs and platform state. See [Ansible's playbook guidance](https://docs.ansible.com/projects/ansible/latest/playbook_guide/playbooks_intro.html).

## Application Architecture

Secure applications should include:
- Authentication
- Authorization
- Input validation
- Secure session management
- Secure APIs
- Error handling
- Logging
- Secrets management

## Architectural Considerations

- **Resilience:** Keep essential functions operating through disruption, possibly at reduced capacity, and recover within the time the business can tolerate. A business impact analysis (BIA) helps set recovery priorities and objectives; redundancy, failover, backups, and tested recovery plans help meet them. See [NIST's resilience definition](https://csrc.nist.gov/glossary/term/resilience).
- **Availability, reliability, and durability:** Availability concerns whether a service works when needed; reliability concerns how consistently it performs its intended function; durability concerns whether stored data remains intact over time. The availability calculation and treatment of planned maintenance depend on the defined measurement or SLA. See [AWS availability guidance](https://docs.aws.amazon.com/wellarchitected/latest/reliability-pillar/availability.html) and [Google Cloud's durability definition](https://docs.cloud.google.com/storage/docs/availability-durability).
- **Cost and performance:** Compare initial and ongoing cost, maintenance, capacity, latency, throughput, and the service levels users require.
- **Scalability and deployment:** Scale out by adding instances or nodes; scale up by increasing resources on a machine. Autoscaling depends on workload and platform support. Infrastructure as code and automated patching can improve repeatability but still require review and testing.
- **Risk and power:** Cloud services and insurance can shift some operational or financial risk, but the organization retains responsibilities under the shared responsibility model. For on-premises systems, assess redundant feeds, UPS capacity, generators, and power quality. See [AWS shared responsibility](https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/shared-responsibility.html).

## Key Takeaways

- Security architecture is secure design before problems happen.
- Good design uses layers, least privilege, segmentation, and monitoring.