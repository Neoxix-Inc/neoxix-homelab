# Neoxix Homelab Architecture

## Purpose and scope

This document summarizes the current, sanitized architecture of the Neoxix personal homelab. It distinguishes validated infrastructure from work that is configured, under diagnosis, or planned. It does not describe a production, client, or highly available environment.

## Current architecture

The FortiGate 60F provides routing, firewall policy, VLAN segmentation, and DHCP. VMware ESXi 8.0 U3 runs on a Dell Precision T7910 and hosts the server and laboratory virtual machines. A Synology DS925+ provides network storage and hosts the Docker and Portainer environment. The Synology RAID layout is not documented because it has not been validated for publication.

Key systems include:

| Component | Role | Status |
|---|---|---|
| FortiGate 60F | Routing, firewall policy, DHCP, and VLAN segmentation | Operational and validated |
| Dell Precision T7910 with VMware ESXi 8.0 U3 | Virtual-machine host | Operational and validated |
| Synology DS925+ | Network storage and container host | Operational and validated |
| `DC01-HQ` | Windows Server 2025 domain controller and DNS server | Operational and validated |
| `DC02-BR2` | Windows Server 2025 domain controller and DNS server | Operational and validated |
| Wazuh on Ubuntu Server 22.04 under ESXi | Centralized monitoring and security telemetry | Deployed; improving |
| EVE-NG | Virtual network laboratory | Deployed; improving |
| TP-Link Omada TL-SG2218P | Planned managed switching and PoE | Planned |
| TP-Link Omada EAP670 | Planned wireless access | Planned |
| Omada Controller | Planned network management | Planned |

Proxmox is not part of the current operational architecture. Any future Proxmox work is planned learning and requires validation before it can be represented as deployed.

## Network segmentation

Ten VLAN interfaces are configured on the FortiGate, with corresponding ESXi port groups. Nine are operational and validated; VLAN 35 is configured but awaits documented end-to-end validation.

| VLAN | Name | Subnet | Purpose | Status |
|---:|---|---|---|---|
| 30 | BR1 | `10.30.0.0/24` | Branch-style laboratory segment | Operational and validated |
| 35 | BR2 | `10.35.0.0/24` | Branch-style laboratory segment | Configured; validation pending |
| 40 | HQ | `10.40.0.0/24` | Main user and workstation segment | Operational and validated |
| 50 | DC | `10.50.0.0/24` | Domain controllers and infrastructure services | Operational and validated |
| 60 | GUEST | `10.60.0.0/24` | Guest network | Operational and validated |
| 70 | VOIP | `10.70.0.0/24` | Voice network laboratory segment | Operational and validated |
| 80 | TEST/LAB | `10.80.0.0/24` | EVE-NG and technical laboratories | Operational and validated |
| 90 | MGMT | `10.90.0.0/24` | Infrastructure management | Operational and validated |
| 100 | IOT | `10.100.0.0/24` | IoT device segment | Operational and validated |
| 110 | SANDBOX | `10.110.0.0/24` | Controlled testing segment | Operational and validated |

VLAN names describe homelab functions and do not imply business sites or production workloads. The sandbox is segmented but is not described as air-gapped.

## Identity, storage, and monitoring

The `neoxix.local` Active Directory domain uses `DC01-HQ` and `DC02-BR2`. Active Directory and DNS replication are functional. DHCP is supplied by the FortiGate. OU design, security groups, permissions, Group Policy work, and domain-controller backup remain incomplete.

The Synology hosts the documented container environment. Service status varies from deployed and improving to installed with validation or configuration pending; installation alone is not treated as proof of operation.

Wazuh runs on Ubuntu Server 22.04 under ESXi. Six endpoint agents are connected: two Windows and four Linux. ESXi, FortiGate, and Synology also contribute agentless or Syslog telemetry. Monitoring capabilities are available, but no security incident has yet been fully investigated.

## Remote access and planned infrastructure

The IKEv2 remote-access VPN previously passed a test, was later stopped, and remains under diagnosis pending revalidation. It is not currently presented as operational.

The Omada TL-SG2218P, EAP670, and Omada Controller are planned. No operational Omada switching, trunking, or wireless design is claimed. Proxmox and associated infrastructure-as-code work are planned learning rather than current infrastructure.

## Limitations

This homelab has limited redundancy. Current documentation does not establish hypervisor failover, storage replication, or complete architecture-wide validation. Each component or workflow must be validated individually before its status is promoted.
