
# Server Roles Documentation

## ISCSI Server

<img width="560" height="383" alt="image" src="https://github.com/user-attachments/assets/18be982e-17aa-4433-82fd-94823e895ee3" />

**iSCSI** (Internet Small Computer Systems Interface) is a protocol that enables servers and users to access shared storage over a TCP/IP network. It uses:

- **iSCSI Initiator** (client)
- **iSCSI Target** (server)

Provides **block-level storage** access.

### Benefits

- Cost-effective – uses standard Ethernet
- Multipathing support – better performance and redundancy

### Limitations

- May underperform compared to high-end storage setups
- 10Gb Ethernet helps close the performance gap

### Configuration

1. Install iSCSI target on the server
2. Install iSCSI initiator on client systems
3. Discover and connect to the target from the initiator
4. Configure authentication (optional)

---

## DHCP Server 


<img width="450" height="250" alt="image" src="https://github.com/user-attachments/assets/5116f993-cdc4-474b-a623-30b78794b5cf" />


**DHCP** (Dynamic Host Configuration Protocol) assigns IP addresses automatically to devices on a network.

### Benefits

- No manual IP configuration needed
- Reduces configuration errors and saves time

### Limitations

- If the server is down, devices can't get IPs
- Vulnerable to IP spoofing and unauthorized access

### Configuration

1. Install DHCP server software
2. Define IP address range (scope)
3. Set DNS, gateway, and lease settings

---

## DNS Server

<img width="450" height="250" alt="image" src="https://github.com/user-attachments/assets/013778a2-5e9d-42bd-8b15-20482270a090" />

**DNS** (Domain Name System) translates domain names into IP addresses.

### Benefits

- Easier to access websites (name vs. IP)
- Faster browsing via DNS caching
- Can help detect and block threats (with security settings)

### Limitations

- Centralized control (ICANN)
- Attackers can spoof or hide real IPs

### Configuration

1. Install DNS server software
2. Create domain zones
3. Add DNS records (A,CNAME,..)

---

## RADIUS Server

<img width="500" height="350" alt="image" src="https://github.com/user-attachments/assets/600ee289-da2d-4f01-903f-45b0282c90d9" />

**RADIUS** (Remote Authentication Dial-In User Service) is a protocol that enables remote user authentication and access control over a network.

It operates using a **client/server model**. When a user connects remotely via VPN, their credentials are sent to the RADIUS server, which then **authenticates** and **authorizes** the connection.

### Benefits

- **Enhanced Security**: Only authorized users are granted network access, reducing the risk of unauthorized access or attacks.
- **Policy Enforcement**: RADIUS servers can enforce password complexity, session timeouts, and other security policies.

### Limitations

- **Configuration Complexity**: RADIUS server setup can be complex and may require integration with other systems like Active Directory or LDAP.
- **Single Point of Failure**: If redundancy is not set up, failure of the RADIUS server could lock out all remote users.

### Configuration

1. Install RADIUS server software (Microsoft NPS or FreeRADIUS).
2. Configure RADIUS clients (VPN gateways or wireless access points) with the RADIUS server's IP and shared secret.
3. Set up a user database (local, Active Directory, or LDAP).
4. Define authentication and authorization policies.
5. Enable logging and monitoring for auditing and troubleshooting.

