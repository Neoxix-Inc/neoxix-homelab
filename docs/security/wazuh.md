# Wazuh SIEM — SRV-WAZUH

## Information
| Parameter | Value |
|---|---|
| Hostname | SRV-WAZUH |
| IP | 10.50.0.30/24 |
| OS | Ubuntu 22.04 LTS |
| Wazuh Version | 4.12.0 |
| Dashboard | https://10.50.0.30 |

## Components
| Component | Port | Status |
|---|---|---|
| wazuh-manager | 1514/tcp, 1515/tcp | Active |
| wazuh-indexer | 9200/tcp | Active |
| wazuh-dashboard | 443/tcp | Active |
| Syslog receiver | 514/udp | Active |

## Agents
| ID | Name | IP | OS | Group | Status |
|---|---|---|---|---|---|
| 001 | DC01-HQ | 10.50.0.10 | WS2025 | windows-servers | Active |
| 002 | DC02-BR2 | 10.50.0.11 | WS2025 | windows-servers | Active |
| 003 | Bastion | 10.90.0.99 | Ubuntu 22.04 | linux-servers | Active |
| 004 | SRV-FILE01 | 10.50.0.21 | WS2025 | windows-servers | Active |

## Syslog Sources
| Source | IP | Protocol | Status |
|---|---|---|---|
| FortiGate 60F | 10.50.0.1 | UDP/514 | Active |
| ESXi | 10.50.0.20 (vmk1) | UDP/514 | Active |
| NAS DS925+ | 10.50.0.5 | UDP/514 | Active |

## Credentials
- Dashboard: admin / (see password file)
- Wazuh API: wazuh / (see password file)
