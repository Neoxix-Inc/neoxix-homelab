# Active Directory — neoxix.local

## Current state

The `neoxix.local` domain is provided by two Windows Server 2025 domain controllers.

| Hostname | Role | Status |
|---|---|---|
| `DC01-HQ` | Domain controller and DNS server | Operational and validated |
| `DC02-BR2` | Domain controller and DNS server | Operational and validated |

Active Directory and DNS replication between the two domain controllers is functional. DHCP is provided by the FortiGate rather than Windows Server.

## Work not yet completed

The following work is not yet complete and is not represented as operational:

- Organizational-unit design.
- Security-group design.
- Permissions implementation and validation.
- Group Policy design and validation.
- Domain-controller backup.

## Unvalidated details

The authoritative baseline does not establish forest or domain functional levels, FSMO role placement, reverse DNS zones, or a deployed PKI/Active Directory Certificate Services design. Root certification authorities, certificate templates, and certificate inventories are therefore intentionally omitted until they are independently validated and sanitized.

## Validation boundary

Current validation is limited to the stated domain-controller, DNS, and replication functions. Future identity, policy, permission, backup, or certificate work must be documented and tested before its status changes.
