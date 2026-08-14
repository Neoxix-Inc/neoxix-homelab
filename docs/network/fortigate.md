# FortiGate 60F

## Current role

The FortiGate 60F provides routing, firewall policy, DHCP, and VLAN segmentation for the homelab. It is operational and validated for those functions. Hardware identifiers, external connectivity details, management endpoints, and complete configuration output are intentionally excluded.

## VLAN summary

Ten VLAN interfaces are configured, with corresponding ESXi port groups. Nine VLANs are operational and validated. VLAN 35 is configured but awaits documented end-to-end validation.

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

These private subnets are retained because they explain the documented segmentation design. Gateway addresses, management paths, and policy details are omitted.

## Monitoring integration

The FortiGate supplies security and network telemetry to Wazuh through Syslog. Destination addresses, ports, facilities, credentials, and full device configuration are not published here.

## Remote access

The IKEv2 remote-access VPN previously passed a test, was later stopped, and is under diagnosis pending revalidation. It is not currently presented as operational.

## Documentation boundary

Future configuration examples must be limited to the minimum required concept, sanitized before publication, and accompanied by validation evidence. Complete configuration exports are outside the scope of this repository documentation.
