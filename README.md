# Neoxix Homelab

Personal technical homelab and portfolio project maintained by **Kodjo Mathias Akah**, an IT Technician focused on technical support, systems, networking, and junior infrastructure. The environment is used to build, operate, troubleshoot, and document infrastructure skills in a controlled setting. It is not a production MSP environment or a client engagement.

## Status legend

| Status | Meaning |
|---|---|
| Operational and validated | Deployed and confirmed to perform the stated function |
| Configured; validation pending | Present on the relevant infrastructure, but awaiting documented end-to-end validation |
| Deployed; improving | Running, with configuration, documentation, or coverage still being refined |
| Under diagnosis | Implemented or configured, but not yet confirmed fully operational |
| Planned | Future learning or laboratory work; not presented as current capability |
| In progress | Work or study that has started but is not complete |
| In preparation | Certification study underway; certification not yet obtained |
| Planned learning and future labs | Roadmap topic not presented as a current operational capability |
| Inventory only | Recorded hardware that is present without a claim of validated operation |
| Lab platform | Equipment or software available for controlled laboratory use |

## Overview

This repository documents a segmented homelab built around VMware ESXi, Windows Server, Fortinet networking, Synology storage and containers, infrastructure monitoring, and an EVE-NG virtual networking lab. Its purpose is to demonstrate practical IT support and infrastructure work through accurate inventories, repeatable procedures, troubleshooting records, and evidence-based lab reports.

The repository will progressively contain network diagrams, operating procedures, validated lab reports, troubleshooting records, and sanitized configuration examples. Configurations and screenshots will be reviewed and sanitized before publication to remove credentials, tokens, public IP addresses, serial numbers, and other sensitive data.

## Current infrastructure

| Component | Platform | Role | Status |
|---|---|---|---|
| Hypervisor | Dell Precision T7910, 256 GB RAM; VMware ESXi 8.0 U3 | Hosts server and laboratory virtual machines | Operational and validated |
| NAS | Synology DS925+ | Network storage and container host | Operational and validated |
| Firewall | FortiGate 60F; FortiOS 7.6.x | Routing, firewall policy, and VLAN segmentation | Operational and validated |
| Managed switch | TP-Link Omada TL-SG2218P PoE | Wired switching, PoE, and VLAN connectivity | Operational and validated |
| Wireless access point | TP-Link Omada EAP670 Wi-Fi 6 | Wireless connectivity | Operational and validated |
| UPS | CyberPower CP1000PFCLCD | Power protection | Inventory only |
| Virtual network lab | EVE-NG at `10.80.0.10` | Progressive CCNA and Fortinet laboratories | Deployed; improving |
| Additional firewall labs | FortiGate 200D, Sophos XG VM, pfSense CE VM | Isolated firewall configuration and testing platforms | Lab platform |

## Network segmentation

The FortiGate and ESXi infrastructure is configured for the following ten private IPv4 VLAN segments. Eight are operational and validated; VLANs 35 and 70 are configured on the relevant infrastructure but await documented end-to-end validation. VLAN names describe their intended homelab function and do not imply a production business environment.

| VLAN | Name | Subnet | Purpose | Status |
|---:|---|---|---|---|
| 30 | BR1 | `10.30.0.0/24` | Branch-style laboratory segment | Operational and validated |
| 35 | BR2 | `10.35.0.0/24` | Branch-style laboratory segment | Configured; validation pending |
| 40 | HQ | `10.40.0.0/24` | Main user and workstation segment | Operational and validated |
| 50 | DC | `10.50.0.0/24` | Domain controllers and infrastructure services | Operational and validated |
| 60 | GUEST | `10.60.0.0/24` | Guest network | Operational and validated |
| 70 | VOIP | `10.70.0.0/24` | Voice network laboratory segment | Configured; validation pending |
| 80 | TEST/LAB | `10.80.0.0/24` | EVE-NG and technical laboratories | Operational and validated |
| 90 | MGMT | `10.90.0.0/24` | Infrastructure management | Operational and validated |
| 100 | IOT | `10.100.0.0/24` | IoT device segment | Operational and validated |
| 110 | SANDBOX | `10.110.0.0/24` | Controlled testing segment | Operational and validated |

The sandbox is a segmented test network; it is not described as air-gapped.

## Core systems and services

### Active Directory and DNS

| System | Address | Role | Status |
|---|---|---|---|
| `DC1-HQ` | `10.50.0.10` | Windows Server 2025 domain controller and DNS server | Operational and validated |
| `DC02-BR2` | `10.50.0.11` | Windows Server 2025 domain controller and DNS server | Operational and validated |

The Active Directory domain is `neoxix.local`. Active Directory and DNS replication between both domain controllers is functional.

### Synology container environment

Docker and Portainer are used on the Synology environment. The deployed service set includes:

| Service | Function | Status |
|---|---|---|
| Nginx Proxy Manager | Reverse-proxy management | Deployed; improving |
| n8n | Workflow automation platform | Deployed; improving |
| Omada Controller | Omada network management | Operational and validated |
| Uptime Kuma | Service availability monitoring | Deployed; improving |
| Pi-hole | DNS filtering | Deployed; improving |
| Heimdall | Service dashboard | Deployed; improving |
| Guacamole | Browser-based remote access | Deployed; improving |
| Zabbix | Infrastructure monitoring | Deployed; improving |
| Grafana | Monitoring visualization | Deployed; improving |

The status `Deployed; improving` confirms that a service exists and is in use without claiming that every integration, alert, dashboard, or operational procedure is complete.

## Monitoring and security

Wazuh is deployed on Ubuntu Server 22.04 and is being used for centralized monitoring and security telemetry.

| Capability | Current state | Status |
|---|---|---|
| Endpoint agents | Six connected agents | Operational and validated |
| Syslog collection | FortiGate, ESXi, and Synology sources | Operational and validated |
| File Integrity Monitoring (FIM) | Enabled | Operational and validated |
| Security Configuration Assessment (SCA) | Enabled | Operational and validated |
| Vulnerability detection | Enabled | Operational and validated |
| Email alerts | Configured and functioning | Operational and validated |

This deployment demonstrates monitoring configuration and log centralization. It does not represent a production security operations centre, and no completed incident investigations are claimed.

An IKEv2 remote-access VPN is configured but remains **under diagnosis**. It is not presented as a fully operational remote-access service.

## Virtual networking lab

EVE-NG is deployed at `10.80.0.10` to support progressive CCNA 200-301 and Fortinet FortiOS laboratories. The environment provides a place to build, test, troubleshoot, and document network topologies and firewall configurations.

Installed images or available platforms are not treated as evidence of mastery. Individual scenarios will be described as completed only after their objectives, configurations, validation steps, results, and troubleshooting notes have been documented.

Current laboratory platforms include EVE-NG, a FortiGate 200D, a Sophos XG virtual machine, and a pfSense CE virtual machine.

## Skills demonstrated

The validated environment provides practical evidence of:

- Hardware inventory and basic infrastructure lifecycle management.
- VMware ESXi virtual-machine hosting and administration.
- Windows Server 2025, Active Directory Domain Services, DNS, and replication validation.
- IPv4 subnetting, VLAN segmentation, managed switching, Wi-Fi, and firewall policy administration.
- FortiGate and FortiOS configuration in an operational homelab.
- Synology NAS administration and Docker service management with Portainer.
- Centralized monitoring, Syslog collection, endpoint agents, FIM, SCA, vulnerability detection, and alerting with Wazuh.
- Service monitoring and visualization using Uptime Kuma, Zabbix, and Grafana.
- Structured troubleshooting, technical documentation, change awareness, and secure publication practices.

These are homelab-based capabilities and do not imply professional client delivery or production-scale experience.

## Learning roadmap

| Area | Planned work | Status |
|---|---|---|
| Cisco networking | Progressive CCNA 200-301 labs covering the published exam objectives | In progress |
| Fortinet administration | FortiOS 7.6 administration studies and additional firewall labs after CCNA | Planned |
| VPN troubleshooting | Diagnose and validate the IKEv2 remote-access implementation | Under diagnosis |
| Automation and infrastructure as code | Python, Netmiko, Paramiko, Ansible, Terraform, APIs, and Postman | Planned learning and future labs |
| Cloud and endpoint administration | Microsoft 365, Entra ID, Intune, Azure, Sentinel, Defender XDR, and KQL | Planned learning and future labs |
| Security and packet analysis | Nmap, Zenmap, Wireshark, and Splunk | Planned learning and future labs |
| Containers and orchestration | Kubernetes and advanced container operations | Planned learning and future labs |
| Documentation | Sanitized diagrams, procedures, lab reports, configuration examples, and troubleshooting records | In progress |

Roadmap entries are learning goals, not claims of operational proficiency.

## Certifications

### Obtained

| Certification | Issuer | Date obtained |
|---|---|---|
| Fortinet Certified Fundamentals in Cybersecurity | Fortinet | October 2025 |
| Fortinet NSE 1 Certified in Cybersecurity | Fortinet | October 2025 |
| Fortinet NSE 2 Certified in Cybersecurity | Fortinet | October 2025 |

### In preparation

| Certification | Target | Status |
|---|---|---|
| Cisco CCNA 200-301 | Exam planned for September 30, 2026 | In preparation |
| Fortinet NSE 4 / FortiOS 7.6 Administrator | Planned after CCNA | Planned |

CCNA and NSE 4 are not held certifications.

## Documentation and security practices

- Record the purpose, prerequisites, implementation steps, validation method, results, and rollback considerations for documented changes.
- Separate confirmed operating state from installed software, work in progress, troubleshooting, and planned work.
- Sanitize configurations, logs, screenshots, and diagrams before publication.
- Exclude passwords, tokens, private keys, public IP addresses, serial numbers, and other identifying or security-sensitive values.
- Use private addresses only where they clarify the lab design and do not expose external access details.
- Update documentation when validation changes the known state of the environment.

## Current limitations

- This is a personal homelab with limited redundancy and is not a production, enterprise, MSP, or client environment.
- The IKEv2 remote-access VPN is under diagnosis.
- EVE-NG scenarios are being developed progressively; no fixed number of completed or documented scenarios is claimed.
- Deployed services may still need stronger documentation, alert tuning, backup testing, access review, and recovery validation.
- Technologies listed in the learning roadmap are not presented as mastered or operational without direct evidence.
- Repository documentation is being refreshed; older supporting documents may contain stale or unvalidated details until they are reviewed separately.
