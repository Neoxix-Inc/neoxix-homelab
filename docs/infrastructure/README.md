# Infrastructure Inventory

This inventory follows the status definitions and validated baseline in the repository README. Exact management endpoints and unsupported hardware specifications are intentionally omitted.

## Current systems

| Component | Platform or role | Status and limitation |
|---|---|---|
| Dell Precision T7910 | VMware ESXi 8.0 U3 virtual-machine host | Operational and validated; single-host lab environment |
| Synology DS925+ | Network storage and container host | Operational and validated; RAID layout not validated for publication |
| FortiGate 60F | Routing, firewall policy, DHCP, and VLAN segmentation | Operational and validated; single firewall |
| `DC01-HQ` | Windows Server 2025 domain controller and DNS server | Operational and validated; no domain-controller backup currently available |
| `DC02-BR2` | Windows Server 2025 domain controller and DNS server | Operational and validated; no domain-controller backup currently available |
| Wazuh | Ubuntu Server 22.04 VM under ESXi | Deployed; improving — no incident fully investigated yet |
| EVE-NG | Virtual network laboratory | Deployed; improving — scenarios remain progressive work |
| Docker and Portainer | Synology container environment | Deployed; improving — individual service maturity varies |
| FortiGate 200D | Physical firewall laboratory platform | Non-functional |
| Sophos XG VM | Virtual firewall laboratory platform | Installed; validation pending |
| pfSense CE VM | Virtual firewall laboratory platform | Tested lab platform |

`SRV-FILE01`, a bastion host, and Proxmox are not listed as operational infrastructure because the authoritative baseline does not establish them as deployed and validated.

## Planned equipment

| Component | Intended role | Status |
|---|---|---|
| TP-Link Omada TL-SG2218P | Managed wired switching, PoE, and VLAN connectivity | Planned |
| TP-Link Omada EAP670 | Wireless connectivity | Planned |
| Omada Controller | Omada network management | Planned |

Planned equipment is not presented as installed, connected, or validated.
