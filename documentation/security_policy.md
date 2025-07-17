# Security Policy

This document outlines the key security mechanisms applied to the network design, with a focus on segmentation, service isolation, and access control.

---

## Network Segmentation (VLAN)
Each department is assigned its own VLAN and IP subnet, limiting broadcast domains and reducing the risk of lateral movement in the event of compromise.

| VLAN | Department               | Subnet           |
|------|--------------------------|------------------|
| 10   | Management & Secretariat | 192.168.10.0/24  |
| 20   | Study                    | 192.168.20.0/24  |
| 30   | Production               | 192.168.30.0/24  |
| 40   | Support A                | 192.168.40.0/24  |
| 50   | Support B                | 192.168.50.0/24  |
| 60   | DMZ (Servers)            | 192.168.60.0/24  |

---

## DMZ Implementation
A separate VLAN (VLAN 60) is reserved for DNS, DHCP, and iSCSI servers. This zone acts as a **buffer** between internal users and critical infrastructure, ensuring:
- Controlled access through ACLs
- Minimal exposure of internal services
- Centralized management

---

## Access Control Lists (ACLs)
ACLs are configured on the router or multilayer switch to:
- Deny all inter-VLAN communication by default
- Permit specific services (e.g., DNS, DHCP) from user VLANs to the DMZ
- Allow only the Management VLAN to access the iSCSI server
- Prevent access from user VLANs to other VLANs unless explicitly permitted

ACLs have been tested using ping and DNS resolution to ensure that:
- Only allowed traffic is forwarded
- Unauthorized access attempts are blocked
- Inter-VLAN isolation is enforced

---

## Server Access Strategy
- All servers have **static IPs**
- DNS and DHCP are reachable from all VLANs
- The iSCSI server is reachable **only** from VLAN 10 (Management)
- No direct access to servers from external networks
- Server configurations enforce access control at the service level (e.g., BIND views, DHCP relay scopes)

---

## Administrative Security

### RADIUS Authentication
- All routers and switches are configured with AAA and use a **centralized FreeRADIUS server**
- This reduces the risk of compromise and allows for centralized user management
- Login access is restricted using `login authentication default` and privilege levels

### CLI Hardening
- Console and VTY lines are secured with:
  - **Encrypted passwords** (`service password-encryption`, `enable secret`)
  - **Session timeouts**
  - **Login banners**
  - **SSH-only access**, disabling Telnet entirely

### RADIUS Benefits Summary:
- Prevents password sprawl across devices
- Enables consistent logging of access attempts
- Supports secure authentication methods (e.g., CHAP, MS-CHAPv2)

---

## Summary
The layered security approach includes:
- VLAN-based segmentation
- ACL filtering for precise inter-VLAN traffic control
- Service isolation in a DMZ with dedicated VLAN
- Static addressing for critical infrastructure
- RADIUS-based centralized authentication
- Hardened administrative access (VTY, console, SSH)

This strategy follows the **principle of least privilege** and ensures a **scalable, auditable, and resilient security posture** for the client's network infrastructure.