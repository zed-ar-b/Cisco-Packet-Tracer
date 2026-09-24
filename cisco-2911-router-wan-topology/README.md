# Cisco Point-to-Point WAN Routing Lab

**Author:** Zunaira Rashid  
**Tool Used:** Cisco Packet Tracer  
**Project Type:** Basic Routing & WAN Connectivity Lab

## 📖 Overview
This project demonstrates a fundamental network topology built in Cisco Packet Tracer. It simulates connecting two separate Local Area Networks (LANs) over a Wide Area Network (WAN) link using two Cisco 2911 routers. 

The lab focuses on:
- IP subnetting (using a `/24` for LANs and `/30` for the WAN link).
- Interface configuration on Cisco routers and switches.
- Enabling communication between two distinct networks (Routing).

## 🗺️ Network Topology
The topology consists of two sites connected via a serial-like point-to-point link:

- **Left Site (LAN 1):**
  - 1x PC-PT (IP: `192.168.12.10/24`)
  - 1x Switch (2960-24TT)
  - 1x Router (2911) - **Router1**
- **WAN Link:**
  - Point-to-point connection between Router1 and Router2 using a `/30` subnet.
- **Right Site (LAN 2):**
  - 1x Server-PT (IP: `10.0.12.100/24`)
  - 1x Switch (2960-24TT)
  - 1x Router (2911) - **Router2**

*(Tip: Upload your screenshot of the topology to the repository and rename it to `topology.png`, then link it here: `![Network Topology](topology.png)`)*

## 🌐 IP Addressing Scheme

| Device | Interface | IP Address | Subnet Mask | Description |
| :--- | :--- | :--- | :--- | :--- |
| **PC-PT** | NIC | 192.168.12.10 | 255.255.255.0 | Default Gateway: 192.168.12.1 |
| **Router1** | Gig0/1 | 192.168.12.1 | 255.255.255.0 | LAN 1 Gateway |
| **Router1** | Gig0/0 | 172.16.12.1 | 255.255.255.252 | WAN Link (DCE side) |
| **Router2** | Gig0/0 | 172.16.12.2 | 255.255.255.252 | WAN Link (DTE side) |
| **Router2** | Gig0/1 | 10.0.12.1 | 255.255.255.0 | LAN 2 Gateway |
| **Server-PT**| NIC | 10.0.12.100 | 255.255.255.0 | Default Gateway: 10.0.12.1 |

## ⚙️ Configuration Highlights

To make this network functional, the following configurations were applied:

1.  **Interface Configuration:**
    - Configured Gigabit Ethernet interfaces on both routers with the IPs listed above.
    - Applied `no shutdown` to all active interfaces.
    - *Note: If using a Serial connection instead of Gigabit, the DCE side (Router1) requires the `clock rate 64000` command.*

2.  **Routing:**
    - Since there are only two routers and two remote networks, **Static Routing** (or a simple single-area OSPF) was used.
    - **Router1** needs a route to `10.0.12.0/24` pointing to `172.16.12.2`.
    - **Router2** needs a route to `192.168.12.0/24` pointing to `172.16.12.1`.

    *Example Static Route Configuration:*
    ```cisco
    ! On Router1
    ip route 10.0.12.0 255.255.255.0 172.16.12.2

    ! On Router2
    ip route 192.168.12.0 255.255.255.0 172.16.12.1

  #Screenshot
  <img width="977" height="366" alt="image" src="https://github.com/user-attachments/assets/ced56d26-95c9-49e2-8f28-7ac6057adc14" />
