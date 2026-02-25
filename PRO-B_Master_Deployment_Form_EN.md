# PROTECTED B ENVIRONMENT
# MASTER DEPLOYMENT REQUEST FORM

**Government of Canada — Technology Deployment Authorization**

> **INSTRUCTIONS:** This modular form covers all technology deployment types. Select only the sections relevant to your specific deployment. Sections marked with ⚙️ are REQUIRED for all submissions. Sections marked with 📋 are CONDITIONAL based on deployment type.

---

## ⚙️ SECTION 1: PROJECT OVERVIEW & DEPLOYMENT TYPE

| Field | Description | Required |
|-------|-------------|----------|
| **Project Name** | | Yes |
| **Project ID** | | Yes |
| **Deployment Date** | | Yes |
| **Technology Type** | ☐ VPN ☐ Firewall ☐ Load Balancer ☐ API Gateway ☐ Network Switch ☐ Router ☐ IDS/IPS ☐ WAF ☐ Other: _____ | Yes |
| **Requestor Name** | | Yes |
| **Requestor Title** | | Yes |
| **Requestor Email** | | Yes |
| **Requestor Phone** | | Yes |
| **Approving Authority** | | Yes |
| **Budget Code** | | No |

---

## ⚙️ SECTION 2: EXECUTIVE SUMMARY

**Business Justification:**
> _____________________________________________________________________________
> _____________________________________________________________________________

**Expected Benefits:**
> _____________________________________________________________________________
> _____________________________________________________________________________

**Project Timeline:**

| Milestone | Target Date |
|-----------|-------------|
| Planning Complete | |
| Testing Complete | |
| Production Deployment | |
| Post-Implementation Review | |

---

## ⚙️ SECTION 3: INFRASTRUCTURE & SYSTEM INVENTORY

| System/Component Name | Type | Hostname | IP Address | Environment | Owner | Notes |
|-----------------------|------|----------|------------|-------------|-------|-------|
| | | | | ☐ Dev ☐ Test ☐ Prod | | |
| | | | | ☐ Dev ☐ Test ☐ Prod | | |
| | | | | ☐ Dev ☐ Test ☐ Prod | | |
| | | | | ☐ Dev ☐ Test ☐ Prod | | |
| | | | | ☐ Dev ☐ Test ☐ Prod | | |

---

## ⚙️ SECTION 4: NETWORK COMMUNICATION MATRIX (INTERNAL)

| Source | Destination | Protocol | Port(s) | Direction | Purpose | Encrypted |
|--------|-------------|----------|---------|-----------|---------|-----------|
| | | ☐ TCP ☐ UDP ☐ ICMP | | ☐ In ☐ Out ☐ Both | | ☐ Yes ☐ No |
| | | ☐ TCP ☐ UDP ☐ ICMP | | ☐ In ☐ Out ☐ Both | | ☐ Yes ☐ No |
| | | ☐ TCP ☐ UDP ☐ ICMP | | ☐ In ☐ Out ☐ Both | | ☐ Yes ☐ No |
| | | ☐ TCP ☐ UDP ☐ ICMP | | ☐ In ☐ Out ☐ Both | | ☐ Yes ☐ No |
| | | ☐ TCP ☐ UDP ☐ ICMP | | ☐ In ☐ Out ☐ Both | | ☐ Yes ☐ No |

---

## 📋 SECTION 5: EXTERNAL COMMUNICATION

*Required for deployments with external network connectivity*

| Source | Destination | Protocol | Port(s) | Frequency | Sensitivity | Encrypted |
|--------|-------------|----------|---------|-----------|-------------|-----------|
| | | | | ☐ Continuous ☐ Scheduled | ☐ Public ☐ Internal ☐ Confidential | ☐ Yes ☐ No |
| | | | | ☐ Continuous ☐ Scheduled | ☐ Public ☐ Internal ☐ Confidential | ☐ Yes ☐ No |
| | | | | ☐ Continuous ☐ Scheduled | ☐ Public ☐ Internal ☐ Confidential | ☐ Yes ☐ No |

---

## ⚙️ SECTION 6: SECURITY & ENCRYPTION REQUIREMENTS

### Data Classification
☐ Unclassified  ☐ Protected A  ☐ Protected B  ☐ Secret  ☐ Top Secret

### In-Transit Encryption (per ITSP.40.111)
☐ TLS 1.2  ☐ TLS 1.3  ☐ IPSec  ☐ SSH  ☐ Other: _____________________

### At-Rest Encryption
☐ AES-256  ☐ AES-192  ☐ AES-128  ☐ N/A

### Authentication Methods
☐ Username/Password  
☐ Multi-Factor Authentication (MFA)  
☐ Certificate-Based  
☐ OAuth 2.0  
☐ SAML 2.0  
☐ Kerberos  
☐ Other: _____________________

### Access Control Model
☐ Role-Based Access Control (RBAC)  
☐ Attribute-Based Access Control (ABAC)  
☐ Zero Trust Architecture  

### Principle of Least Privilege
☐ Implemented  ☐ Planned  ☐ Not Applicable

---

## 📋 SECTION 7: FIREWALL & NETWORK SECURITY RULES

*Required for Firewall, VPN, and perimeter deployments*

| Rule # | Source | Destination | Protocol | Port(s) | Action | Logging | Priority |
|--------|--------|-------------|----------|---------|--------|---------|----------|
| | | | | | ☐ Allow ☐ Deny | ☐ Yes ☐ No | ☐ High ☐ Med ☐ Low |
| | | | | | ☐ Allow ☐ Deny | ☐ Yes ☐ No | ☐ High ☐ Med ☐ Low |
| | | | | | ☐ Allow ☐ Deny | ☐ Yes ☐ No | ☐ High ☐ Med ☐ Low |
| | | | | | ☐ Allow ☐ Deny | ☐ Yes ☐ No | ☐ High ☐ Med ☐ Low |
| | | | | | ☐ Allow ☐ Deny | ☐ Yes ☐ No | ☐ High ☐ Med ☐ Low |

**Default Policy:** ☐ Deny All (Whitelist)  ☐ Allow All (Blacklist)

---

## ⚙️ SECTION 8: COMPLIANCE & REGULATORY REQUIREMENTS

### Applicable Frameworks (select all that apply)
☐ ITSP.40.111 (Cryptographic Algorithms for Unclassified, Protected A & B)  
☐ PIPEDA (Personal Information Protection and Electronic Documents Act)  
☐ SOC 2 Type II  
☐ ISO 27001  
☐ NIST Cybersecurity Framework (GC Adoption)  
☐ POCTIA (Policy on Communications and Federal Identity)  
☐ TBS Policy on Service and Digital  
☐ TBS Directive on Security Management  
☐ Other: _____________________

### Data Residency Requirements
☐ Canada Only  ☐ North America  ☐ International (specify): _____________________

### Logging Requirements
**Level:** ☐ Minimal  ☐ Standard  ☐ Comprehensive  ☐ Forensic

**Retention Period:** ☐ 30 days  ☐ 90 days  ☐ 1 year  ☐ 7 years  ☐ Other: _____

### Incident Response
**Incident Response Plan in Place:** ☐ Yes  ☐ No

**Event Reporting Timeline:** ☐ Immediate  ☐ 24 hours  ☐ 72 hours  ☐ As per SLA

---

## 📋 SECTION 9: VULNERABILITY MANAGEMENT & PATCHING

*Required for all internet-facing or critical infrastructure deployments*

### Vulnerability Scanning Frequency
☐ Weekly  ☐ Monthly  ☐ Quarterly  ☐ N/A

### Patching Schedule
| Severity | Timeline |
|----------|----------|
| Critical/Emergency | ☐ 24 hours  ☐ 48 hours  ☐ 72 hours |
| High/Urgent | ☐ 1 week  ☐ 2 weeks |
| Medium/Regular | ☐ 30 days  ☐ 60 days |
| Low | ☐ Next maintenance window |

---

## 📋 SECTION 10: CYBER THREAT & DDoS PROTECTION

*Required for internet-facing deployments*

### DDoS Mitigation
**Enabled:** ☐ Yes  ☐ No

**Type:** ☐ Rate-Based Filtering  ☐ Behavioral Analysis  ☐ WAF Integration  ☐ CDN-Based

### Intrusion Detection/Prevention System (IDS/IPS)
**Enabled:** ☐ Yes  ☐ No

**Mode:** ☐ Detection Only  ☐ Prevention  ☐ Both

### GC Threat Feed Integration
**Enabled:** ☐ Yes  ☐ No

**Real-time Updates:** ☐ Yes  ☐ No

---

## 📋 SECTION 11: PACKET ANALYSIS & NETWORK MONITORING

*Required for network infrastructure deployments*

### Monitoring Technologies
☐ NetFlow  
☐ sFlow  
☐ IPFIX  
☐ Full Packet Capture  
☐ Deep Packet Inspection (DPI)  
☐ SNMP  
☐ Other: _____________________

### Bandwidth Monitoring
☐ Required  ☐ Not Required

**Expected Bandwidth:** __________ Mbps/Gbps

### Quality of Service (QoS)
☐ Required  ☐ Not Required

**SLA Requirements:** _____________________

---

## ⚙️ SECTION 12: BACKUP & DISASTER RECOVERY

### Backup Strategy
☐ Full Backup  
☐ Incremental  
☐ Differential  
☐ Continuous Replication  
☐ N/A

### Recovery Objectives
| Metric | Value |
|--------|-------|
| **RTO (Recovery Time Objective)** | __________ hours/days |
| **RPO (Recovery Point Objective)** | __________ hours |

### Backup Location
☐ On-Premises  ☐ Cloud (GC-approved)  ☐ Geo-Redundant  ☐ Hybrid

### Backup Testing Frequency
☐ Monthly  ☐ Quarterly  ☐ Annually  ☐ N/A

---

## ⚙️ SECTION 13: CHANGE MANAGEMENT & TESTING

### Pre-Production Testing
☐ Required  ☐ Not Required

### Test Environment(s)
☐ Development  ☐ Test  ☐ Staging  ☐ Production (limited)

### Change Advisory Board (CAB) Approval
☐ Required  ☐ Not Required

### Rollback Plan Documented
☐ Yes  ☐ No

---

## 📋 SECTION 14: VENDOR & THIRD-PARTY INFORMATION

| Vendor/Product | Version | Support Level | SLA | Security Certification | Notes |
|----------------|---------|---------------|-----|------------------------|-------|
| | | ☐ Platinum ☐ Gold ☐ Silver ☐ Bronze | | ☐ SOC 2 ☐ ISO 27001 ☐ FedRAMP | |
| | | ☐ Platinum ☐ Gold ☐ Silver ☐ Bronze | | ☐ SOC 2 ☐ ISO 27001 ☐ FedRAMP | |
| | | ☐ Platinum ☐ Gold ☐ Silver ☐ Bronze | | ☐ SOC 2 ☐ ISO 27001 ☐ FedRAMP | |

---

## SECTION 15: ADDITIONAL REQUIREMENTS & COMMENTS

> _____________________________________________________________________________
> _____________________________________________________________________________
> _____________________________________________________________________________
> _____________________________________________________________________________

---

## ⚙️ SECTION 16: APPROVALS & SIGN-OFF

| Role | Name | Title | Signature | Date |
|------|------|-------|-----------|------|
| **Requestor** | | | | |
| **Technical Lead** | | | | |
| **Security Officer** | | | | |
| **Compliance Officer** | | | | |
| **Approving Authority** | | | | |

---

**Document Version:** 1.0  
**Classification:** Protected B  
**Last Updated:** _____________________

---

*This form is designed to meet Government of Canada Protected B requirements for technology deployments. Ensure all applicable sections are completed before submission.*
