# NEOXIX HomeLab — Architecture Documentation

## 📐 Architecture Overview

The NEOXIX homelab is designed as an enterprise-grade infrastructure for hands-on Network & Security Engineering practice. It combines multiple hypervisors, firewall appliances, and containerized services across 10 VLANs for complete network segmentation.

---

## 🏗️ High-Level Topology

\\\
┌─────────────────────────────────────────────────────────┐
│                    ISP Gateway (Bell)                   │
│              192.168.2.1 (DHCP + Internet)              │
└────────────────────┬────────────────────────────────────┘
                     │ WAN Link (Dynamic IP)
        ┌────────────▼────────────────┐
        │     FortiGate 60F            │
        │    192.168.2.254             │
        │  (Firewall, VPN, NAT)        │
        └────────────┬─────────────────┘
                     │ LAN Port
        ┌────────────▼──────────────────┐
        │  TP-Link Omada TL-SG2218P     │
        │  (Managed Switch + VLAN Trunk)│
        │  172.27.0.0/24 (Management)   │
        └────────┬───────────┬──────────┘
                 │           │
         ┌───────▼──┐   ┌────▼──────┐
         │  Dell    │   │ Synology  │
         │ T7910    │   │ DS925+    │
         │192.168.  │   │10.50.0.5  │
         │2.13      │   │(NAS)      │
         │(ESXi 8)  │   │           │
         │          │   │ Docker:   │
         │VMs:      │   │ -Guacamole│
         │-DC01     │   │ -Omada    │
         │-Bastion  │   │ -Others   │
         └──────────┘   └───────────┘
               │
         ┌─────▼──────────┐
         │ Proxmox VE     │
         │ (on Workstation│
         │  Pro VM)       │
         │ 192.168.2.26   │
         │ Bridge: vmbr0  │
         └────────────────┘
\\\

---

## 🔗 VLAN Architecture

### VLAN Design Rationale

The network uses 10 segregated VLANs to achieve:
- **Security:** Isolate trust domains (management, lab, guest)
- **Scalability:** Room for multiple branch/site simulations
- **Compliance:** Separate sensitive services (VOIP, management)
- **Lab Flexibility:** Independent network scenarios (BR1, BR2, sandbox)

### VLAN Details

| VLAN | Name | Subnet | Gateway | Purpose | Devices |
|------|------|--------|---------|---------|---------|
| 1 | Default | 192.168.2.0/24 | 192.168.2.1 | ISP + Management | FG60F, T7910, Proxmox, iPad |
| 30 | BR1 | 10.30.0.0/24 | 10.30.0.1 | Branch 1 Lab | VM Lab instances |
| 35 | BR2 | 10.35.0.0/24 | 10.35.0.1 | Branch 2 Lab | VM Lab instances |
| 40 | HQ | 10.40.0.0/24 | 10.40.0.1 | Headquarters | DC01, servers |
| 50 | DC | 10.50.0.0/24 | 10.50.0.1 | Data Center | DS925+ (10.50.0.5) |
| 60 | GUEST | 10.60.0.0/24 | 10.60.0.1 | Guest Network | Guest VMs, visitor WiFi |
| 70 | VOIP | 10.70.0.0/24 | 10.70.0.1 | Voice Services | Phone systems, SIP |
| 80 | LAB | 10.80.0.0/24 | 10.80.0.1 | Network Labs | EVE-NG (10.80.0.10) |
| 90 | MGMT | 10.90.0.0/24 | 10.90.0.1 | Management/Bastion | Bastion SSH (10.90.0.99) |
| 100 | IOT | 10.100.0.0/24 | 10.100.0.1 | IoT Devices | Smart home, sensors |
| 110 | SANDBOX | 10.110.0.0/24 | 10.110.0.1 | Experimental | Temporary testing |

---

## 💻 Core Infrastructure Components

### FortiGate 60F (Primary Firewall)
\\\
Device: FortiGate 60F
Firmware: FortiOS 7.6.6
IP Address: 192.168.2.254
Interface:
  - WAN: DHCP (ISP Gateway)
  - LAN: 192.168.2.254/24 (Omada Switch)
Management:
  - GUI: https://192.168.2.254 (admin/admin)
  - SSH: admin@192.168.2.254 (port 22)
Services:
  - Firewall rules (10 VLANs)
  - DHCP Server (5 scopes: VLAN 40, 50, 80, 90, 100)
  - NTP Server (internal)
  - SSL VPN (certificate-based)
  - IPsec VPN (ISP NAT issue — workaround: Bastion SSH)
\\\

### Dell PowerEdge T7910 (Primary Hypervisor)
\\\
Device: Dell T7910
Hypervisor: VMware ESXi 8.0
IP Address: 192.168.2.13 (VM console)
Datastore: Synology iSCSI (10.50.0.5:3260)
VMs Deployed: 29 permanent + 4 sandbox
Key VMs:
  - DC01-HQ: Windows Server 2022 (AD, DNS, DHCP)
  - Bastion: Ubuntu 22.04 (SSH + MFA gateway)
  - EVE-NG: Network simulation lab environment
  - Lab VMs: 25+ for testing/training
Storage: Synology DS925+ via iSCSI
\\\

### Proxmox VE (Secondary Hypervisor)
\\\
Device: VM on VMware Workstation Pro
Hypervisor: Proxmox VE 8.x
IP Address: 192.168.2.26
Network: vmbr0 bridge (vlan 1 default)
  - Bridge Port: nic0 (VMware virtual NIC)
  - Static IP: 192.168.2.26/24
  - Gateway: 192.168.2.1
Web UI: https://192.168.2.26:8006 (root)
SSH: ssh root@192.168.2.26
Status: ✅ Networking repaired (June 18, 2026)
Planned VMs:
  - DC02-BR2: Domain controller for BR2 lab
  - SRV-FILE01: File server (DFS testing)
\\\

### Synology DS925+ (NAS + Docker Host)
\\\
Device: Synology DS925+
IP Address: 10.50.0.5 (VLAN 50 DC)
NAS Services:
  - iSCSI Datastore (for ESXi, Proxmox)
  - NFS Exports (lab VMs)
  - Backup storage (RAID 6)
Docker Services:
  - Guacamole 1.5.4 (RDP gateway) — Port 8080
  - Omada Controller 5.x (WiFi management)
  - Portainer (container UI) — Port 9000
  - PostgreSQL 15 (database)
  - Wazuh (SIEM — deploying)
Management: Portainer @ http://10.50.0.5:9000
SSH: admin@10.50.0.5
\\\

### TP-Link Omada TL-SG2218P (Switch)
\\\
Device: TP-Link Omada TL-SG2218P
IP Address: 172.27.0.0/24 (management VLAN)
Ports: 18 Gigabit + 2 SFP uplinks
VLAN Trunk: Port 1-17 (tagged for all 10 VLANs)
Uplink: Port 18 to FortiGate LAN
WiFi Controller: Omada EAP650 (WiFi 6)
Features:
  - Per-VLAN port assignment
  - RSTP (spanning tree)
  - QoS per VLAN
  - Management IP: Discovered by Omada Controller
\\\

---

## 🔐 Security Architecture

### Trust Domains

\\\
┌─────────────────────────────────────────┐
│         UNTRUSTED (Internet)            │
└──────────────┬──────────────────────────┘
               │ FortiGate Firewall
┌──────────────▼──────────────────────────┐
│    SEMI-TRUSTED (Default VLAN 1)        │
│   - Management access                   │
│   - Admin tools (Portainer, Proxmox)    │
└──────────────┬──────────────────────────┘
               │ Internal Firewall Rules
      ┌────────┴────────────────┬─────────────────────┐
      │                         │                     │
┌─────▼──────┐  ┌──────────┐  ┌───────▼────┐  ┌──────▼─────┐
│ DATA (DC)  │  │ GUEST    │  │ LAB (EVE-NG)│  │ SANDBOX    │
│ VLAN 50    │  │ VLAN 60  │  │ VLAN 80    │  │ VLAN 110   │
│ Production │  │ Visitors │  │ Education  │  │ Testing    │
└────────────┘  └──────────┘  └────────────┘  └────────────┘
\\\

---

## 🌐 Networking Details

### Routing Architecture

\\\
Destination       | Next Hop          | Via
------------------|-------------------|------------------
192.168.2.0/24    | Direct            | LAN interface
10.30.0.0/24      | 192.168.2.254 (FG)| FortiGate VLAN 30
10.35.0.0/24      | 192.168.2.254 (FG)| FortiGate VLAN 35
10.40.0.0/24      | 192.168.2.254 (FG)| FortiGate VLAN 40
10.50.0.0/24      | 192.168.2.254 (FG)| FortiGate VLAN 50
10.60.0.0/24      | 192.168.2.254 (FG)| FortiGate VLAN 60
10.70.0.0/24      | 192.168.2.254 (FG)| FortiGate VLAN 70
10.80.0.0/24      | 192.168.2.254 (FG)| FortiGate VLAN 80
10.90.0.0/24      | 192.168.2.254 (FG)| FortiGate VLAN 90
10.100.0.0/24     | 192.168.2.254 (FG)| FortiGate VLAN 100
10.110.0.0/24     | 192.168.2.254 (FG)| FortiGate VLAN 110
0.0.0.0/0         | 192.168.2.1 (ISP) | Default gateway
\\\

---

## 📊 Network Utilization

| VLAN | Purpose | Current Load | Growth Room |
|------|---------|--------------|-------------|
| VLAN 1 (Default) | Management | Medium | Limited to 5 devices |
| VLAN 40 (HQ) | Production | Low (2 VMs) | 254 devices |
| VLAN 50 (DC) | NAS + services | Medium | 254 devices |
| VLAN 80 (LAB) | EVE-NG + labs | Medium (43 scenarios) | 254 devices |
| VLAN 90 (MGMT) | Bastion + admin | Low (1 VM) | 254 devices |
| Others | Reserved | Low | Future expansion |

---

## 🔧 Failover & Redundancy

### Current State
- **Single Firewall:** FortiGate 60F (no HA pair)
- **Single NAS:** Synology DS925+ (RAID 6 protection)
- **Dual Hypervisors:** ESXi (primary) + Proxmox (secondary)
- **Backup Strategy:** Manual snapshots (Synology)

### Future Improvements
- [ ] FortiGate HA pair (60F + spare)
- [ ] Synology replication to secondary NAS
- [ ] VMware vSAN for VM replication
- [ ] Automated backup orchestration (Veeam)

---

**Last Updated:** June 18, 2026  
**Architecture Version:** 8.2  
**Confidence Level:** ✅ Verified from live infrastructure
