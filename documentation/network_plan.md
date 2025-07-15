# IP Addressing Plan and VLAN Segmentation

## Project Context

The client is relocating to a new office and requires a modern, secure, and cost-effective network infrastructure to support its operations. Their previous setup lacks segmentation, centralized management, and proper access control. The new design must ensure secure inter-departmental communication, central authentication, and a robust server infrastructure including DNS, DHCP, RADIUS, and iSCSI services.

The network will be segmented into multiple VLANs to reflect different departments and functions. The design must account for future scalability and ease of maintenance while strictly adhering to security best practices.

## Project Objectives

- Design and simulate a scalable, structured network using GNS3  
- Implement network segmentation using VLANs and inter-VLAN routing  
- Provide centralized services (DHCP, DNS, iSCSI, RADIUS) with redundancy where needed  
- Apply security controls using ACLs and VLAN isolation to implement a DMZ and restrict access  
- Document all configurations, IP planning, and design choices clearly  
- Ensure cost-effective equipment selection with proper technical justification  
- Enable future network growth with minimal disruption

## 1. Design Principles
Each department is assigned its own VLAN and subnet. A /24 subnet is used to:
- Support current host count comfortably
- Provide margin for future scalability
- Simplify routing and ACL management

Inter-VLAN communication will be controlled using Layer 3 routing and Access Control Lists (ACLs).

---

## 2. VLAN and IP Plan

| Department               | VLAN ID | Subnet          | Gateway        | DHCP Range         | Reserved IPs               |
|--------------------------|---------|-----------------|----------------|--------------------|----------------------------|
| Management & Secretariat | 10      | 192.168.10.0/24 | 192.168.10.1   | 192.168.10.100–150 | .1 (GW), .10–.20 static    |
| Study Area               | 20      | 192.168.20.0/24 | 192.168.20.1   | 192.168.20.100–150 | .1 (GW), .10–.20 static    |
| Production               | 30      | 192.168.30.0/24 | 192.168.30.1   | 192.168.30.100–150 | .1 (GW), .10–.20 static    |
| Support 1                | 40      | 192.168.40.0/24 | 192.168.40.1   | 192.168.40.100–150 | .1 (GW), .10–.20 static    |
| Support 2                | 50      | 192.168.50.0/24 | 192.168.50.1   | 192.168.50.100–150 | .1 (GW), .10–.20 static    |
| DMZ (Servers)            | 60      | 192.168.60.0/24 | 192.168.60.1   | N/A (static only)  | .10–.13 (DNS, DHCP, iSCSI) |

> ℹ️ The /24 subnet was selected for each VLAN to ensure scalability and address alignment, even though the estimated number of hosts per department is currently low.

---

## 3. Reserved IP Addressing Plan

| IP Address         | Purpose                      |
|--------------------|------------------------------|
| 192.168.X.1        | VLAN Gateway per subnet      |
| 192.168.60.10      | DNS Server (in DMZ)          |
| 192.168.60.11      | DHCP Server (in DMZ)         |
| 192.168.60.12      | iSCSI Server (in DMZ)        |
| 192.168.60.13      | RADIUS Server (in DMZ)       |

> Note: The X in 192.168.X.1 corresponds to the VLAN ID for easy tracking (e.g., VLAN 10 = 192.168.10.1)

---

## 4. Summary

The addressing and segmentation plan is designed to:
- Ensure logical separation of network traffic
- Facilitate ACL enforcement for inter-VLAN security
- Simplify troubleshooting and future growth