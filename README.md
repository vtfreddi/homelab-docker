# 🛡️ Cybersecurity Home Lab

This project documents the deployment and configuration of a comprehensive Home Lab environment designed for Cybersecurity study. The primary goal is to simulate a real-world enterprise network to execute Blue Team exercises (defense, monitoring, SIEM), deploy Honeypots, and conduct Red Team assessments (offensive VMs) to test security posture.

## 🎯 Project Goals
- **Infrastructure as Code:** Deploying services using Docker and Git version control.
- **Network Segmentation:** Proper VLAN implementation using enterprise gear (Cisco/Palo Alto).
- **Blue Team Ops:** Implementing SIEM (Wazuh), IDS/IPS (Suricata), and Netflow monitoring.
- **Identity Management:** Centralized authentication via Authentik.
- **Security Assessment:** continuous monitoring and security score improvement.

---

## 🏗️ Architecture & Status

### 🖥️ Hardware Inventory
- **Firewall:** Palo Alto PA-220
  - *IP:* `[Gateway IP]`
- **Switch:** Cisco SG200-08
  - *IP:* `[Switch IP]`
- **Hypervisor:** Dell Precision 7520 (Proxmox VE)
  - *IP:* `[Hypervisor IP]`

### 🔌 Switch Configuration (Cisco SG200-08)
| Port | Type | Description |
| :--- | :--- | :--- |
| **Eth1/1** | Trunk | Uplink to Palo Alto Firewall |
| **Eth1/2** | Trunk | Downlink to Proxmox Host |
| **Eth1/3** | Access | Firewall Management |
| **Eth1/6** | Access | User Desktop |
| **Eth1/7** | Access | Wireless Router/AP |
| **Eth1/8** | Span | Port Mirroring *(Planned)* |

---

## 🌐 Network Topology
The environment is segmented into strict VLANs to isolate management, servers, and lab traffic.

| Name | VLAN ID | Subnet | Description |
| :--- | :--- | :--- | :--- |
| **Management** | `[Mgmt ID]` | `10.x.x.x/24` | Network Infrastructure (FW, Switch, Proxmox) |
| **Servers** | `[Srv ID]` | `10.x.x.x/24` | Docker Hosts & Core Services |
| **DMZ** | `[DMZ ID]` | `10.x.x.x/24` | Exposed Services / Honeypots |
| **Lab** | `[Lab ID]` | `10.x.x.x/24` | Isolated Testing Environment |
| **Users** | `[User ID]` | `172.x.x.x/24` | Daily Driver Devices & WiFi |
| **WAN** | N/A | DHCP | ISP Connection |

---

## 🚀 Service Deployment (Docker Host 01)
**Host IP:** `[Server IP]`

### Core Infrastructure
- [x] **Portainer** - Container Management
- [x] **AdGuard Home** - DNS & AdBlocking
- [x] **Authentik** - SSO & Identity Management
    - [ ] LDAP Integration
- [ ] **Netbox** - IPAM & DCIM *(In Progress)*
- [x] **Homepage** - Dashboard

### Security & Monitoring Stack
- [ ] **Wazuh** - SIEM & XDR
- [ ] **Suricata** - IDS/IPS Network Monitoring
- [ ] **NTOPNG** - Traffic Analysis & Netflow
- [ ] **Smokeping** - Latency Monitoring

### Future Implementation (Phase 2)
- [ ] **Honeypots** (T-Pot or custom)
- [ ] **Red Team VM** (Kali/Parrot Security)
- [ ] **Automated Backups**

---

## 📝 Notes
