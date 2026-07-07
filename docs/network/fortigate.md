# FortiGate 60F — FG60F-NEOXIX-HQ

## Information
| Parameter | Value |
|---|---|
| Model | FortiGate 60F |
| Serial | FGT60FTK20099XJ7 |
| Firmware | FortiOS 7.6.6 |
| Management IP | 192.168.2.254 |
| DC Interface | 10.50.0.1 (VLAN50) |

## Interfaces
| Name | IP | VLAN | Role |
|---|---|---|---|
| wan1 (BELL_WAN1) | 192.168.2.254 | Native | WAN |
| DC | 10.50.0.1/24 | 50 | Data Center |
| HQ | 10.40.0.1/24 | 40 | Headquarters |
| MGMT | 10.90.0.1/24 | 90 | Management |
| LAB | 10.80.0.1/24 | 80 | Lab |
| GUEST | 10.60.0.1/24 | 60 | Guest |
| VOIP | 10.70.0.1/24 | 70 | VoIP |
| BR1 | 10.30.0.1/24 | 30 | Branch 1 |
| BR2 | 10.35.0.1/24 | 35 | Branch 2 |

## Syslog
- Destination: 10.50.0.30:514 (Wazuh)
- Facility: local7
- Format: default

## VPN
- Neoxix-VPN (IKEv2 Remote Access)
