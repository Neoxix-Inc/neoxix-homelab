# Active Directory — neoxix.local

## Forest Information
| Parameter | Value |
|---|---|
| Forest Name | neoxix.local |
| Forest Level | Windows Server 2025 |
| Domain Level | Windows Server 2025 |
| PKI | Neoxix-Root-CA (ADCS Enterprise Root) |

## Domain Controllers
| Hostname | IP | Role | Site |
|---|---|---|---|
| DC1-HQ | 10.50.0.10 | PDC Emulator, RID Master, Schema Master | Default-First-Site-Name |
| DC02-BR2 | 10.50.0.11 | Additional DC, Global Catalog | Default-First-Site-Name |

## Replication Status
- Last verified: 2026-06-28
- Partitions replicated: 5/5
- Errors: 0

## PKI — ADCS
| Component | Value |
|---|---|
| CA Name | Neoxix-Root-CA |
| CA Type | Enterprise Root CA |
| Server | DC1-HQ.neoxix.local |
| Templates | VPN-Server, VPN-Client |

## DNS
| Zone | Type | Server |
|---|---|---|
| neoxix.local | Primary | DC1-HQ, DC02-BR2 |
| 50.10.in-addr.arpa | Reverse | DC1-HQ |

## Organizational Units
- OU=Servers,DC=neoxix,DC=local
- OU=Workstations,DC=neoxix,DC=local
- OU=Users,DC=neoxix,DC=local
- OU=Groups,DC=neoxix,DC=local
