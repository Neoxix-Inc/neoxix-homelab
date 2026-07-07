## Inventory

| Hostname | IP | OS | Role | VLAN |
|---|---|---|---|---|
| FG60F-NEOXIX-HQ | 192.168.2.254 | FortiOS 7.6.6 | Firewall/Router | Native |
| esxi.neoxix.local | 10.90.0.10 | ESXi 8.0 | Hypervisor | MGMT |
| NX-Cloud | 10.50.0.5 | DSM 7.x | NAS/Docker | DC |
| DC1-HQ | 10.50.0.10 | WS2025 | AD DC Primary | DC |
| DC02-BR2 | 10.50.0.11 | WS2025 | AD DC Secondary | DC |
| SRV-FILE01 | 10.50.0.21 | WS2025 | File Server/DFS | DC |
| SRV-WAZUH | 10.50.0.30 | Ubuntu 22.04 | SIEM | DC |
| Bastion | 10.90.0.99 | Ubuntu 22.04 | Jump Host | MGMT |
| EVE-NG | 10.80.0.10 | Ubuntu 22.04 | Network Lab | LAB |
| Proxmox | 192.168.2.26 | PVE 9.1.1 | Hypervisor | Native |

## Hardware

| Device | Model | Specs |
|---|---|---|
| Firewall | FortiGate 60F | FortiOS 7.6.6 |
| ESXi Server | Dell T7910 | 12x Xeon E5-2667 v4, 256 GB RAM |
| NAS | Synology DS925+ | 5x HDD, Btrfs RAID5 |
| Switch | Omada SG2428P | 24x PoE+ |
| WiFi | TP-Link EAP650 x2 | WiFi 6 |
