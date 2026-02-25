# PROTECTED B ENVIRONMENT
# SITE-TO-SITE VPN DEPLOYMENT REQUEST FORM

**Government of Canada — VPN Tunnel Authorization**

---

## SECTION 1: PROJECT OVERVIEW

| Field | Value |
|-------|-------|
| **VPN Project Name** | |
| **Project ID** | |
| **Deployment Date** | |
| **Requestor Name** | |
| **Requestor Title** | |
| **Requestor Email** | |
| **Requestor Phone** | |
| **Approving Authority** | |

---

## SECTION 2: VPN ENDPOINTS

### Site A (Local)

| Field | Value |
|-------|-------|
| **Site Name** | |
| **Physical Location** | |
| **Public IP Address** | |
| **Internal IP Range/Subnet** | |
| **Primary Contact Name** | |
| **Primary Contact Email** | |
| **Primary Contact Phone** | |

### Site B (Remote)

| Field | Value |
|-------|-------|
| **Site Name** | |
| **Physical Location** | |
| **Public IP Address** | |
| **Internal IP Range/Subnet** | |
| **Primary Contact Name** | |
| **Primary Contact Email** | |
| **Primary Contact Phone** | |

---

## SECTION 3: VPN TUNNEL SPECIFICATIONS

### Protocol Selection
☐ IPSec (IKEv2) — *Recommended*  
☐ IPSec (IKEv1)  
☐ WireGuard  
☐ OpenVPN  
☐ Other: _____________________

### Phase 1 (IKE) Parameters
| Parameter | Value |
|-----------|-------|
| **Encryption Algorithm** | ☐ AES-256 ☐ AES-192 ☐ AES-128 |
| **Hashing Algorithm** | ☐ SHA-256 ☐ SHA-384 ☐ SHA-512 |
| **DH Group** | ☐ Group 14 ☐ Group 19 ☐ Group 20 ☐ Group 21 |
| **SA Lifetime** | __________ seconds |

### Phase 2 (IPSec) Parameters
| Parameter | Value |
|-----------|-------|
| **Encryption Algorithm** | ☐ AES-256 ☐ AES-192 ☐ AES-128 |
| **Hashing Algorithm** | ☐ SHA-256 ☐ SHA-384 ☐ SHA-512 |
| **PFS Group** | ☐ Group 14 ☐ Group 19 ☐ Group 20 ☐ None |
| **SA Lifetime** | __________ seconds |

### Authentication Method
☐ Pre-Shared Key (PSK)  
☐ X.509 Certificates  
☐ EAP  
☐ Other: _____________________

**If PSK:** Key will be exchanged via: ☐ Secure channel  ☐ In-person  ☐ Encrypted email

---

## SECTION 4: NETWORK TRAFFIC & ROUTING

### Allowed Traffic Flows

| Source Network | Destination Network | Protocol | Port(s) | Purpose |
|----------------|---------------------|----------|---------|---------|
| | | ☐ TCP ☐ UDP ☐ Both | | |
| | | ☐ TCP ☐ UDP ☐ Both | | |
| | | ☐ TCP ☐ UDP ☐ Both | | |
| | | ☐ TCP ☐ UDP ☐ Both | | |
| | | ☐ TCP ☐ UDP ☐ Both | | |

### Routing Configuration
**Routing Type:** ☐ Static  ☐ Dynamic (BGP)  ☐ Policy-Based

**NAT Required:** ☐ Yes  ☐ No

If Yes, specify NAT configuration:
> _____________________________________________________________________________

---

## SECTION 5: FIREWALL RULES

### Rules Required
☐ Inbound  ☐ Outbound  ☐ Both

### Site A Firewall Rules

| Rule # | Source | Destination | Protocol | Port(s) | Action |
|--------|--------|-------------|----------|---------|--------|
| | | | | | ☐ Allow ☐ Deny |
| | | | | | ☐ Allow ☐ Deny |
| | | | | | ☐ Allow ☐ Deny |

### Site B Firewall Rules

| Rule # | Source | Destination | Protocol | Port(s) | Action |
|--------|--------|-------------|----------|---------|--------|
| | | | | | ☐ Allow ☐ Deny |
| | | | | | ☐ Allow ☐ Deny |
| | | | | | ☐ Allow ☐ Deny |

### IKE/IPSec Ports Required
☐ UDP 500 (IKE)  
☐ UDP 4500 (NAT-T)  
☐ ESP Protocol 50  
☐ AH Protocol 51  

---

## SECTION 6: SECURITY & COMPLIANCE

### Data Classification
☐ Unclassified  ☐ Protected A  ☐ Protected B

### Compliance Requirements
☐ ITSP.40.111 (Cryptographic Standards)  
☐ PIPEDA  
☐ SOC 2  
☐ ISO 27001  
☐ Other: _____________________

### Data Residency
☐ Canada Only  ☐ North America  ☐ International

### Incident Reporting Timeline
☐ Immediate  ☐ 24 hours  ☐ 72 hours  ☐ As per SLA

---

## SECTION 7: MONITORING & LOGGING

### Logging Level
☐ Minimal (connection up/down only)  
☐ Standard (connection events + errors)  
☐ Comprehensive (all traffic metadata)  

### Log Retention Period
☐ 30 days  ☐ 90 days  ☐ 1 year  ☐ 7 years

### Monitoring Requirements
**Bandwidth Monitoring:** ☐ Required  ☐ Not required

**Expected Bandwidth:** __________ Mbps

**Alerting Required:** ☐ Yes  ☐ No

If Yes, alert on:
☐ Tunnel Down  
☐ High Latency (threshold: _____ ms)  
☐ Packet Loss (threshold: _____ %)  
☐ Bandwidth Threshold (threshold: _____ Mbps)  

---

## SECTION 8: HIGH AVAILABILITY & FAILOVER

### Failover Required
☐ Yes  ☐ No

### Failover Configuration (if applicable)

| Field | Value |
|-------|-------|
| **Backup VPN Endpoint (Site A)** | |
| **Backup VPN Endpoint (Site B)** | |
| **Failover Type** | ☐ Active/Passive ☐ Active/Active |
| **Failover Trigger** | ☐ Automatic ☐ Manual |

### Recovery Objectives
| Metric | Value |
|--------|-------|
| **RTO (Recovery Time Objective)** | __________ minutes |
| **RPO (Recovery Point Objective)** | __________ minutes |

---

## SECTION 9: VENDOR INFORMATION

### VPN Solution

| Field | Value |
|-------|-------|
| **Vendor** | |
| **Product Name** | |
| **Version/Firmware** | |
| **Support Level** | ☐ Platinum ☐ Gold ☐ Silver ☐ Bronze |
| **Support SLA** | |
| **Security Certifications** | ☐ SOC 2 ☐ ISO 27001 ☐ Common Criteria ☐ FIPS 140-2/3 |

---

## SECTION 10: TESTING & VALIDATION

### Pre-Deployment Testing
☐ Required  ☐ Not required

### Test Plan
| Test | Description | Pass/Fail |
|------|-------------|-----------|
| Tunnel Establishment | Verify tunnel comes up successfully | |
| Traffic Flow | Verify allowed traffic passes through | |
| Failover | Test failover to backup (if applicable) | |
| Performance | Verify bandwidth meets requirements | |
| Security | Verify unauthorized traffic is blocked | |

### Test Environment
☐ Lab  ☐ Dev  ☐ Staging  ☐ Production (limited)

---

## SECTION 11: ADDITIONAL NOTES & REQUIREMENTS

> _____________________________________________________________________________
> _____________________________________________________________________________
> _____________________________________________________________________________
> _____________________________________________________________________________

---

## SECTION 12: APPROVALS

| Role | Name | Title | Signature | Date |
|------|------|-------|-----------|------|
| **Requestor** | | | | |
| **Technical Lead** | | | | |
| **Network Administrator** | | | | |
| **Security Officer** | | | | |
| **Approving Authority** | | | | |

---

**Document Version:** 1.0  
**Classification:** Protected B  
**Last Updated:** _____________________

---

*This form is designed specifically for Site-to-Site VPN deployments in Government of Canada Protected B environments.*
