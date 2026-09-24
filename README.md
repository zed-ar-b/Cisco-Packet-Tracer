# Cisco Packet Tracer Projects

![Cisco](https://img.shields.io/badge/Cisco-Packet%20Tracer-blue)
![Projects](https://img.shields.io/badge/Projects-4-orange)
![License](https://img.shields.io/badge/License-Educational-lightgrey)

A collection of Cisco Packet Tracer network simulations and configurations.  
Each project is stored in its own folder and includes a `.pkt` file, a dedicated `README.md`, and any supporting resources.

## 📖 About

This repository serves as a portfolio of my networking projects built with **Cisco Packet Tracer**.  
Each folder contains a self-contained project with:
- The main `.pkt` file
- A detailed `README.md` explaining the scenario, topology, IP addressing, configurations, and testing steps

Use the links below to explore each project.

## 📂 Projects

| # | Project Name | Key Concepts | Folder | Project README |
|---|--------------|--------------|--------|----------------|
| 1 | **Headquarter & Health Care Management** | RIPv2, VLSM, Serial WAN, Switch Mgmt, Security | [📁 Folder](./Connection%20Between%20Headquarter%20and%20Health%20Care%20Management) | [📄 README](./Connection%20Between%20Headquarter%20and%20Health%20Care%20Management/README%20(2).md) |
| 2 | **Cisco 2911 Router WAN Topology** | Static Routing, Point-to-Point WAN, Subnetting | [📁 Folder](./cisco-2911-router-wan-topology) | [📄 README](./cisco-2911-router-wan-topology/README.md) |
| 3 | **Multi-LAN Enterprise Network** | DHCP, DNS, Email, Multi-LAN, OSPF | [📁 Folder](./cisco-multi-lan-enterprise-network) | [📄 README](./cisco-multi-lan-enterprise-network/README(3).md) |
| 4 | **UAE Regional DHCP/DNS Network** | Multi-Site Routing, DHCP Relay, DNS, Web Hosting | [📁 Folder](./packet-tracer-dhcp-dns-multi-lan-routing) | [📄 README](./packet-tracer-dhcp-dns-multi-lan-routing/README.md) |

---

### 🔍 Project Details

#### 1. Connection Between Headquarter and Health Care Management
- **Folder:** [`Connection Between Headquarter and Health Care Management`](./Connection%20Between%20Headquarter%20and%20Health%20Care%20Management)
- **Description:** Connects a school center with three departments (Accounting, Information Systems, Social Science) to a new Health Care Management department at the head office. 
- **Key Concepts:** RIPv2, VLSM, serial WAN link, switch management, basic device security.

#### 2. Cisco 2911 Router WAN Topology
- **Folder:** [`cisco-2911-router-wan-topology`](./cisco-2911-router-wan-topology)
- **Description:** A fundamental point-to-point WAN lab connecting two separate LANs using Cisco 2911 routers. Demonstrates IP subnetting and static routing.
- **Key Concepts:** IP Subnetting (`/24` LAN, `/30` WAN), Static Routing, Interface Configuration.

#### 3. Cisco Multi-LAN Enterprise Network
- **Folder:** [`cisco-multi-lan-enterprise-network`](./cisco-multi-lan-enterprise-network)
- **Description:** A comprehensive enterprise topology connecting multiple LANs and WAN links. Includes centralized DHCP, DNS, Web, and Email services.
- **Key Concepts:** OSPF Routing, DHCP (with IP Helper), DNS, Email Server (SMTP/POP3), Web Server.

#### 4. Packet Tracer DHCP DNS Multi-LAN Routing
- **Folder:** [`packet-tracer-dhcp-dns-multi-lan-routing`](./packet-tracer-dhcp-dns-multi-lan-routing)
- **Description:** Simulates a UAE regional enterprise network (Dubai, Al Ain, Qjman) with centralized DHCP and DNS services, alongside localized web servers for each branch.
- **Key Concepts:** Multi-Site Routing, Centralized DHCP/DNS, Domain Name Resolution, Web Hosting.

---

## 🛠️ Requirements

- **Cisco Packet Tracer** version **8.0** or higher (recommended).
- A computer capable of running Packet Tracer.

## 🚀 How to Use

1. **Clone or download** this repository.
2. Navigate to the folder of the project you want to explore.
3. Open the `.pkt` file with Cisco Packet Tracer.
4. Read the project's own `README.md` for scenario details, IP addressing, testing instructions, and troubleshooting tips.

## 📁 Repository Structure

```text
cisco-packet-tracer-projects/
├── README.md                                         # This main file
├── LICENSE
├── Connection Between Headquarter and Health Care Management/
│   ├── Connection Between Headquarter and Health Care Management.pkt
│   └── README (2).md
├── cisco-2911-router-wan-topology/
│   ├── cisco-2911-router-wan-topology.pkt
│   └── README.md
├── cisco-multi-lan-enterprise-network/
│   ├── cisco-packet-tracer-dhcp-dns-email-lab.pkt
│   └── README(3).md
└── packet-tracer-dhcp-dns-multi-lan-routing/
    ├── packet-tracer-dhcp-dns-multi-lan-routing.pkt
    └── README.md
