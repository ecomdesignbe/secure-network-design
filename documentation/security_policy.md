\# Security Policy



The key security mechanisms applied to the network design, with a focus on segmentation, service isolation, and access control.



---



\## Network Segmentation (VLAN)

Each department is assigned its own VLAN and IP subnet, limiting broadcast domains and reducing the risk of lateral movement in the event of compromise.



| VLAN | Department         | Subnet           |

|------|--------------------|------------------|

| 10   | Management         | 192.168.10.0/24  |

| 20   | Study              | 192.168.20.0/24  |

| 30   | Production         | 192.168.30.0/24  |

| 40   | Support A          | 192.168.40.0/24  |

| 50   | Support B          | 192.168.50.0/24  |

| 60   | DMZ (Servers)      | 192.168.60.0/24  |



---



\## DMZ Implementation

A separate VLAN (VLAN 60) is reserved for DNS, DHCP, and iSCSI servers. This zone acts as a \*\*buffer\*\* between internal users and critical infrastructure, ensuring:

\- Controlled access through ACLs

\- Minimal exposure of internal services

\- Centralized management



---



\## Access Control Lists (ACLs)

ACLs are configured on the router or multilayer switch to:

\- Deny all inter-VLAN communication by default

\- Permit specific services (e.g., DNS, DHCP) from user VLANs to the DMZ

\- Allow only the Management VLAN to access the iSCSI server



---



\## Server Access Strategy

\- All servers have \*\*static IPs\*\*

\- DNS and DHCP are reachable from all VLANs

\- The iSCSI server is reachable \*\*only\*\* from VLAN 10 (Management)

\- No direct access to servers from external networks



---



\## Administrative Security (Preview for Day 4)

\- Administrative access to routers/switches will be protected by:

&nbsp; - Strong passwords

&nbsp; - Centralized authentication using a RADIUS server

&nbsp; - Privilege-level restrictions

\- Console and VTY lines will be hardened with timeout, banners, and encrypted credentials



---



\## Summary

The layered security approach includes:

\- VLAN-based segmentation

\- ACL filtering

\- Service isolation in a DMZ

\- Static addressing for critical infrastructure

\- Previewed RADIUS authentication for management access