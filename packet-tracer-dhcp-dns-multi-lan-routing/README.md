# UAE Regional Enterprise Network (Cisco Packet Tracer)

**Author:** Zunaira Rashid  
**Tool Used:** Cisco Packet Tracer  
**Project Type:** Multi-Branch Enterprise Network & Routing Lab

## 📖 Executive Summary
This project presents a comprehensive multi-site enterprise network topology built using Cisco Packet Tracer. It simulates a company with regional branches across the UAE (Dubai, Al Ain, and Qjman), interconnected via a central headquarters router. The network provides centralized DHCP and DNS services, alongside localized Web Servers for each branch.

*(Note: In the original lab file, LAN3 was labeled `72.72.72.0` but assigned `73.73.73.x` IPs. This documentation standardizes LAN3 to `73.73.73.0` for logical clarity.)*

## 🏢 The Scenario
A regional enterprise needs a scalable network to connect its multiple offices across the UAE. 
- **Headquarters (Router1):** Acts as the central hub. It hosts the **DHCP Server** for automated IP management and the **Dubai Web Server** (`www.dubai.com`). It also connects to the **Al Ain branch** and the **Qjman branch**.
- **Secondary Site (Router2):** Hosts the **Central DNS Server** to resolve domain names for the entire company, alongside a secondary server and PC.
- **Goal:** Ensure full OSPF or RIP routing between all routers so any PC in any branch can access the DNS, DHCP, and all three localized Web Servers.

## 🗺️ Network Topology Breakdown

| LAN | Network ID | Gateway | Key Devices | Connected To |
| :--- | :--- | :--- | :--- | :--- |
| **LAN1** | 70.70.70.0/24 | 70.70.70.1 | PC Host A, PC Host B, DHCP Server, Web_1 (`www.dubai.com`) | Router1 |
| **LAN2** | 71.71.71.0/24 | 71.71.71.1 | DNS Server, Server-PT, PC-PT | Router2 |
| **LAN3** | 73.73.73.0/24 | 73.73.73.1 | Web_3 (`www.qjman.com`), PC (73.73.73.10), PC (73.73.73.20) | Router1 |
| **LAN4** | 72.72.72.0/24 | 72.72.72.1 | Web_2 (`www.alain.com`), PC (72.72.72.10), PC (72.72.72.20) | Router1 |
| **LAN5** | 74.74.74.0/24 | 74.74.74.1 / .2 | WAN Link (Router1 - Router2) | R1 & R2 |

*(Tip: Upload your screenshot of the topology to the repository and rename it to `topology.png`, then link it here: `![Network Topology](topology.png)`)*

## 🖥️ Services & Domains Configured
- **DHCP Server (LAN1):** Automatically assigns IP addresses to all PCs across all LANs using `ip helper-address` on the routers.
- **DNS Server (LAN2):** Resolves the following domains to their respective Web Server IPs:
  - `www.dubai.com` -> LAN1 Web Server
  - `www.alain.com` -> LAN4 Web Server
  - `www.qjman.com` -> LAN3 Web Server
- **Web Servers:** Host basic HTTP pages accessible via the DNS domain names.

## ⚙️ Routing & Configuration Highlights
To enable communication between the 4 distinct LANs, dynamic routing (OSPF or RIP v2) is configured on both routers. 

- **Router1** advertises LAN1 (70.70.70.0), LAN3 (73.73.73.0), LAN4 (72.72.72.0), and LAN5 (74.74.74.0).
- **Router2** advertises LAN2 (71.71.71.0) and LAN5 (74.74.74.0).

#Screenshot
<img width="1235" height="499" alt="image" src="https://github.com/user-attachments/assets/1e1b4195-bd00-4328-be77-9972e6f461d7" />


*Example OSPF Configuration snippet:*
```cisco
! On Router1
router ospf 1
 network 70.70.70.0 0.0.0.255 area 0
 network 72.72.72.0 0.0.0.255 area 0
 network 73.73.73.0 0.0.0.255 area 0
 network 74.74.74.0 0.0.0.255 area 0
