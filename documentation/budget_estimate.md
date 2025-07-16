# BUDGET MANAGEMENT REPORT (First Step)

## SWITCHES

- **Cisco CBS250-24T-4G** (24 ports Gigabit Ethernet, STP) – ~€300  
- **Cisco CBS350-24T-4G** (24 ports Gigabit Ethernet, 4x1G SFP) – ~€600  

---

## SERVERS

- **iSCSI Server** – HPE ProLiant ML30 Gen11 – ~€1300  
- **RADIUS Server** – Dell PowerEdge T140 – ~€700  
- **DHCP Server** – Dell PowerEdge T140 / HPE ML30 Gen11 – ~€700  
- **DNS Server** – Dell PowerEdge T140 / HPE ML30 Gen11 – ~€700  

---

## ROUTERS (Choose one based on context)

- **Ubiquiti EdgeRouter 6P** – ~€200  
  _Widely used in small and medium businesses. Very cost-efficient and supports VLANs._

- **Cisco ISR 1010** – ~€900  
  _Works best in an all-Cisco setup. Offers strong routing capabilities but is more expensive._

- **No router needed** – ~€0  
  _In many cases, a separate router is unnecessary. VLAN routing can be handled by Layer 3 switches, and security by the Cisco Firepower firewall — resulting in simpler design and cost savings._

---

## FIREWALL

- **Cisco Firepower 1010** – ~€1500  
  _Advanced firewall solution. Requires additional licenses for features such as URL filtering, intrusion prevention, and malware protection._

---

## COST BREAKDOWN

| Category   | Item                                   | Qty | Unit Price | Total   |
|------------|----------------------------------------|-----|------------|---------|
| **Switches** | Cisco CBS250-24T-4G (Access Switches) | 4   | €300       | €1,200  |
|            | Cisco CBS350-24T-4G (Core Switch)      | 1   | €600       | €600    |
| **Servers** | iSCSI Server – HPE ProLiant ML30 G11   | 1   | €1,300     | €1,300  |
|            | RADIUS Server – Dell PowerEdge T140    | 1   | €700       | €700    |
|            | DHCP Server – Dell T140 / HPE ML30 G11 | 1   | €700       | €700    |
|            | DNS Server – Dell T140 / HPE ML30 G11  | 1   | €700       | €700    |
| **Router**  | Ubiquiti EdgeRouter 6P                 | 1   | €200       | €200    |
| **Firewall**| Cisco Firepower 1010                   | 1   | €1,500     | €1,500  |

### **TOTAL ESTIMATED COST**  
**€6,900**

---

## Cost Optimization Tip

It is possible to significantly reduce overall costs by reusing existing servers or network hardware where appropriate.

- Some components (such as switches or mid-range servers) can be found in used or refurbished condition at a lower price from trusted suppliers.  
- This is particularly useful for lab setups, non-critical services, or in early modernization phases.  
- However, be sure to verify warranty, firmware compatibility, and support when opting for reused equipment.

