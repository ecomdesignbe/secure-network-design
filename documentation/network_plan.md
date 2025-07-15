# IP Addressing Plan and VLAN Segmentation

## 1. Design Principles
Each department is assigned its own VLAN and subnet. A /24 subnet is used to:
- Support current host count comfortably
- Provide margin for future scalability
- Simplify routing and ACL management

Inter-VLAN communication will be controlled using Layer 3 routing and Access Control Lists (ACLs).

---

## 2. VLAN and IP Plan

| Department                 | VLAN ID | Subnet            | Gateway        | Estimated Hosts |
|----------------------------|---------|-------------------|----------------|-----------------|
| Management % Secretariat   | 10      | 192.168.10.0/24   | 192.168.10.1   | 5               |
| Study Area                 | 20      | 192.168.20.0/24   | 192.168.20.1   | 8               |
| Production                 | 30      | 192.168.30.0/24   | 192.168.30.1   | 10              |
| Support 1                  | 40      | 192.168.40.0/24   | 192.168.40.1   | 10              |
| Support 2                  | 50      | 192.168.50.0/24   | 192.168.50.1   | 10              |
| DMZ (Servers)              | 60      | 192.168.60.0/24   | 192.168.60.1   | 3+              |

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