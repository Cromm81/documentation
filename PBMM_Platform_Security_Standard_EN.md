# PROTECTED B / MEDIUM INTEGRITY / MEDIUM AVAILABILITY
# OPERATIONAL SECURITY STANDARD
## Azure Landing Zone Platform

**Classification:** PROTECTED B  
**Document Version:** 1.0  
**Effective Date:** [DATE]  
**Review Date:** [DATE + 1 YEAR]  
**Document Owner:** [ORGANIZATION NAME]  
**Security Authority:** [NAME/TITLE]

---

# DOCUMENT CONTROL

| Version | Date | Author | Description |
|---------|------|--------|-------------|
| 1.0 | [DATE] | [AUTHOR] | Initial Release |

**Distribution List:**
- Platform Security Authority
- Cloud Platform Operations
- Security Operations Centre
- Client Tenant Administrators
- Change Advisory Board
- Internal Audit

---

# TABLE OF CONTENTS

1. Introduction
2. Purpose and Scope
3. Cloud Security Profile
4. Governance Framework
5. Shared Responsibility Model
6. Risk Management Framework
7. Identity and Access Management
8. Network Security
9. System and Communications Protection
10. Configuration Management
11. Change Management
12. Audit and Accountability
13. Incident Response
14. Contingency Planning
15. Vulnerability Management
16. Data Protection
17. Continuous Monitoring
18. Platform Operations
19. Client Onboarding Security
20. Roles and Responsibilities
21. Exception Management
22. Compliance Verification
23. Document Maintenance
Appendix A: ITSG-33 Control Mapping
Appendix B: Evidence Requirements
Appendix C: Control Inheritance Model
Appendix D: Glossary

---

# 1. INTRODUCTION

## 1.1 Background

The Government of Canada has established security requirements for cloud-based information systems through the Canadian Centre for Cyber Security (CCCS) cloud security framework and the ITSG-33 security control catalogue. Organizations operating information systems that process, store, or transmit Protected B information SHALL implement security controls commensurate with the sensitivity of the information and the operational requirements of the system.

This Operational Security Standard establishes the security policies, procedures, and technical controls for the Azure Landing Zone Platform operated by [ORGANIZATION NAME]. The platform provides foundational cloud infrastructure services supporting multiple client workloads under a hub-and-spoke architecture model.

## 1.2 Document Structure

This document is organized into the following sections:

- **Sections 1-3** establish the document context, scope, and security profile
- **Sections 4-6** define governance, shared responsibility, and risk management frameworks
- **Sections 7-17** specify security control implementation requirements
- **Sections 18-19** define operational procedures and client onboarding
- **Sections 20-23** establish roles, exceptions, compliance, and maintenance
- **Appendices** provide control mappings, evidence requirements, and supporting materials

## 1.3 Compliance Framework

This standard aligns with the following frameworks and requirements:

- **ITSG-33:** IT Security Risk Management: A Lifecycle Approach
- **CCCS PBMM Cloud Profile:** Protected B / Medium Integrity / Medium Availability
- **Treasury Board Policy on Government Security**
- **Directive on Security Management**
- **Treasury Board Standard on Security Categorization**
- **Microsoft Azure Government of Canada Compliance Documentation**

## 1.4 Terminology

Throughout this document, the following terminology SHALL be interpreted as defined:

- **SHALL / MUST:** Indicates a mandatory requirement
- **SHOULD:** Indicates a recommended practice that may be deviated from with documented justification
- **MAY:** Indicates an optional practice
- **Platform:** The Azure Landing Zone infrastructure and shared services
- **Client:** A tenant or workload owner consuming platform services
- **Spoke:** A client subscription connected to the platform hub

---

# 2. PURPOSE AND SCOPE

## 2.1 Purpose

The purpose of this Operational Security Standard is to:

a) Define the security governance framework for the Azure Landing Zone Platform;

b) Establish security control requirements aligned with ITSG-33 and the CCCS PBMM cloud profile;

c) Document operational security procedures for platform management;

d) Define the shared responsibility model between the platform team, clients, and Microsoft Azure;

e) Provide a foundation for Security Assessment and Authorization (SA&A) activities;

f) Enable consistent security posture across all platform-hosted workloads.

## 2.2 Scope

### 2.2.1 In Scope

This standard applies to:

a) **Platform Infrastructure:**
   - Management group hierarchy and subscription structure
   - Hub virtual network and connectivity services
   - Azure Firewall and network security controls
   - Centralized logging and monitoring infrastructure
   - Identity and access management services
   - Security tooling (Microsoft Defender for Cloud, Microsoft Sentinel)
   - Platform management subscriptions
   - Key management infrastructure

b) **Platform Operations:**
   - Platform deployment and configuration
   - Change management for platform components
   - Security monitoring and incident response
   - Client onboarding and offboarding
   - Platform maintenance and patching

c) **Platform Personnel:**
   - Platform administrators
   - Security operations personnel
   - Network operations personnel
   - Service desk personnel with platform access

### 2.2.2 Out of Scope

This standard does not cover:

a) Client workload security controls (defined in workload-specific security documentation)
b) Application-level security requirements
c) Client data classification and handling (client responsibility)
d) End-user device security
e) Physical security of Microsoft data centres (Microsoft responsibility)

### 2.2.3 System Boundary

The authorization boundary for this platform encompasses:

- Azure tenant: [TENANT ID]
- Management groups: Platform, Landing Zones, Sandbox, Decommissioned
- Platform subscriptions: Identity, Connectivity, Management, Security
- Spoke subscriptions: [CLIENT NAMING CONVENTION]
- Azure regions: Canada Central (primary), Canada East (secondary)

## 2.3 Intended Audience

This document is intended for:

- Platform Security Authority and security assessors
- Cloud Platform Engineering and Operations teams
- Security Operations Centre personnel
- Client security representatives
- Internal and external auditors
- Change Advisory Board members

---

# 3. CLOUD SECURITY PROFILE

## 3.1 Security Categorization

The Azure Landing Zone Platform has been categorized according to the Treasury Board Standard on Security Categorization:

| Security Objective | Category | Rationale |
|-------------------|----------|-----------|
| Confidentiality | Protected B | Platform hosts client systems processing Protected B information |
| Integrity | Medium | Compromise of platform integrity could affect multiple client workloads |
| Availability | Medium | Platform supports business operations with defined recovery requirements |

**Aggregate Profile:** Protected B / Medium Integrity / Medium Availability (PBMM)

## 3.2 CCCS Cloud Profile Alignment

This platform operates under the CCCS PBMM cloud profile, which requires:

a) Implementation of ITSG-33 security controls at the PBMM baseline;
b) Use of a CCCS-assessed cloud service (Microsoft Azure Canada);
c) Data residency within Canadian borders;
d) Encryption of data at rest and in transit;
e) Centralized security monitoring and logging;
f) Formal security governance and risk management.

## 3.3 Cloud Service Model

The platform utilizes Infrastructure as a Service (IaaS) and Platform as a Service (PaaS) components from Microsoft Azure. The shared responsibility model (Section 5) defines security responsibilities across the cloud provider, platform team, and clients.

## 3.4 Data Residency

All platform data SHALL reside within Canadian Azure regions:

- **Primary Region:** Canada Central (Toronto)
- **Secondary Region:** Canada East (Quebec City)

Data SHALL NOT be replicated to, processed in, or accessible from regions outside Canada unless explicitly authorized through the exception process defined in Section 21.

## 3.5 Cloud Guardrails

The platform implements the Government of Canada Cloud Guardrails:

| Guardrail | Implementation |
|-----------|---------------|
| GR-1: Protect user accounts and identities | Entra ID with MFA, PIM, Conditional Access |
| GR-2: Manage access | RBAC, least privilege, JIT access |
| GR-3: Secure endpoints | Defender for Endpoint integration |
| GR-4: Enterprise monitoring accounts | Break-glass accounts with monitoring |
| GR-5: Data location | Canada-only region configuration |
| GR-6: Protection of data-at-rest | Platform-managed encryption |
| GR-7: Protection of data-in-transit | TLS 1.2+ enforcement |
| GR-8: Segment and separate | Hub-spoke network architecture |
| GR-9: Network security services | Azure Firewall, NSGs, Private Endpoints |
| GR-10: Cyber defense services | Defender for Cloud, Sentinel |
| GR-11: Logging and monitoring | Central Log Analytics, Sentinel |
| GR-12: Configuration of cloud marketplaces | Restricted marketplace access |

---

# 4. GOVERNANCE FRAMEWORK

## 4.1 Security Governance Structure

### 4.1.1 Organizational Authority

The [ORGANIZATION NAME] Security Authority is responsible for the overall security posture of the Azure Landing Zone Platform. The Security Authority SHALL:

a) Approve this Operational Security Standard and subsequent revisions;
b) Accept residual risk associated with platform operations;
c) Authorize client onboarding to the platform;
d) Review and approve security exceptions;
e) Commission periodic security assessments.

### 4.1.2 Platform Security Authority

The Platform Security Authority is delegated responsibility for:

a) Day-to-day security governance of the platform;
b) Security control implementation and monitoring;
c) Security incident management and response;
d) Continuous compliance monitoring;
e) Client security coordination.

### 4.1.3 Governance Bodies

The following governance bodies support platform security:

**Change Advisory Board (CAB)**
- Reviews and approves platform changes
- Assesses security impact of proposed changes
- Meets weekly or as required for emergency changes

**Security Working Group**
- Reviews security posture and metrics
- Addresses security findings and vulnerabilities
- Meets bi-weekly

**Platform Operations Review**
- Reviews operational metrics and incidents
- Addresses capacity and performance issues
- Meets weekly

## 4.2 Policy Framework

### 4.2.1 Policy Hierarchy

This standard operates within the following policy hierarchy:

1. Treasury Board policies and directives
2. Departmental security policy
3. This Operational Security Standard
4. Platform operational procedures
5. Client security requirements

In cases of conflict, higher-level policies SHALL take precedence.

### 4.2.2 Related Documentation

This standard is supported by:

- Platform Architecture Document
- Security Assessment Report
- Risk Register
- Incident Response Plan
- Business Continuity Plan
- Client Onboarding Guide

## 4.3 Compliance Requirements

### 4.3.1 Regulatory Compliance

The platform SHALL maintain compliance with:

- Privacy Act (Canada)
- Access to Information Act
- Canada Evidence Act
- Provincial privacy legislation as applicable

### 4.3.2 Contractual Compliance

The platform SHALL maintain compliance with:

- Microsoft Enterprise Agreement terms
- Client service agreements
- Third-party vendor agreements

### 4.3.3 Compliance Monitoring

Compliance SHALL be monitored through:

a) Automated policy compliance using Azure Policy;
b) Microsoft Defender for Cloud regulatory compliance dashboard;
c) Quarterly compliance reviews;
d) Annual security assessments.

---

# 5. SHARED RESPONSIBILITY MODEL

## 5.1 Overview

Cloud security operates under a shared responsibility model where security obligations are distributed among Microsoft Azure (cloud provider), the Platform Team, and Client Tenants. Clear delineation of responsibilities is essential for maintaining security posture and avoiding gaps in control implementation.

## 5.2 Microsoft Azure Responsibilities

Microsoft Azure is responsible for security OF the cloud:

### 5.2.1 Physical Security
- Data centre physical access controls
- Environmental controls (power, cooling, fire suppression)
- Physical media destruction
- Facility security monitoring

### 5.2.2 Infrastructure Security
- Hypervisor security and isolation
- Network infrastructure security
- Hardware security and maintenance
- Firmware and BIOS security

### 5.2.3 Platform Security
- Azure service security updates
- Azure platform availability
- Global network backbone security
- DDoS protection at the network edge

### 5.2.4 Compliance
- SOC 2 Type II attestation
- ISO 27001 certification
- CCCS cloud security assessment
- FedRAMP authorization (referenced)

## 5.3 Platform Team Responsibilities

The Platform Team is responsible for security IN the cloud at the platform layer:

### 5.3.1 Identity and Access
- Tenant configuration and security
- Privileged identity management
- Conditional access policies
- Authentication requirements
- Service principal management
- Break-glass account management

### 5.3.2 Network Security
- Hub virtual network architecture
- Azure Firewall configuration and rules
- DNS configuration
- Private endpoint infrastructure
- Network segmentation between clients
- VPN/ExpressRoute connectivity

### 5.3.3 Security Tooling
- Microsoft Defender for Cloud configuration
- Microsoft Sentinel deployment and rules
- Security alerting and response
- Vulnerability management for platform components
- Security baseline enforcement

### 5.3.4 Logging and Monitoring
- Central Log Analytics workspace
- Diagnostic settings for platform resources
- Log retention and archival
- Platform performance monitoring
- Security event monitoring

### 5.3.5 Governance
- Management group structure
- Azure Policy definitions and assignments
- Platform RBAC roles
- Subscription provisioning
- Resource naming and tagging standards
- Cost management at platform level

### 5.3.6 Operations
- Platform change management
- Platform incident response
- Platform backup and recovery
- Key Vault management for platform secrets
- Certificate management

## 5.4 Client Tenant Responsibilities

Client Tenants are responsible for security IN the cloud at the workload layer:

### 5.4.1 Application Security
- Application code security
- Application authentication and authorization
- Application-level encryption
- Application vulnerability management
- Application logging

### 5.4.2 Data Security
- Data classification
- Data encryption decisions beyond platform defaults
- Data access controls
- Data retention and disposal
- Data backup (beyond platform baseline)

### 5.4.3 Workload Security
- Virtual machine security and patching
- Container security
- Database security configuration
- Storage access controls
- Workload-specific network security groups

### 5.4.4 Identity
- Application service principals
- Managed identity usage
- Workload-specific RBAC
- Application user access management

### 5.4.5 Compliance
- Workload-specific compliance requirements
- Application security assessments
- Client-specific audit requirements
- Data handling procedures

## 5.5 Responsibility Matrix

| Control Domain | Microsoft | Platform | Client |
|---------------|-----------|----------|--------|
| Physical data centre security | ● | ○ | ○ |
| Hypervisor and hardware | ● | ○ | ○ |
| Network infrastructure | ● | ◐ | ○ |
| Tenant identity configuration | ○ | ● | ○ |
| Privileged access management | ○ | ● | ◐ |
| Hub network security | ○ | ● | ○ |
| Spoke network security | ○ | ◐ | ● |
| Platform security tooling | ○ | ● | ○ |
| Workload security tooling | ○ | ◐ | ● |
| Central logging infrastructure | ○ | ● | ○ |
| Workload logging | ○ | ○ | ● |
| Platform change management | ○ | ● | ○ |
| Workload change management | ○ | ○ | ● |
| Application security | ○ | ○ | ● |
| Data classification | ○ | ○ | ● |

**Legend:** ● Primary | ◐ Shared | ○ Not Responsible

## 5.6 Control Inheritance

Client workloads inherit certain security controls from the platform:

### 5.6.1 Inherited Controls (Full)
Controls fully inherited by client workloads:
- Physical security
- Tenant security configuration
- Network perimeter security
- Central logging infrastructure
- Security monitoring infrastructure
- Platform patch management

### 5.6.2 Inherited Controls (Partial)
Controls partially inherited, requiring client implementation:
- Network security (spoke-level NSGs required)
- Access management (workload RBAC required)
- Vulnerability management (workload patching required)
- Backup (workload-specific backup required)

### 5.6.3 Client-Implemented Controls
Controls requiring full client implementation:
- Application security
- Data encryption beyond defaults
- Workload-specific logging
- Application access controls

---

# 6. RISK MANAGEMENT FRAMEWORK

## 6.1 Risk Management Approach

The platform employs a continuous risk management approach aligned with ITSG-33 lifecycle methodology:

1. **Identify:** Identify threats, vulnerabilities, and security requirements
2. **Assess:** Assess risk likelihood and impact
3. **Mitigate:** Implement controls to reduce risk to acceptable levels
4. **Monitor:** Continuously monitor residual risk and control effectiveness
5. **Report:** Report risk status to governance bodies

## 6.2 Risk Assessment

### 6.2.1 Threat Assessment

The platform threat assessment considers:

a) **External Threats:**
   - Nation-state actors targeting government systems
   - Cybercriminal organizations
   - Hacktivists
   - Opportunistic attackers

b) **Internal Threats:**
   - Malicious insiders
   - Negligent users
   - Compromised credentials

c) **Environmental Threats:**
   - Cloud service disruptions
   - Regional outages
   - Supply chain compromise

### 6.2.2 Vulnerability Assessment

Vulnerability assessment is conducted through:

a) Automated vulnerability scanning (Microsoft Defender)
b) Configuration compliance scanning (Azure Policy)
c) Penetration testing (annual)
d) Security architecture reviews

### 6.2.3 Risk Calculation

Risk is calculated using the formula:

**Risk = Likelihood × Impact**

| Likelihood | Description |
|------------|-------------|
| 5 - Almost Certain | Expected to occur in most circumstances |
| 4 - Likely | Will probably occur in most circumstances |
| 3 - Possible | Might occur at some time |
| 2 - Unlikely | Could occur at some time |
| 1 - Rare | May occur only in exceptional circumstances |

| Impact | Description |
|--------|-------------|
| 5 - Severe | Critical damage to operations, significant data breach |
| 4 - Major | Major operational impact, significant security incident |
| 3 - Moderate | Moderate operational impact, contained security incident |
| 2 - Minor | Minor operational impact, limited security incident |
| 1 - Insignificant | Negligible impact |

## 6.3 Risk Treatment

### 6.3.1 Treatment Options

Identified risks SHALL be treated using one or more of the following options:

a) **Mitigate:** Implement controls to reduce risk likelihood or impact
b) **Transfer:** Transfer risk through insurance or contractual arrangements
c) **Accept:** Accept residual risk with documented approval
d) **Avoid:** Eliminate the risk source

### 6.3.2 Risk Acceptance

Risk acceptance requires:

a) Documentation in the risk register
b) Identification of risk owner
c) Approval at the appropriate authority level:
   - Low risk: Platform Security Authority
   - Medium risk: Security Authority
   - High/Critical risk: Executive authority

### 6.3.3 Risk Monitoring

Residual risk SHALL be monitored through:

a) Quarterly risk register reviews
b) Security metrics and KPIs
c) Incident trending
d) Vulnerability trending
e) Compliance status

## 6.4 Risk Register

The platform maintains a risk register documenting:

- Risk identifier
- Risk description
- Threat source
- Vulnerability
- Existing controls
- Likelihood and impact ratings
- Risk score
- Treatment decision
- Treatment plan
- Risk owner
- Review date

The risk register SHALL be reviewed quarterly and updated following significant changes or incidents.

---

# 7. IDENTITY AND ACCESS MANAGEMENT

## 7.1 Overview

Identity and Access Management (IAM) is foundational to platform security. The platform implements a comprehensive IAM framework using Microsoft Entra ID (formerly Azure Active Directory) with defense-in-depth controls.

**ITSG-33 Control Families:** AC (Access Control), IA (Identification and Authentication)

## 7.2 Identity Management

### 7.2.1 Identity Provider

Microsoft Entra ID SHALL be the authoritative identity provider for all platform access. All identities accessing platform resources SHALL be:

a) Provisioned through approved identity lifecycle processes;
b) Assigned to appropriate groups based on role requirements;
c) Subject to regular access reviews;
d) Disabled or removed upon role change or termination.

### 7.2.2 Identity Types

The platform supports the following identity types:

**User Identities**
- Platform administrators
- Security operations personnel
- Client tenant administrators
- Break-glass emergency accounts

**Service Identities**
- Managed identities (preferred)
- Service principals (when managed identity not available)
- Application registrations

### 7.2.3 Identity Lifecycle

**Provisioning**
User provisioning SHALL follow the principle of least privilege:
a) Access requests submitted through approved process
b) Manager approval required
c) Security review for privileged access
d) Just-in-time provisioning where possible

**Maintenance**
a) Quarterly access reviews for all privileged accounts
b) Annual access reviews for standard accounts
c) Role changes trigger access review
d) Inactive accounts disabled after 90 days

**Deprovisioning**
a) Immediate revocation upon termination
b) Access removal within 24 hours of role change
c) Service account decommissioning follows change process

### 7.2.4 Break-Glass Accounts

Emergency access accounts SHALL be maintained for scenarios where normal authentication is unavailable:

a) Minimum of two break-glass accounts
b) Cloud-only accounts (not federated)
c) Excluded from Conditional Access policies
d) Stored credentials secured in physical safe
e) Usage triggers immediate alert
f) Usage logged and reviewed
g) Credentials rotated after each use
h) Quarterly verification of account functionality

## 7.3 Authentication

### 7.3.1 Multi-Factor Authentication

Multi-Factor Authentication (MFA) SHALL be enforced for all interactive authentication:

a) All user accounts require MFA without exception
b) Phishing-resistant methods preferred (FIDO2, Windows Hello)
c) Microsoft Authenticator app as standard second factor
d) SMS and voice call prohibited for privileged accounts
e) Per-user MFA settings SHALL NOT be used (Conditional Access enforced)

### 7.3.2 Conditional Access

Conditional Access policies SHALL enforce authentication requirements based on context:

**Baseline Policies (All Users)**
- Require MFA for all cloud applications
- Block legacy authentication protocols
- Require compliant or Hybrid Azure AD joined device for portal access
- Block access from unauthorized locations

**Privileged Access Policies**
- Require phishing-resistant MFA for administrative portals
- Require compliant device
- Block access outside Canada
- Session lifetime maximum 4 hours
- Require re-authentication for sensitive actions

**Risk-Based Policies**
- Require MFA for medium sign-in risk
- Block high sign-in risk (require password reset)
- Block high user risk (require secure password reset)

### 7.3.3 Password Policy

For accounts using password authentication:

a) Minimum 14 characters
b) Complexity requirements enabled
c) Password expiration disabled (per NIST guidance) with breach detection
d) Banned password list enabled
e) Self-service password reset enabled with strong verification

### 7.3.4 Service Authentication

Service principals and managed identities SHALL:

a) Use certificate-based authentication or managed identity where possible
b) Rotate secrets every 90 days maximum if secret-based
c) Use federated credentials where supported
d) Not use long-lived secrets where alternatives exist

## 7.4 Authorization

### 7.4.1 Role-Based Access Control

Azure Role-Based Access Control (RBAC) SHALL be used for all authorization:

a) No direct user assignments (groups only)
b) Least privilege principle enforced
c) Custom roles minimized (prefer built-in roles)
d) Role assignments documented and justified

### 7.4.2 Privileged Identity Management

Azure AD Privileged Identity Management (PIM) SHALL be used for all privileged roles:

**Eligible Assignments**
- Privileged roles assigned as "eligible" not "active"
- Activation requires justification
- Activation requires MFA
- Activation duration limited (maximum 8 hours)

**Approval Workflows**
- Global Administrator requires approval
- Security Administrator requires approval
- Other privileged roles require justification

**Access Reviews**
- Monthly access reviews for Global Administrator
- Quarterly access reviews for other privileged roles
- Reviewers independent of role holders

### 7.4.3 Privileged Roles

The following roles are classified as privileged and require PIM:

**Tier 0 (Highest Privilege)**
- Global Administrator
- Privileged Role Administrator
- Security Administrator
- Exchange Administrator (if applicable)
- SharePoint Administrator (if applicable)

**Tier 1 (High Privilege)**
- User Administrator
- Application Administrator
- Cloud Application Administrator
- Authentication Administrator
- Groups Administrator
- Intune Administrator (if applicable)

**Tier 2 (Platform Privilege)**
- Subscription Owner
- Subscription Contributor (platform subscriptions)
- Key Vault Administrator
- Network Contributor (hub subscription)

### 7.4.4 Subscription Access

Subscription access SHALL follow these principles:

a) Management group level assignments for broad access
b) Subscription level assignments for specific access
c) Resource group assignments avoided except for client delegated access
d) Direct resource assignments prohibited

## 7.5 Access Control Procedures

### 7.5.1 Access Request Process

1. Requestor submits access request with business justification
2. Manager approves business need
3. Data/Resource owner approves access scope
4. Security reviews privileged access requests
5. Access provisioned via group membership
6. Requestor acknowledges access responsibility

### 7.5.2 Access Review Process

1. Reviewer receives access review notification
2. Reviewer validates continued business need
3. Reviewer approves or denies access
4. Denied access removed automatically
5. Non-response results in access removal
6. Completion reported to governance

### 7.5.3 Emergency Access Process

1. Emergency declared by authorized personnel
2. Break-glass credentials retrieved from secure storage
3. Break-glass usage logged with justification
4. Emergency work performed
5. Session terminated
6. Incident report filed
7. Credentials rotated
8. Usage reviewed by Security Authority

---

# 8. NETWORK SECURITY

## 8.1 Overview

Network security implements defense-in-depth principles through segmentation, controlled connectivity, and traffic inspection. The platform employs a hub-and-spoke architecture with centralized security services.

**ITSG-33 Control Families:** SC (System and Communications Protection)

## 8.2 Network Architecture

### 8.2.1 Hub-and-Spoke Model

The platform implements a hub-and-spoke network topology:

**Hub Virtual Network**
- Centralized connectivity and security services
- Azure Firewall for traffic inspection
- VPN/ExpressRoute gateway for hybrid connectivity
- Azure Bastion for secure administrative access
- DNS infrastructure
- Shared services subnet

**Spoke Virtual Networks**
- Client workload hosting
- Peered to hub for connectivity
- Isolated from other spokes
- Subject to hub firewall policies

### 8.2.2 Network Segmentation

Network segmentation SHALL be implemented through:

a) Separate virtual networks per client (spoke isolation)
b) Subnets within spokes for workload tiers
c) Network Security Groups (NSGs) on all subnets
d) Azure Firewall for inter-spoke and egress traffic
e) Private endpoints for PaaS services

### 8.2.3 IP Address Management

IP addressing SHALL be centrally managed:

a) Documented IP address plan
b) Non-overlapping address spaces
c) Reserved ranges for future growth
d) Platform team controls all address assignments

## 8.3 Traffic Flow Control

### 8.3.1 Ingress Traffic

Inbound traffic from the internet SHALL:

a) Pass through Azure Firewall or approved WAF
b) Be limited to explicitly approved flows
c) Be logged and monitored
d) Use TLS 1.2 or higher for encrypted services

### 8.3.2 Egress Traffic

Outbound traffic to the internet SHALL:

a) Route through Azure Firewall
b) Be filtered by application rules
c) Use FQDN-based allow lists (no wildcard destinations)
d) Be logged for security analysis
e) Block known malicious destinations (Threat Intelligence)

### 8.3.3 East-West Traffic

Traffic between spokes SHALL:

a) Route through Azure Firewall
b) Be explicitly allowed by firewall rules
c) Default deny between client spokes
d) Logged for security analysis

### 8.3.4 Management Traffic

Administrative traffic SHALL:

a) Use Azure Bastion for VM access (no public IPs on VMs)
b) Use Private Endpoints for PaaS management
c) Use dedicated management subnet where required
d) Be logged and monitored

## 8.4 Azure Firewall

### 8.4.1 Firewall Configuration

Azure Firewall SHALL be deployed with:

a) Premium SKU for TLS inspection and IDPS
b) Firewall Policy for centralized rule management
c) Threat Intelligence enabled in Alert and Deny mode
d) IDPS in Alert and Deny mode
e) DNS Proxy enabled

### 8.4.2 Rule Hierarchy

Firewall rules SHALL be organized:

1. **Platform rules:** Infrastructure requirements
2. **Security rules:** Threat blocking, deny lists
3. **Client rules:** Client-specific application rules
4. **Default deny:** Implicit deny for unmatched traffic

### 8.4.3 Rule Management

Firewall rule changes SHALL:

a) Follow the change management process
b) Include security review for new allow rules
c) Document business justification
d) Use least-privilege scoping
e) Include expiration for temporary rules

## 8.5 Network Security Groups

### 8.5.1 NSG Requirements

Network Security Groups SHALL be applied to all subnets:

a) Default deny inbound from internet
b) Explicit allow rules for required traffic
c) NSG flow logs enabled
d) Rules documented and justified

### 8.5.2 NSG Best Practices

a) Use service tags instead of IP addresses where possible
b) Use Application Security Groups for workload grouping
c) Avoid overly permissive rules (no 0.0.0.0/0 sources)
d) Regular review of NSG rules

## 8.6 Private Connectivity

### 8.6.1 Private Endpoints

Private Endpoints SHALL be used for PaaS services:

a) Storage accounts
b) Key Vault
c) Azure SQL Database
d) Azure Container Registry
e) Other supported PaaS services

Public access SHALL be disabled where Private Endpoints are implemented.

### 8.6.2 Hybrid Connectivity

Connectivity to on-premises networks SHALL:

a) Use ExpressRoute (preferred) or VPN Gateway
b) Encrypt traffic in transit
c) Be documented in network architecture
d) Follow least-privilege connectivity principles

### 8.6.3 DNS Configuration

DNS SHALL be configured to support Private Endpoints:

a) Private DNS zones for Azure services
b) DNS forwarding to on-premises where required
c) Azure Firewall DNS proxy for spoke DNS resolution
d) Centrally managed DNS infrastructure

## 8.7 Network Monitoring

### 8.7.1 Flow Logging

Network flow logs SHALL be collected:

a) NSG flow logs enabled on all NSGs
b) Flow logs sent to Log Analytics
c) Traffic Analytics enabled
d) Retention minimum 90 days

### 8.7.2 Firewall Logging

Azure Firewall logs SHALL include:

a) Application rule logs
b) Network rule logs
c) Threat Intelligence logs
d) IDPS logs
e) DNS proxy logs

### 8.7.3 Network Monitoring

Network monitoring SHALL include:

a) Connection Monitor for connectivity testing
b) Network Performance Monitor where applicable
c) Alerting on firewall denies and threat detections
d) Regular traffic pattern analysis

---

# 9. SYSTEM AND COMMUNICATIONS PROTECTION

## 9.1 Overview

System and communications protection ensures the confidentiality and integrity of information in transit and at rest through encryption and secure configuration.

**ITSG-33 Control Families:** SC (System and Communications Protection)

## 9.2 Encryption at Rest

### 9.2.1 Storage Encryption

All data at rest SHALL be encrypted:

a) Azure Storage Service Encryption (SSE) enabled
b) Managed disks encrypted by default
c) SQL Database Transparent Data Encryption (TDE) enabled
d) Backup data encrypted

### 9.2.2 Key Management

Encryption keys SHALL be managed according to data sensitivity:

**Platform-Managed Keys (Default)**
- Microsoft manages encryption keys
- Acceptable for most workloads
- No customer key management overhead

**Customer-Managed Keys (Where Required)**
- Customer controls keys in Azure Key Vault
- Required for specific compliance requirements
- Key rotation policies enforced

### 9.2.3 Key Vault

Azure Key Vault SHALL be used for secrets management:

a) Dedicated Key Vault per security boundary
b) Access policies or RBAC for authorization
c) Soft delete and purge protection enabled
d) Private Endpoint for network access
e) Diagnostic logging enabled

## 9.3 Encryption in Transit

### 9.3.1 Transport Layer Security

TLS SHALL be enforced for all data in transit:

a) Minimum TLS version 1.2
b) TLS 1.0 and 1.1 disabled
c) Strong cipher suites only
d) Certificate validation enforced

### 9.3.2 Internal Traffic

Traffic within the platform SHALL:

a) Use TLS for service-to-service communication
b) Use TLS for database connections
c) Use TLS for storage access
d) Use IPsec for VPN tunnels

### 9.3.3 External Traffic

Traffic to/from external parties SHALL:

a) Use TLS 1.2 or higher
b) Use certificates from trusted CAs
c) Implement certificate monitoring for expiration

## 9.4 Secure Configuration

### 9.4.1 Security Baselines

Platform resources SHALL meet security baselines:

a) Microsoft Cloud Security Benchmark as baseline
b) CIS Azure Foundations Benchmark recommendations
c) Azure Policy for compliance enforcement
d) Regular baseline compliance assessment

### 9.4.2 Resource Configuration

Default secure configuration SHALL include:

**Virtual Machines**
- Encrypted disks
- No public IP addresses
- NSG on subnet
- Defender for Servers enabled
- Automatic updates enabled

**Storage Accounts**
- HTTPS only
- Minimum TLS 1.2
- Private endpoint
- Soft delete enabled
- Blob versioning enabled

**Azure SQL**
- TDE enabled
- Minimum TLS 1.2
- Private endpoint
- Auditing enabled
- Defender for SQL enabled

**Key Vault**
- Soft delete enabled
- Purge protection enabled
- Private endpoint
- Diagnostic logging enabled

---

# 10. CONFIGURATION MANAGEMENT

## 10.1 Overview

Configuration management ensures consistent, secure, and documented platform configuration through Infrastructure as Code and automated compliance.

**ITSG-33 Control Families:** CM (Configuration Management)

## 10.2 Baseline Configuration

### 10.2.1 Configuration Standards

Platform configuration standards SHALL be documented for:

a) Management group structure
b) Subscription configuration
c) Network architecture
d) Security tool configuration
e) Logging configuration
f) Identity configuration

### 10.2.2 Configuration Baseline

The configuration baseline SHALL:

a) Be version controlled in Git repository
b) Represent the approved secure state
c) Be the source of truth for deployments
d) Include all infrastructure configuration

## 10.3 Infrastructure as Code

### 10.3.1 IaC Requirements

All platform infrastructure SHALL be deployed using Infrastructure as Code:

a) Terraform or Bicep as approved IaC tools
b) No manual portal deployments for platform resources
c) All configuration changes through code
d) Code review required before merge

### 10.3.2 Code Repository

IaC code SHALL be managed in approved repositories:

a) Azure DevOps or GitHub repository
b) Branch protection enabled
c) Pull request required for changes
d) Review and approval required
e) CI/CD integration for deployment

### 10.3.3 Module Standards

IaC modules SHALL follow standards:

a) Documented inputs and outputs
b) Security defaults configured
c) Tagging requirements enforced
d) Naming conventions enforced
e) Version controlled

## 10.4 Azure Policy

### 10.4.1 Policy Framework

Azure Policy SHALL enforce configuration compliance:

a) Policies assigned at management group level
b) Inherited by subscriptions and resources
c) Audit and Deny effects used appropriately
d) Exemptions documented and time-limited

### 10.4.2 Policy Categories

Policies SHALL cover:

**Security Policies**
- Encryption requirements
- Network security requirements
- Identity requirements
- Logging requirements

**Governance Policies**
- Allowed regions (Canada only)
- Allowed resource types
- Naming conventions
- Tagging requirements

**Cost Policies**
- SKU restrictions
- Reserved instance enforcement
- Budget alerts

### 10.4.3 Policy Compliance

Policy compliance SHALL be monitored:

a) Defender for Cloud compliance dashboard
b) Regular compliance reporting
c) Non-compliance remediation process
d) Exemption review process

## 10.5 Change Control

### 10.5.1 Configuration Change Process

Configuration changes SHALL follow the change management process (Section 11):

a) Change request submitted
b) Impact assessment performed
c) Security review for security-relevant changes
d) Approval obtained
e) Change implemented via IaC
f) Verification performed
g) Change documented

### 10.5.2 Drift Detection

Configuration drift SHALL be detected and remediated:

a) Terraform state monitoring
b) Azure Policy compliance monitoring
c) Regular configuration audits
d) Automated drift alerts
e) Drift remediation procedures

---

# 11. CHANGE MANAGEMENT

## 11.1 Overview

Change management ensures controlled, documented, and reversible changes to the platform while maintaining security and availability.

**ITSG-33 Control Families:** CM (Configuration Management)

## 11.2 Change Categories

### 11.2.1 Standard Changes

Pre-approved, low-risk, routine changes:
- Client spoke provisioning (using approved template)
- Firewall rule additions (within approved scope)
- User access provisioning
- Routine maintenance activities

Standard changes require documented procedure but not CAB approval.

### 11.2.2 Normal Changes

Changes requiring assessment and approval:
- New platform capability deployment
- Network architecture changes
- Security configuration changes
- New integration deployments
- Policy changes

Normal changes require impact assessment, security review, and CAB approval.

### 11.2.3 Emergency Changes

Urgent changes required to restore service or address security incidents:
- Security vulnerability remediation
- Incident response actions
- Critical service restoration

Emergency changes may bypass normal approval with retrospective review.

## 11.3 Change Process

### 11.3.1 Request

1. Change requestor creates change request
2. Request includes:
   - Description of change
   - Business justification
   - Technical implementation plan
   - Impact assessment
   - Rollback plan
   - Testing plan
   - Implementation schedule

### 11.3.2 Assessment

1. Technical review of implementation plan
2. Security review for security-relevant changes
3. Impact assessment on platform and clients
4. Risk assessment
5. Rollback plan validation

### 11.3.3 Approval

**Standard Changes**
- Pre-approved by category
- Implementation team executes

**Normal Changes**
- Change Advisory Board review
- Security Authority approval for security changes
- Scheduled implementation window

**Emergency Changes**
- Platform Manager verbal approval
- CAB retrospective review

### 11.3.4 Implementation

1. Pre-implementation verification
2. Implementation per approved plan
3. Progress monitoring
4. Issue escalation if required
5. Rollback if success criteria not met

### 11.3.5 Verification

1. Functional testing
2. Security verification
3. Performance verification
4. Client impact verification
5. Documentation update

### 11.3.6 Closure

1. Change record updated
2. Lessons learned documented
3. Configuration baseline updated
4. Stakeholders notified

## 11.4 CI/CD Pipeline

### 11.4.1 Pipeline Structure

Platform deployments SHALL use CI/CD pipelines:

**Continuous Integration**
- Code commit triggers build
- Automated linting and validation
- Security scanning (credentials, vulnerabilities)
- Terraform plan generation
- Plan review and approval gate

**Continuous Deployment**
- Approved changes deployed automatically
- Staged deployment (dev → staging → prod)
- Automated smoke tests
- Automatic rollback on failure

### 11.4.2 Pipeline Security

CI/CD pipelines SHALL implement:

a) Service principal with least privilege
b) Secrets stored in Key Vault or pipeline secrets
c) Approval gates for production deployments
d) Audit logging of pipeline executions
e) No hardcoded credentials in code

### 11.4.3 Deployment Windows

Platform changes SHALL be deployed during approved windows:

- **Standard Window:** Tuesday-Thursday, 06:00-08:00 ET
- **Emergency Window:** As required with approval
- **Freeze Periods:** Announced in advance for critical business periods

---

# 12. AUDIT AND ACCOUNTABILITY

## 12.1 Overview

Audit and accountability ensures comprehensive logging, monitoring, and retention of security-relevant events for detection, investigation, and compliance.

**ITSG-33 Control Families:** AU (Audit and Accountability)

## 12.2 Logging Architecture

### 12.2.1 Central Log Analytics

All platform logs SHALL be collected in central Log Analytics workspace:

a) Platform subscription hosts Log Analytics
b) All platform resources send diagnostics
c) Client spokes send diagnostics
d) Retention configured per requirements
e) Access controlled via RBAC

### 12.2.2 Log Sources

The following log sources SHALL be collected:

**Azure Activity Logs**
- Control plane operations
- Administrative actions
- Service health events

**Azure AD Sign-in Logs**
- User authentication events
- Conditional access results
- MFA events

**Azure AD Audit Logs**
- Directory changes
- Application changes
- Group membership changes

**Resource Diagnostic Logs**
- Azure Firewall logs
- Key Vault access logs
- Storage access logs
- Virtual machine logs
- Network flow logs

**Security Logs**
- Defender for Cloud alerts
- Sentinel incidents
- Vulnerability findings

### 12.2.3 Log Format

Logs SHALL include:

a) Timestamp (UTC)
b) Event type
c) Actor identity
d) Source IP address
e) Resource affected
f) Action performed
g) Result (success/failure)

## 12.3 Microsoft Sentinel

### 12.3.1 SIEM Implementation

Microsoft Sentinel SHALL be deployed for security monitoring:

a) Connected to Log Analytics workspace
b) Data connectors enabled for all relevant sources
c) Analytics rules for threat detection
d) Automated response playbooks
e) Incident management workflow

### 12.3.2 Detection Rules

Sentinel SHALL include detection rules for:

**Identity Threats**
- Brute force attempts
- Suspicious sign-in locations
- Impossible travel
- Privileged account usage
- Service principal abuse

**Network Threats**
- Firewall deny patterns
- Command and control traffic
- Data exfiltration indicators
- Lateral movement

**Resource Threats**
- Unauthorized resource creation
- Configuration changes
- Encryption key access
- Backup deletion

### 12.3.3 Incident Management

Sentinel incidents SHALL be managed:

a) Incident assignment within 15 minutes
b) Initial triage within 1 hour
c) Investigation procedures followed
d) Escalation per incident severity
e) Incident documentation maintained

## 12.4 Log Retention

### 12.4.1 Retention Requirements

Log retention SHALL meet the following minimums:

| Log Type | Online Retention | Archive Retention |
|----------|-----------------|-------------------|
| Security logs | 365 days | 7 years |
| Activity logs | 365 days | 7 years |
| Authentication logs | 365 days | 7 years |
| Firewall logs | 90 days | 1 year |
| Resource diagnostics | 90 days | 1 year |

### 12.4.2 Log Archive

Logs beyond online retention SHALL be:

a) Exported to secure storage
b) Encrypted at rest
c) Access controlled
d) Integrity protected
e) Retrievable for investigation

## 12.5 Monitoring and Alerting

### 12.5.1 Alert Categories

Alerts SHALL be configured for:

**Critical (Immediate Response)**
- Security incident detected
- Authentication service degraded
- Firewall failure
- Break-glass account usage

**High (Response within 1 hour)**
- Multiple authentication failures
- Privileged role activation
- Security policy violation
- Configuration drift detected

**Medium (Response within 4 hours)**
- Vulnerability detected
- Compliance deviation
- Capacity threshold exceeded

**Low (Response within 24 hours)**
- Informational security events
- Operational warnings

### 12.5.2 Alert Notification

Alerts SHALL be routed to:

a) Security Operations Centre (all security alerts)
b) Platform Operations (operational alerts)
c) On-call personnel (critical alerts)
d) Management (critical security incidents)

---

# 13. INCIDENT RESPONSE

## 13.1 Overview

Incident response provides structured procedures for detecting, responding to, containing, and recovering from security incidents affecting the platform.

**ITSG-33 Control Families:** IR (Incident Response)

## 13.2 Incident Classification

### 13.2.1 Severity Levels

| Severity | Description | Response Time | Examples |
|----------|-------------|---------------|----------|
| Critical | Active breach, significant data exposure, platform compromise | Immediate | Confirmed data breach, ransomware, platform admin account compromise |
| High | Likely breach, significant vulnerability, major service impact | 1 hour | Successful privilege escalation, zero-day vulnerability, authentication bypass |
| Medium | Potential security issue, contained incident | 4 hours | Phishing success (contained), policy violation, failed attack attempts |
| Low | Minor security event, informational | 24 hours | Vulnerability disclosure, suspicious activity (unconfirmed) |

### 13.2.2 Incident Categories

- **Unauthorized Access:** Successful or attempted unauthorized access
- **Malware:** Malicious software detection
- **Data Breach:** Confirmed or suspected data exposure
- **Denial of Service:** Service disruption attacks
- **Configuration Incident:** Security misconfiguration discovered
- **Policy Violation:** Violation of security policies

## 13.3 Incident Response Phases

### 13.3.1 Detection

Incidents may be detected through:

a) Microsoft Sentinel alerts
b) Defender for Cloud alerts
c) User reports
d) Third-party notifications
e) Threat intelligence
f) Automated monitoring

### 13.3.2 Triage

Upon detection:

1. Validate the incident (true positive confirmation)
2. Classify severity and category
3. Assign incident owner
4. Notify relevant parties
5. Begin documentation

### 13.3.3 Containment

Containment actions based on incident type:

**Account Compromise**
- Disable affected accounts
- Revoke active sessions
- Reset credentials
- Review account activity

**Network Incident**
- Isolate affected resources
- Block malicious IPs/domains
- Capture network traffic for analysis

**Malware**
- Isolate affected systems
- Preserve evidence
- Block indicators of compromise

**Data Breach**
- Identify data affected
- Preserve access logs
- Assess exposure scope

### 13.3.4 Eradication

Remove the threat:

a) Remove malicious artifacts
b) Close vulnerability exploited
c) Patch affected systems
d) Strengthen controls

### 13.3.5 Recovery

Restore normal operations:

a) Restore from clean backups if required
b) Verify system integrity
c) Monitor for recurrence
d) Gradual service restoration

### 13.3.6 Post-Incident

After incident closure:

a) Complete incident documentation
b) Conduct lessons learned review
c) Update procedures as needed
d) Implement additional controls
e) Report to governance bodies

## 13.4 Incident Response Team

### 13.4.1 Team Structure

| Role | Responsibilities |
|------|-----------------|
| Incident Commander | Overall incident coordination |
| Security Analyst | Technical investigation |
| Platform Engineer | Platform remediation actions |
| Communications Lead | Stakeholder communication |
| Legal/Privacy (as needed) | Legal and privacy guidance |

### 13.4.2 Escalation

| Severity | Notification |
|----------|-------------|
| Critical | Executive, Legal, Client (if affected), CCCS (if required) |
| High | Security Authority, Platform Manager |
| Medium | Security Operations Manager |
| Low | Security Analyst team |

## 13.5 Communication

### 13.5.1 Internal Communication

a) Secure communication channels (Teams, encrypted email)
b) Status updates at defined intervals
c) Need-to-know information sharing

### 13.5.2 External Communication

a) Client notification per agreed procedures
b) Regulatory notification as required
c) Public communication through approved channels only
d) No social media discussion of incidents

### 13.5.3 Reporting Requirements

Incidents involving Protected B data SHALL be reported to:

a) Organizational Security Authority
b) Privacy Officer (if personal information involved)
c) CCCS (significant cyber incidents)
d) Affected clients

---

# 14. CONTINGENCY PLANNING

## 14.1 Overview

Contingency planning ensures platform resilience and recovery capability through backup, disaster recovery, and business continuity procedures.

**ITSG-33 Control Families:** CP (Contingency Planning)

## 14.2 Recovery Objectives

### 14.2.1 Platform Recovery Objectives

| Component | RTO | RPO |
|-----------|-----|-----|
| Identity Services | 1 hour | 0 (no data loss) |
| Network Connectivity | 2 hours | N/A |
| Security Monitoring | 4 hours | 1 hour |
| Management Services | 4 hours | 24 hours |
| Platform Configuration | 4 hours | 24 hours |

### 14.2.2 Client Recovery Objectives

Client workload recovery objectives are defined per client service agreement. Platform provides infrastructure capability; client responsible for workload recovery.

## 14.3 Backup

### 14.3.1 Backup Scope

Platform backups SHALL include:

a) **Configuration Backups**
   - IaC repository (Git)
   - Azure Policy definitions
   - RBAC assignments
   - Firewall rules
   - Diagnostic settings

b) **Data Backups**
   - Key Vault (keys and secrets)
   - Log Analytics data (via export)
   - Azure AD configuration

c) **Client Responsibility**
   - Virtual machine backups
   - Database backups
   - Application data

### 14.3.2 Backup Procedures

**IaC Repository**
- Replicated to secondary location
- Point-in-time recovery available
- 90-day history minimum

**Key Vault**
- Soft delete enabled (90 days)
- Purge protection enabled
- Key export for critical keys

**Azure AD**
- Microsoft-managed replication
- Soft delete for users (30 days)
- Configuration documented for recreation

### 14.3.3 Backup Verification

Backup verification SHALL be performed:

a) Monthly verification of backup completeness
b) Quarterly test restore of critical components
c) Annual full recovery test

## 14.4 Disaster Recovery

### 14.4.1 DR Strategy

The platform employs the following DR strategies:

**Active-Passive**
- Primary: Canada Central
- Secondary: Canada East
- Manual failover for platform services

**Configuration Recovery**
- IaC enables rapid rebuild
- Documented recovery procedures
- Tested recovery runbooks

### 14.4.2 Failover Procedures

Failover SHALL be initiated when:

a) Regional Azure outage declared
b) Recovery time exceeds acceptable threshold
c) Security incident requires isolation

Failover procedures:

1. Incident Commander declares DR event
2. Assessment of current state
3. Decision to failover
4. Execute failover runbook
5. Verify platform functionality
6. Notify clients
7. Monitor secondary region

### 14.4.3 Failback Procedures

Failback to primary region:

1. Primary region restored and verified
2. Data synchronization verified
3. Failback window scheduled
4. Execute failback runbook
5. Verify platform functionality
6. Notify clients

## 14.5 Business Continuity

### 14.5.1 Continuity Scenarios

The following scenarios are addressed:

a) Regional Azure outage
b) Key personnel unavailability
c) Security incident requiring isolation
d) Vendor service disruption

### 14.5.2 Personnel Continuity

Platform operations continuity:

a) Cross-training of personnel
b) Documented procedures
c) On-call rotation
d) Vendor support contracts

### 14.5.3 Testing

Continuity testing SHALL include:

a) Annual tabletop exercise
b) Annual failover test
c) Quarterly backup verification
d) Lessons learned documentation

---

# 15. VULNERABILITY MANAGEMENT

## 15.1 Overview

Vulnerability management provides systematic identification, assessment, and remediation of security vulnerabilities in platform components.

**ITSG-33 Control Families:** RA (Risk Assessment), SI (System Integrity)

## 15.2 Vulnerability Identification

### 15.2.1 Scanning

Vulnerability scanning SHALL be performed:

**Microsoft Defender for Cloud**
- Continuous assessment of Azure resources
- Configuration compliance scanning
- Agentless scanning where supported

**Microsoft Defender for Servers**
- Agent-based vulnerability scanning
- Operating system vulnerabilities
- Installed software vulnerabilities

**Microsoft Defender Vulnerability Management**
- Software inventory
- Vulnerability prioritization
- Remediation tracking

### 15.2.2 Threat Intelligence

Threat intelligence sources SHALL include:

a) Microsoft Threat Intelligence
b) CCCS alerts and advisories
c) Vendor security bulletins
d) CVE databases

## 15.3 Vulnerability Assessment

### 15.3.1 Severity Rating

Vulnerabilities SHALL be rated using CVSS v3 scores:

| CVSS Score | Severity | Remediation Timeline |
|------------|----------|---------------------|
| 9.0-10.0 | Critical | 72 hours |
| 7.0-8.9 | High | 7 days |
| 4.0-6.9 | Medium | 30 days |
| 0.1-3.9 | Low | 90 days |

### 15.3.2 Risk Assessment

Vulnerability risk assessment SHALL consider:

a) CVSS score
b) Exploitability (public exploit available?)
c) Asset criticality
d) Exposure (internet-facing?)
e) Compensating controls

## 15.4 Remediation

### 15.4.1 Remediation Process

1. Vulnerability identified and assessed
2. Risk rating assigned
3. Remediation owner assigned
4. Remediation planned
5. Change request submitted
6. Remediation implemented
7. Verification performed
8. Vulnerability closed

### 15.4.2 Remediation Methods

**Patching**
- Operating system patches
- Application patches
- Firmware updates

**Configuration**
- Security hardening
- Disable vulnerable features
- Network isolation

**Compensating Controls**
- WAF rules
- Firewall rules
- Enhanced monitoring

### 15.4.3 Exceptions

Vulnerability remediation exceptions:

a) Must be documented with business justification
b) Compensating controls documented
c) Exception expiration date set
d) Security Authority approval required
e) Regular review of exceptions

## 15.5 Patch Management

### 15.5.1 Patch Sources

Platform components patched through:

**Azure PaaS**
- Microsoft-managed patching
- Platform team monitors announcements

**Platform VMs**
- Azure Update Management
- Automated patching enabled
- Maintenance windows defined

**Client Workloads**
- Client responsibility
- Platform provides Update Management capability

### 15.5.2 Patch Schedule

| Patch Category | Schedule |
|----------------|----------|
| Critical security | Within 72 hours |
| High security | Within 7 days |
| Other security | Monthly maintenance window |
| Feature updates | Quarterly (tested first) |

### 15.5.3 Patch Testing

Patches SHALL be tested:

a) Non-production environment first
b) Automated testing where possible
c) Staged rollout to production
d) Rollback capability verified

---

# 16. DATA PROTECTION

## 16.1 Overview

Data protection ensures appropriate handling, protection, and lifecycle management of data within the platform.

**ITSG-33 Control Families:** MP (Media Protection), SC (System and Communications Protection)

## 16.2 Data Classification

### 16.2.1 Classification Levels

The platform supports data classified up to Protected B:

| Classification | Description |
|---------------|-------------|
| Protected B | Information where compromise could cause serious injury |
| Protected A | Information where compromise could cause injury |
| Unclassified | Information approved for public release |

### 16.2.2 Classification Responsibility

Data classification is the responsibility of the data owner (client). The platform provides controls appropriate for Protected B.

## 16.3 Data Handling

### 16.3.1 Data at Rest

Protected B data at rest SHALL be:

a) Encrypted using AES-256 or equivalent
b) Stored only in Canadian regions
c) Access controlled via RBAC
d) Backed up per retention requirements

### 16.3.2 Data in Transit

Protected B data in transit SHALL be:

a) Encrypted using TLS 1.2 or higher
b) Not transmitted over untrusted networks without encryption
c) Not transmitted outside Canada without authorization

### 16.3.3 Data in Use

Protected B data in use SHALL be:

a) Accessed only by authorized personnel
b) Protected from unauthorized viewing
c) Not copied to unauthorized locations

## 16.4 Data Residency

### 16.4.1 Geographic Restrictions

All platform data SHALL reside in Canada:

a) Azure regions: Canada Central, Canada East only
b) No replication to non-Canadian regions
c) Azure Policy enforces region restriction
d) Client data remains in Canada

### 16.4.2 Data Sovereignty

Data remains under Canadian jurisdiction:

a) Microsoft Canada data centre operations
b) Canadian law applies
c) Subject to lawful Canadian court orders only

## 16.5 Data Lifecycle

### 16.5.1 Retention

Data retention SHALL comply with:

a) Applicable retention schedules
b) Legal hold requirements
c) Minimum retention for compliance (varies by data type)
d) Maximum retention to limit exposure

### 16.5.2 Disposal

Data disposal SHALL ensure:

a) Secure deletion using Azure capabilities
b) Soft delete period before permanent deletion
c) Disposal approval documented
d) Disposal verification

### 16.5.3 Media Sanitization

For physical media (if applicable):

a) Microsoft responsible for data centre media
b) Client responsible for any physical media
c) Sanitization meets CCCS standards

---

# 17. CONTINUOUS MONITORING

## 17.1 Overview

Continuous monitoring maintains ongoing awareness of security posture, threats, and vulnerabilities through automated and manual assessment.

**ITSG-33 Control Families:** CA (Security Assessment), PM (Program Management)

## 17.2 Monitoring Strategy

### 17.2.1 Objectives

Continuous monitoring SHALL:

a) Maintain awareness of security posture
b) Detect security events and incidents
c) Identify configuration drift
d) Track vulnerability status
e) Verify control effectiveness

### 17.2.2 Monitoring Domains

| Domain | Tools | Frequency |
|--------|-------|-----------|
| Security posture | Defender for Cloud | Continuous |
| Threat detection | Microsoft Sentinel | Continuous |
| Compliance | Azure Policy | Continuous |
| Vulnerability | Defender Vulnerability Management | Daily |
| Configuration | Terraform state | Continuous |
| Access | Azure AD logs | Continuous |

## 17.3 Security Posture Management

### 17.3.1 Defender for Cloud

Microsoft Defender for Cloud SHALL:

a) Be enabled on all subscriptions
b) Enhanced security features enabled
c) Secure score monitored
d) Recommendations reviewed weekly
e) Regulatory compliance tracked

### 17.3.2 Secure Score

Platform SHALL maintain minimum secure score:

a) Target: 80% or higher
b) Weekly review of score changes
c) Action plan for score improvement
d) Score reported to governance

### 17.3.3 Compliance Dashboard

Regulatory compliance SHALL be tracked:

a) CCCS PBMM controls mapped
b) Compliance status monitored
c) Non-compliance investigated
d) Exemptions documented

## 17.4 Threat Detection

### 17.4.1 Detection Capabilities

Threat detection SHALL include:

a) Identity threat detection (Azure AD Identity Protection)
b) Network threat detection (Azure Firewall, Sentinel)
c) Endpoint threat detection (Defender for Endpoint)
d) Cloud workload threat detection (Defender for Cloud)

### 17.4.2 Alert Management

Security alerts SHALL be:

a) Triaged within SLA
b) Investigated using documented procedures
c) Escalated per severity
d) Documented in incident tracking

## 17.5 Metrics and Reporting

### 17.5.1 Security Metrics

The following metrics SHALL be tracked:

| Metric | Target | Frequency |
|--------|--------|-----------|
| Secure score | ≥80% | Weekly |
| Critical vulnerabilities | 0 open >72hr | Daily |
| High vulnerabilities | 0 open >7 days | Weekly |
| MFA coverage | 100% | Monthly |
| Privileged access reviews | 100% complete | Monthly |
| Security incidents | Trending down | Monthly |
| Mean time to detect | <1 hour | Monthly |
| Mean time to respond | <4 hours | Monthly |

### 17.5.2 Reporting

Security reports SHALL be produced:

**Weekly**
- Security operations summary
- Alert and incident summary
- Vulnerability status

**Monthly**
- Security posture report
- Compliance status
- Metrics dashboard
- Risk register update

**Quarterly**
- Executive security report
- Trend analysis
- Control effectiveness assessment

**Annual**
- Security program review
- Risk assessment update
- Policy and procedure review

---

# 18. PLATFORM OPERATIONS

## 18.1 Overview

Platform operations defines day-to-day operational procedures for maintaining the secure and reliable operation of the Azure Landing Zone Platform.

## 18.2 Operational Procedures

### 18.2.1 Daily Operations

**Security Operations**
- Review Sentinel incidents
- Review Defender for Cloud alerts
- Review authentication anomalies
- Process access requests

**Platform Operations**
- Review platform health
- Review capacity metrics
- Process change requests
- Address operational issues

### 18.2.2 Weekly Operations

- Review security posture score
- Review vulnerability status
- Review policy compliance
- Conduct CAB meeting
- Review open incidents

### 18.2.3 Monthly Operations

- Access reviews for privileged roles
- Security metrics reporting
- Capacity planning review
- Procedure review and updates

### 18.2.4 Quarterly Operations

- Risk register review
- Compliance assessment
- Tabletop exercises
- Training and awareness

### 18.2.5 Annual Operations

- Policy and procedure review
- Security assessment
- Disaster recovery test
- Business continuity review

## 18.3 Maintenance

### 18.3.1 Maintenance Windows

Scheduled maintenance:

- **Standard:** Tuesday-Thursday, 06:00-08:00 ET
- **Extended:** First Saturday monthly, 02:00-06:00 ET
- **Emergency:** As required with notification

### 18.3.2 Maintenance Activities

Maintenance activities include:

a) Security patching
b) Configuration updates
c) Capacity adjustments
d) Certificate renewals
e) Key rotations

### 18.3.3 Maintenance Communication

Maintenance SHALL be communicated:

a) Planned: 5 business days notice
b) Emergency: As soon as possible
c) Post-maintenance: Completion notification

## 18.4 Capacity Management

### 18.4.1 Capacity Monitoring

Platform capacity SHALL be monitored:

a) Azure Monitor metrics
b) Log Analytics workspace capacity
c) Network bandwidth utilization
d) Key Vault transaction limits

### 18.4.2 Capacity Planning

Capacity planning SHALL include:

a) Monthly capacity review
b) Client onboarding impact assessment
c) Growth projections
d) Budget alignment

---

# 19. CLIENT ONBOARDING SECURITY

## 19.1 Overview

Client onboarding security ensures consistent security posture for new client workloads deployed to the platform.

## 19.2 Onboarding Process

### 19.2.1 Security Requirements

Prior to onboarding, clients SHALL:

a) Complete security requirements questionnaire
b) Identify data classification requirements
c) Identify compliance requirements
d) Designate security contact
e) Acknowledge shared responsibility model

### 19.2.2 Security Assessment

Platform team SHALL assess:

a) Client workload security requirements
b) Compatibility with platform security controls
c) Additional controls required
d) Risk of onboarding

### 19.2.3 Onboarding Checklist

Security onboarding checklist:

- [ ] Security requirements documented
- [ ] Data classification confirmed
- [ ] Compliance requirements confirmed
- [ ] Shared responsibility acknowledged
- [ ] Client security contact identified
- [ ] Spoke subscription provisioned
- [ ] Network segmentation configured
- [ ] Logging configured
- [ ] Access provisioned
- [ ] Client security briefing completed

## 19.3 Spoke Security

### 19.3.1 Spoke Baseline

Each client spoke SHALL have:

a) Azure Policy inheritance from Landing Zones management group
b) Network peering to hub
c) Forced tunneling through Azure Firewall
d) Diagnostic settings to central Log Analytics
e) Defender for Cloud enabled
f) Default NSG on subnets

### 19.3.2 Client Responsibilities

Clients are responsible for:

a) Workload security configuration
b) Application security
c) Data protection within workload
d) Workload vulnerability management
e) Workload backup
f) Workload access management

## 19.4 Offboarding

### 19.4.1 Offboarding Process

Client offboarding SHALL include:

a) Data export/migration assistance
b) Access revocation
c) Resource deletion verification
d) Log retention per requirements
e) Subscription decommissioning

### 19.4.2 Data Handling

Upon offboarding:

a) Client data exported per client requirements
b) Data retention per legal requirements
c) Secure deletion after retention period
d) Deletion confirmation provided

---

# 20. ROLES AND RESPONSIBILITIES

## 20.1 RACI Matrix

| Activity | Security Authority | Platform Team | Security Ops | Client |
|----------|-------------------|---------------|--------------|--------|
| Security governance | A | R | C | I |
| Risk acceptance | A | R | C | I |
| Policy management | A | R | C | I |
| Identity management | A | R | R | C |
| Network security | A | R | C | I |
| Security monitoring | I | C | R | I |
| Incident response | A | R | R | C |
| Vulnerability management | A | R | R | C |
| Change management | A | R | C | C |
| Client onboarding | A | R | C | R |
| Workload security | I | C | C | R |
| Data protection | I | C | C | R |

**Legend:** R=Responsible, A=Accountable, C=Consulted, I=Informed

## 20.2 Role Definitions

### 20.2.1 Security Authority

- Accountable for platform security posture
- Approves security policies and exceptions
- Accepts residual risk
- Commissions security assessments

### 20.2.2 Platform Security Authority

- Day-to-day security governance
- Security control implementation oversight
- Security incident management oversight
- Continuous compliance monitoring

### 20.2.3 Platform Engineering

- Platform infrastructure deployment
- Configuration management
- Change implementation
- Capacity management

### 20.2.4 Security Operations

- Security monitoring and alerting
- Incident detection and response
- Vulnerability management
- Security tool administration

### 20.2.5 Platform Operations

- Platform health monitoring
- Operational issue resolution
- Maintenance execution
- Client support

### 20.2.6 Client Security Contact

- Workload security responsibility
- Incident coordination with platform
- Access request management
- Compliance coordination

---

# 21. EXCEPTION MANAGEMENT

## 21.1 Exception Process

### 21.1.1 Exception Request

Security exceptions require:

a) Business justification
b) Risk assessment
c) Compensating controls
d) Exception duration
e) Review schedule

### 21.1.2 Exception Approval

| Risk Level | Approval Authority |
|------------|-------------------|
| Low | Platform Security Authority |
| Medium | Security Authority |
| High | Executive + Security Authority |
| Critical | Not permitted |

### 21.1.3 Exception Documentation

Exceptions SHALL be documented with:

- Exception ID
- Description
- Justification
- Risk assessment
- Compensating controls
- Approval
- Expiration date
- Review schedule

## 21.2 Exception Review

Exceptions SHALL be reviewed:

a) Before expiration
b) After security incidents
c) After significant changes
d) At least annually

---

# 22. COMPLIANCE VERIFICATION

## 22.1 Compliance Activities

### 22.1.1 Continuous Compliance

- Azure Policy compliance monitoring
- Defender for Cloud regulatory compliance
- Automated control validation
- Configuration drift detection

### 22.1.2 Periodic Assessment

- Quarterly compliance reviews
- Annual security assessments
- Penetration testing (annual)
- Third-party audits (as required)

## 22.2 Evidence Management

### 22.2.1 Evidence Collection

Evidence SHALL be maintained for:

- Control implementation
- Policy compliance
- Incident response
- Change management
- Access management

### 22.2.2 Evidence Retention

Evidence SHALL be retained:

- Minimum 3 years
- Longer per specific requirements
- Accessible for audits

---

# 23. DOCUMENT MAINTENANCE

## 23.1 Review Schedule

This document SHALL be reviewed:

- Annually (minimum)
- Following significant changes
- Following security incidents
- Following audit findings

## 23.2 Change Process

Document changes require:

a) Change request with justification
b) Security Authority review
c) Stakeholder review
d) Approval
e) Version update
f) Communication to stakeholders

## 23.3 Version Control

All versions SHALL be maintained with:

- Version number
- Date
- Author
- Change description
- Approval

---

# APPENDIX A: ITSG-33 CONTROL MAPPING

## A.1 Control Implementation Summary

| Family | Control | Implementation | Status |
|--------|---------|----------------|--------|
| **AC - Access Control** ||||
| AC-1 | Access Control Policy | This document + procedures | Implemented |
| AC-2 | Account Management | Entra ID + procedures | Implemented |
| AC-3 | Access Enforcement | Azure RBAC | Implemented |
| AC-4 | Information Flow | Azure Firewall + NSGs | Implemented |
| AC-5 | Separation of Duties | RBAC role design | Implemented |
| AC-6 | Least Privilege | RBAC + PIM | Implemented |
| AC-7 | Unsuccessful Login | Conditional Access + monitoring | Implemented |
| AC-8 | System Use Notification | Azure portal banner | Implemented |
| AC-11 | Session Lock | Conditional Access session controls | Implemented |
| AC-12 | Session Termination | Azure session timeout | Implemented |
| AC-17 | Remote Access | Azure Bastion + VPN | Implemented |
| AC-18 | Wireless Access | Not applicable (cloud) | N/A |
| AC-19 | Access Control Mobile | Conditional Access | Implemented |
| AC-20 | External Systems | Firewall egress control | Implemented |
| **AU - Audit and Accountability** ||||
| AU-1 | Audit Policy | This document | Implemented |
| AU-2 | Audit Events | Log Analytics + Sentinel | Implemented |
| AU-3 | Content of Audit Records | Azure diagnostic logs | Implemented |
| AU-4 | Audit Storage | Log Analytics retention | Implemented |
| AU-5 | Response to Failures | Monitoring + alerting | Implemented |
| AU-6 | Audit Review | SOC procedures | Implemented |
| AU-7 | Audit Reduction | Log Analytics queries | Implemented |
| AU-8 | Time Stamps | Azure platform time | Implemented |
| AU-9 | Protection of Audit Info | RBAC + immutable storage | Implemented |
| AU-11 | Audit Record Retention | 365 days online + archive | Implemented |
| AU-12 | Audit Generation | Azure diagnostics enabled | Implemented |
| **CM - Configuration Management** ||||
| CM-1 | Configuration Policy | This document | Implemented |
| CM-2 | Baseline Configuration | IaC repository | Implemented |
| CM-3 | Configuration Change | Change management process | Implemented |
| CM-4 | Security Impact Analysis | Change assessment | Implemented |
| CM-5 | Access Restrictions | IaC pipeline + RBAC | Implemented |
| CM-6 | Configuration Settings | Azure Policy | Implemented |
| CM-7 | Least Functionality | Resource restrictions | Implemented |
| CM-8 | Information System Inventory | Azure Resource Graph | Implemented |
| CM-9 | Configuration Plan | This document | Implemented |
| CM-10 | Software Usage | Marketplace restrictions | Implemented |
| CM-11 | User-Installed Software | Policy restrictions | Implemented |
| **CP - Contingency Planning** ||||
| CP-1 | Contingency Policy | This document | Implemented |
| CP-2 | Contingency Plan | Section 14 | Implemented |
| CP-3 | Contingency Training | Annual exercise | Implemented |
| CP-4 | Contingency Testing | Annual DR test | Implemented |
| CP-6 | Alternate Storage | Canada East region | Implemented |
| CP-7 | Alternate Processing | Canada East region | Implemented |
| CP-9 | System Backup | Azure Backup + IaC | Implemented |
| CP-10 | Recovery/Reconstitution | DR procedures | Implemented |
| **IA - Identification and Authentication** ||||
| IA-1 | I&A Policy | This document | Implemented |
| IA-2 | User Identification | Entra ID | Implemented |
| IA-3 | Device Identification | Conditional Access | Implemented |
| IA-4 | Identifier Management | Entra ID lifecycle | Implemented |
| IA-5 | Authenticator Management | Entra ID + MFA | Implemented |
| IA-6 | Authenticator Feedback | Azure portal | Implemented |
| IA-7 | Cryptographic Auth | Certificate auth available | Implemented |
| IA-8 | Non-Org User I&A | B2B with MFA | Implemented |
| **IR - Incident Response** ||||
| IR-1 | Incident Response Policy | This document | Implemented |
| IR-2 | Incident Response Training | SOC training | Implemented |
| IR-3 | Incident Response Testing | Annual exercise | Implemented |
| IR-4 | Incident Handling | Section 13 procedures | Implemented |
| IR-5 | Incident Monitoring | Sentinel | Implemented |
| IR-6 | Incident Reporting | Reporting procedures | Implemented |
| IR-7 | Incident Assistance | SOC support | Implemented |
| IR-8 | Incident Response Plan | Section 13 | Implemented |
| **MA - Maintenance** ||||
| MA-1 | Maintenance Policy | This document | Implemented |
| MA-2 | Controlled Maintenance | Change management | Implemented |
| MA-3 | Maintenance Tools | Approved tools only | Implemented |
| MA-4 | Nonlocal Maintenance | Azure portal + Bastion | Implemented |
| MA-5 | Maintenance Personnel | RBAC controlled | Implemented |
| **MP - Media Protection** ||||
| MP-1 | Media Protection Policy | Microsoft responsibility | Inherited |
| MP-2 | Media Access | RBAC | Implemented |
| MP-4 | Media Storage | Azure encryption | Implemented |
| MP-6 | Media Sanitization | Microsoft procedures | Inherited |
| **PL - Planning** ||||
| PL-1 | Security Planning Policy | This document | Implemented |
| PL-2 | System Security Plan | This document | Implemented |
| PL-4 | Rules of Behavior | Acceptable use policy | Implemented |
| **RA - Risk Assessment** ||||
| RA-1 | Risk Assessment Policy | This document | Implemented |
| RA-2 | Security Categorization | Section 3 | Implemented |
| RA-3 | Risk Assessment | Section 6 | Implemented |
| RA-5 | Vulnerability Scanning | Defender | Implemented |
| **SA - System and Services Acquisition** ||||
| SA-1 | Acquisition Policy | Procurement policy | Implemented |
| SA-2 | Resource Allocation | Capacity management | Implemented |
| SA-3 | System Dev Lifecycle | IaC + CI/CD | Implemented |
| SA-4 | Acquisition Process | Procurement requirements | Implemented |
| SA-9 | External Services | Microsoft assessment | Implemented |
| **SC - System and Communications Protection** ||||
| SC-1 | SC Policy | This document | Implemented |
| SC-5 | DoS Protection | Azure DDoS + Firewall | Implemented |
| SC-7 | Boundary Protection | Azure Firewall + NSGs | Implemented |
| SC-8 | Transmission Confidentiality | TLS 1.2+ | Implemented |
| SC-12 | Cryptographic Key Mgmt | Key Vault | Implemented |
| SC-13 | Cryptographic Protection | Azure encryption | Implemented |
| SC-17 | PKI Certificates | Managed certificates | Implemented |
| SC-20 | Secure DNS | Azure DNS | Implemented |
| SC-23 | Session Authenticity | TLS | Implemented |
| SC-28 | Protection at Rest | Azure encryption | Implemented |
| **SI - System and Information Integrity** ||||
| SI-1 | SI Policy | This document | Implemented |
| SI-2 | Flaw Remediation | Vulnerability management | Implemented |
| SI-3 | Malicious Code Protection | Defender | Implemented |
| SI-4 | System Monitoring | Sentinel + Defender | Implemented |
| SI-5 | Security Alerts | CCCS advisories | Implemented |
| SI-7 | Software Integrity | Azure policy | Implemented |
| SI-10 | Information Input Validation | Application responsibility | Client |
| SI-12 | Information Handling | Data protection policy | Implemented |

---

# APPENDIX B: EVIDENCE REQUIREMENTS

## B.1 Control Evidence Matrix

| Control Area | Evidence Type | Location | Frequency |
|--------------|--------------|----------|-----------|
| Access Control | RBAC export | Azure Portal | Quarterly |
| Access Control | PIM activation logs | Azure AD | Continuous |
| Access Control | Conditional Access policies | Azure AD | Quarterly |
| Authentication | MFA registration report | Azure AD | Monthly |
| Authentication | Sign-in logs | Log Analytics | Continuous |
| Network Security | Firewall rules export | Azure Portal | Quarterly |
| Network Security | NSG rules export | Azure Portal | Quarterly |
| Logging | Diagnostic settings | Azure Portal | Quarterly |
| Logging | Log Analytics retention | Azure Portal | Quarterly |
| Vulnerability | Defender recommendations | Azure Portal | Weekly |
| Vulnerability | Vulnerability report | Defender | Monthly |
| Compliance | Azure Policy compliance | Azure Portal | Weekly |
| Compliance | Defender secure score | Azure Portal | Weekly |
| Change Management | Change records | ITSM tool | Continuous |
| Incident Response | Incident records | ITSM/Sentinel | Continuous |

---

# APPENDIX C: CONTROL INHERITANCE MODEL

## C.1 Inheritance Overview

Client workloads inherit controls from the platform layer. This appendix documents which controls are inherited, partially inherited, or client-implemented.

## C.2 Fully Inherited Controls

Clients fully inherit these controls without additional implementation:

- Physical security (Microsoft)
- Tenant security configuration
- Network perimeter security (Azure Firewall)
- Centralized logging infrastructure
- SIEM and threat detection
- Platform identity provider
- Conditional Access policies
- Break-glass procedures
- DNS security
- DDoS protection

## C.3 Partially Inherited Controls

Clients inherit baseline controls but must implement workload-specific requirements:

| Platform Provides | Client Implements |
|------------------|-------------------|
| Hub network security | Spoke NSG rules |
| Centralized logging | Workload diagnostic settings |
| Defender for Cloud | Workload security recommendations |
| Vulnerability scanning infra | Workload patching |
| Key Vault infrastructure | Workload secrets |
| Backup infrastructure | Workload backup policies |

## C.4 Client-Implemented Controls

Clients must fully implement these controls:

- Application authentication/authorization
- Application code security
- Data classification
- Data encryption decisions
- Application logging
- Workload-specific access control
- Application vulnerability management
- Workload DR procedures

---

# APPENDIX D: GLOSSARY

| Term | Definition |
|------|------------|
| Azure Firewall | Cloud-native network security service |
| Azure Policy | Azure governance and compliance service |
| CAB | Change Advisory Board |
| CCCS | Canadian Centre for Cyber Security |
| Conditional Access | Azure AD policy-based access control |
| DR | Disaster Recovery |
| Entra ID | Microsoft's cloud identity service (formerly Azure AD) |
| Hub | Central network providing shared services |
| IaC | Infrastructure as Code |
| ITSG-33 | IT Security Risk Management: A Lifecycle Approach |
| JIT | Just-In-Time access |
| MI/MA | Medium Integrity / Medium Availability |
| MFA | Multi-Factor Authentication |
| NSG | Network Security Group |
| PaaS | Platform as a Service |
| PBMM | Protected B / Medium / Medium |
| PIM | Privileged Identity Management |
| RBAC | Role-Based Access Control |
| RPO | Recovery Point Objective |
| RTO | Recovery Time Objective |
| SA&A | Security Assessment and Authorization |
| Sentinel | Microsoft's cloud-native SIEM |
| SIEM | Security Information and Event Management |
| SOC | Security Operations Centre |
| Spoke | Client workload virtual network |
| SSE | Storage Service Encryption |
| TDE | Transparent Data Encryption |
| TLS | Transport Layer Security |

---

**END OF DOCUMENT**

---

*This document is PROTECTED B when populated with system-specific information.*

*Document classification when blank: UNCLASSIFIED*
