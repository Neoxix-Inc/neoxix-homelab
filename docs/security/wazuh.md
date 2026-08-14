# Wazuh Monitoring

## Current state

Wazuh runs on an Ubuntu Server 22.04 virtual machine under VMware ESXi. It provides centralized monitoring and security telemetry for the homelab. Exact management endpoints, account names, credentials, software versions, ports, and credential-storage details are intentionally omitted.

## Endpoint agents

Six endpoint agents are connected:

| Endpoint type | Connected agents | Status |
|---|---:|---|
| Windows | 2 | Available |
| Linux | 4 | Available |
| **Total** | **6** | **Available** |

Endpoint agents are distinct from devices that provide telemetry through agentless collection or Syslog.

## Source coverage

Available sources include:

- Windows endpoints through Wazuh agents.
- Linux endpoints through Wazuh agents.
- VMware ESXi through agentless or log-based collection.
- FortiGate through Syslog.
- Synology NAS through agentless or log-based collection.

Host inventories and destination details are omitted where they are unnecessary to explain coverage.

## Available capabilities

| Capability | Status |
|---|---|
| File Integrity Monitoring (FIM) | Available |
| Security Configuration Assessment (SCA) | Available |
| Vulnerability detection | Available |
| Alerts | Available |
| Dashboards | Available |

## Validation boundary

The deployment demonstrates homelab monitoring configuration, endpoint-agent connectivity, and log centralization. No security incident has yet been fully investigated. This work is not presented as production security operations experience.

Future validation should document representative test events, alert quality, source coverage, retention, access review, backup, and recovery without exposing credentials or sensitive infrastructure details.
