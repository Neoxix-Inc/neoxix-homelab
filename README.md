# README.md — Neoxix Inc. GitHub Organization Profile

# Content to copy into GitHub

---

<div align="center">

<img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=700&size=28&pause=1000&color=2E75B6&center=true&vCenter=true&width=700&lines=NEOXIX+INC.;Network+%26+Infrastructure+Engineer;Day+0+to+Production" alt="Typing SVG" />

### Enterprise-Grade HomeLab · Day 0 to Production
### Gatineau, QC, Canada · Bilingual MSP Portfolio

[![FortiGate](https://img.shields.io/badge/FortiGate-60F_Perimeter-EE3124?style=for-the-badge&logo=fortinet&logoColor=white)](https://www.fortinet.com/)
[![VMware](https://img.shields.io/badge/ESXi-256_GB_RAM-607078?style=for-the-badge&logo=vmware&logoColor=white)](https://www.vmware.com/)
[![Synology](https://img.shields.io/badge/Synology-DS925%2B-4B9BD5?style=for-the-badge&logo=synology&logoColor=white)](https://www.synology.com/)
[![Docker](https://img.shields.io/badge/Docker-13_Containers-2496ED?style=for-the-badge&logo=docker&logoColor=white)](https://www.docker.com/)

[![FCF](https://img.shields.io/badge/Fortinet_FCF-✅_Oct_2025-00B140?style=for-the-badge)](https://www.fortinet.com/training/certification)
[![CCNA](https://img.shields.io/badge/CCNA_200--301-In_Progress_Jul_2026-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white)](https://www.cisco.com/c/en/us/training-events/training-certifications/certifications/associate/ccna.html)
[![NSE4](https://img.shields.io/badge/NSE4_FortiOS_7.6-In_Progress_Jul_2026-EE3124?style=for-the-badge)](https://www.fortinet.com/training/certification)

[![LinkedIn](https://img.shields.io/badge/LinkedIn-kodjo--akah-0077B5?style=flat-square&logo=linkedin)](https://linkedin.com/in/kodjo-akah)
[![Website](https://img.shields.io/badge/Web-neoxix.ca-0A2342?style=flat-square&logo=cloudflare)](https://neoxix.ca)
[![Email](https://img.shields.io/badge/Email-kodjo@neoxix.ca-EA4335?style=flat-square&logo=gmail)](mailto:kodjo@neoxix.ca)

</div>

---

## 🏢 About Neoxix Inc.

**Neoxix Inc.** is a bilingual MSP portfolio project built around a production-grade enterprise homelab — designed, deployed, and documented from scratch as a real client engagement.

Every component is treated as a production system: change management procedures, before/after audits, rollback plans, and full technical documentation. The goal is to demonstrate real-world infrastructure skills in the Ottawa-Gatineau market.

> *"Build it like it's production. Document it like it's a client."*

**Founder:** Kodjo Mathias Akah · Network & Infrastructure Engineer · 5+ years IT experience

---

## 🏗️ Infrastructure — Current State

### Physical Hardware

| Equipment | Model | Role | Status |
|-----------|-------|------|--------|
| **Perimeter Firewall** | FortiGate 60F | WAN + 802.1Q trunk | ✅ Active |
| **Lab Firewall** | FortiGate 200D | Internal lab segments | ✅ Active |
| **Hypervisor** | Dell T7910 #1 · 256 GB RAM | VMware ESXi 8 — primary | ✅ Active |
| **Workstation** | Dell T7910 #2 · 256 GB RAM | Labs, CLI, Proxmox VE | ✅ Active |
| **NAS** | Synology DS925+ | Storage, Docker, Backups | ✅ Active |
| **Switch** | TP-Link Omada TL-SG2218P | 16 PoE+ / 2 SFP · 802.1Q | ✅ Active |
| **WiFi** | TP-Link EAP670 | WiFi 6 — PoE+ | ✅ Active |
| **UPS** | CyberPower CP1000PFCLCD | Sinewave 1000VA — USB→NAS | ✅ Active |

### Network Architecture

```
                        ┌─────────────┐
                        │   INTERNET  │
                        │  Bell FTTH  │
                        └──────┬──────┘
                               │
                    ┌──────────┴──────────┐
                    │   FortiGate 60F     │
                    │   FG60F-NEOXIX-HQ  │
                    │   FortiOS 7.6.6    │
                    └──────────┬──────────┘
                               │ 802.1Q Trunk
                    ┌──────────┴──────────┐
                    │  Omada TL-SG2218P  │
                    │  16x PoE+ / 2 SFP  │
                    └──┬──┬──┬──┬──┬─────┘
                       │  │  │  │  │
          ┌────────────┘  │  │  │  └──────────────┐
          │               │  │  │                  │
    ┌─────┴──────┐   ┌────┴──┴──┴────┐     ┌──────┴──────┐
    │  ESXi #1   │   │  DS925+ NAS  │     │  EAP670 AP  │
    │  T7910     │   │  10.50.0.5   │     │  WiFi 6     │
    │  256 GB    │   │  Docker ×13  │     │  VLAN60     │
    └────────────┘   └──────────────┘     └─────────────┘
```

### VLAN Segmentation

| VLAN | ID | Subnet | Purpose | Status |
|------|----|--------|---------|--------|
| BR1 | 30 | 10.30.0.0/24 | Branch 1 site | ✅ |
| BR2 | 35 | 10.35.0.0/24 | Branch 2 site | ✅ |
| HQ | 40 | 10.40.0.0/24 | Headquarters workstations | ✅ |
| DC | 50 | 10.50.0.0/24 | Servers & services | ✅ |
| GUEST | 60 | 10.60.0.0/24 | Guest WiFi — isolated | ✅ |
| VOIP | 70 | 10.70.0.0/24 | VoIP lab | ✅ |
| LAB | 80 | 10.80.0.0/24 | EVE-NG labs | ✅ |
| MGMT | 90 | 10.90.0.0/24 | Management OOB | ✅ |
| IOT | 100 | 10.100.0.0/24 | IoT devices — isolated | ✅ |
| SANDBOX | 110 | 10.110.0.0/24 | Malware analysis — air-gapped | ✅ |

---

## 🖥️ Services — Deployment Status

### Core Infrastructure (ESXi)

| VM | Role | IP | Status |
|----|------|----|--------|
| DC01-HQ | Active Directory · DNS · DHCP | 10.50.0.10 | ✅ Active |
| EVE-NG | CCNA/NSE4 Labs (43 scenarios) | 10.80.0.10 | ✅ Active |
| DC02-BR2 | AD Replication | 10.50.0.11 | 🔄 In Progress |
| SRV-RADIUS | FreeRADIUS · 802.1X | 10.50.0.30 | 📋 Planned |
| SRV-WAZUH | Wazuh SIEM | 10.50.0.40 | 📋 Planned S5 |
| SRV-THEHIVE | TheHive + Cortex | 10.50.0.51 | 📋 Planned S5 |
| SRV-MISP | Threat Intelligence | 10.50.0.53 | 📋 Planned S6 |
| SRV-CAPE | CAPEv2 Malware Sandbox | 10.110.0.20 | 📋 Planned S6 |
| Bastion | Jump Host + MFA | 10.90.0.99 | 📋 Planned S4 |
| Proxmox VE | IaC Lab (Terraform) | 192.168.2.26 | 🔄 In Progress |

### Docker Stack (Synology DS925+)

| Container | Role | Status |
|-----------|------|--------|
| Portainer | Container management | ✅ Active |
| Guacamole | HTML5 remote access | ✅ Active |
| Nginx Proxy Manager | Reverse proxy + SSL | ✅ Active |
| Pi-hole | DNS · Ad blocking | ✅ Active |
| Uptime Kuma | Service monitoring | ✅ Active |
| Heimdall | Dashboard | ✅ Active |
| Omada Controller | WiFi management | ✅ Active |
| n8n | Workflow automation | ✅ Active |
| Grafana | Metrics visualization | ✅ Active |
| Prometheus | Metrics collection | ✅ Active |
| Zabbix | Infrastructure monitoring | ✅ Active |
| Odoo 18 | ERP | 📋 Planned S6 |
| GLPI | Helpdesk | 📋 Planned S6 |

---

## 🔬 EVE-NG Labs — 43 Documented Scenarios

<details>
<summary>📚 CCNA 200-301 Labs (click to expand)</summary>

- VLANs, Trunking, STP, RSTP
- OSPF Single-Area & Multi-Area
- EIGRP & Route Redistribution
- BGP basics & eBGP peering
- NAT/PAT, ACLs, IPv6
- DHCP, DNS, NTP configuration
- WAN technologies, QoS
- Network automation with Python + Netmiko

</details>

<details>
<summary>🔒 NSE4 FortiGate 7.x Labs (click to expand)</summary>

- FortiGate initial setup & interface config
- Firewall policies & Security Profiles
- VPN IPsec Site-to-Site & SSL VPN
- VLAN segmentation & inter-VLAN routing
- IDS/IPS, Web Filtering, App Control
- HA Clustering (Active-Passive)
- FortiGate REST API automation

</details>

---

## 🛠️ Automation & IaC

```bash
# Repo structure (in progress)
neoxix-homelab/
├── ansible/          # Playbooks — OS config, AD join, service deploy
├── terraform/        # Proxmox VM provisioning (Telmate provider v3.x)
├── python/           # FortiGate REST API scripts, NetOps tools
├── fortigate/        # FortiGate 60F config exports (sanitized)
├── eve-ng/           # Lab topologies + scenario docs
├── docker/           # docker-compose files for DS925+
└── docs/             # Architecture diagrams (Draw.io)
```

---

## 📜 Certifications

| Certification | Issuer | Date | Status |
|--------------|--------|------|--------|
| **Fortinet Certified Fundamentals (FCF)** | Fortinet | Oct 2025 | ✅ Obtained |
| **CCNA 200-301** | Cisco | Jul 2026 (target) | 📖 Studying |
| **NSE4 — Network Security Professional** | Fortinet | Jul 2026 (target) | 📖 Studying |

---

## 📊 Tech Stack

**Networking:** FortiGate · Cisco IOS · VLAN/802.1Q · OSPF · BGP · IPsec VPN · 802.1X RADIUS · TP-Link Omada

**Virtualization:** VMware ESXi 8 · VMware vSphere · EVE-NG · GNS3 · Synology DSM · iSCSI · NFS

**Systems:** Windows Server 2022/2019 · Active Directory · GPO · Linux (Ubuntu · Rocky) · PowerShell

**Security:** Wazuh SIEM · TheHive · Cortex · MISP · CAPEv2 · PKI/CA · Zero Trust segmentation

**Automation:** Ansible · Python · Terraform · Git · Docker · REST API (FortiGate)

**Monitoring:** Grafana · Prometheus · Zabbix · Uptime Kuma · Pi-hole

---

## 📬 Contact

**Kodjo Mathias Akah** — Network & Infrastructure Engineer
Founder, Neoxix Inc. · Gatineau, QC, Canada

| | |
|-|-|
| 🌐 **Web** | [neoxix.ca](https://neoxix.ca) |
| 💼 **LinkedIn** | [linkedin.com/in/kodjo-akah](https://linkedin.com/in/kodjo-akah) |
| 📧 **Email** | [kodjo@neoxix.ca](mailto:kodjo@neoxix.ca) |
| 📞 **Phone** | 873-354-2056 |

---

<div align="center">

*Building real infrastructure. Documenting everything.*
*Open to Network Administrator · Infrastructure Engineer · Junior SOC Analyst roles in Ottawa-Gatineau.*

![Visitors](https://visitor-badge.laobi.icu/badge?page_id=neoxix-inc.neoxix-inc)

</div>
