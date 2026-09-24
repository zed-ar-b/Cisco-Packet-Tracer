# Cisco-Packet-Tracer

- **Router1 (SchoolCenter)** connects to three LAN segments and one WAN link.
- **Router2 (HeadOffice)** connects to one LAN segment (Health Care) and the WAN link.

## 🌐 IP Addressing Scheme

| Device | Interface | IP Address | Subnet Mask | Gateway | Description |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Router1** | G0/0 | 192.168.1.1 | 255.255.255.128 | N/A | Accounting LAN |
| | G0/1 | 192.168.1.129 | 255.255.255.192 | N/A | Info Systems LAN |
| | G0/2 | 192.168.1.193 | 255.255.255.224 | N/A | Social Science LAN |
| | S0/0/0 | 192.168.10.1 | 255.255.255.0 | N/A | WAN link (DCE) |
| **Router2** | G0/0 | 192.168.2.1 | 255.255.255.128 | N/A | Health Care LAN |
| | S0/0/0 | 192.168.10.2 | 255.255.255.0 | N/A | WAN link (DTE) |
| **Switch1** | VLAN 1 | 192.168.1.2 | 255.255.255.128 | 192.168.1.1 | Accounting |
| **Switch2** | VLAN 1 | 192.168.1.130 | 255.255.255.192 | 192.168.1.129 | Info Systems |
| **Switch3** | VLAN 1 | 192.168.1.194 | 255.255.255.224 | 192.168.1.193 | Social Science |
| **Switch4** | VLAN 1 | 192.168.2.2 | 255.255.255.0 | 192.168.2.1 | Health Care |

> **Note:** Switch4 is configured with a /24 mask (`255.255.255.0`) while Router2 G0/0 uses /25 (`255.255.255.128`). This is per the provided scenario.

## 📋 Subnet Details

| Subnet | Network Address | Mask | Usable Range | Broadcast |
| :--- | :--- | :--- | :--- | :--- |
| Accounting | 192.168.1.0 | /25 | .1 – .126 | 192.168.1.127 |
| Info Systems | 192.168.1.128 | /26 | .129 – .190 | 192.168.1.191 |
| Social Science | 192.168.1.192 | /27 | .193 – .222 | 192.168.1.223 |
| Health Care | 192.168.2.0 | /25 | .1 – .126 | 192.168.2.127 |
| WAN Link | 192.168.10.0 | /24 | .1 – .254 | 192.168.10.255 |

## ⚙️ Device Configuration Summary

### Router1 (SchoolCenter)
- Hostname: `SchoolCenter`
- Enable secret: `123`
- Console password: `123`
- Service password-encryption enabled
- Banner MOTD configured
- Interfaces:
  - G0/0: 192.168.1.1/25
  - G0/1: 192.168.1.129/26
  - G0/2: 192.168.1.193/27
  - S0/0/0: 192.168.10.1/24 (clock rate 64000)
- RIP v2: `network 192.168.1.0`, `network 192.168.10.0`, `no auto-summary`

### Router2 (HeadOffice)
- Hostname: `HeadOffice`
- No IP domain lookup
- Enable secret: `123`
- Console password: `123`
- Service password-encryption enabled
- Banner MOTD configured
- Interfaces:
  - G0/0: 192.168.2.1/25
  - S0/0/0: 192.168.10.2/24
- RIP v2: `network 192.168.2.0`, `network 192.168.10.0`, `no auto-summary`

### Switches
All switches share the same security configuration (enable secret `123`, console password `123`, service password-encryption, banner MOTD) and have management IPs on VLAN 1 with default gateways pointing to the respective router interfaces.

## 🛠️ Requirements

- **Cisco Packet Tracer** version 8.0 or higher (recommended).
- Basic understanding of Cisco IOS commands.

## 🚀 How to Use

1. **Download** the file `Connection Between Headquarter and Health Care Management.pkt` from this repository.
2. **Open** it using Cisco Packet Tracer.
3. **Wait** for the network to converge (RIP updates may take a few seconds).
4. **Verify Connectivity**:
   - Click on any PC in the Accounting department.
   - Go to **Desktop > Command Prompt**.
   - Ping a device in another department, e.g., `ping 192.168.2.2` (Health Care switch).
   - You can also ping the routers: `ping 192.168.10.2` (HeadOffice serial).
5. **Check Routing Tables**:
   - On Router1, use `show ip route` to see RIP-learned routes.
   - On Router2, do the same.

## 🐛 Troubleshooting

| Problem | Possible Cause | Solution |
| :--- | :--- | :--- |
| PCs cannot ping across routers | RIP not configured or interfaces down | Check `show ip protocols` and `show ip interface brief` |
| Serial link down | Clock rate not set on DCE | Ensure `clock rate 64000` on Router1 S0/0/0 |
| Switch IP unreachable | Wrong gateway or VLAN 1 down | Verify `ip default-gateway` and `no shutdown` on VLAN 1 |
| Password issues | Console password not set | Check `line con 0` configuration |

## 📸 Screenshots
Output of: Connection Between Headquarter and Health Care Management
![image](https://github.com/user-attachments/assets/e548c02d-0b94-4e7c-91ce-539ac5398899)

