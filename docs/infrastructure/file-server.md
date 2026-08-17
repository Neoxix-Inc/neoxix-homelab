# Proposed File Server Lab Design

## Status

This document is a proposed future lab design. It does not describe a deployed file server. No server hostname, address, share, DFS configuration, permission model, UNC path, or Wazuh integration is currently claimed as active.

## Learning objectives

The proposed lab would explore:

- Windows Server file services.
- Role-based access using Active Directory security groups.
- Share and NTFS permission interaction.
- Optional DFS namespace and replication behavior.
- Backup, restoration, auditing, and monitoring.

## Example design concepts

The following names are conceptual examples only and must not be interpreted as implemented shares:

| Example share | Intended concept | Example access approach |
|---|---|---|
| Department | Shared team data | Grant access through a dedicated role-based group |
| User Data | User-specific storage | Limit each user to the appropriate personal area |
| IT Lab | Administrative lab material | Restrict access to an authorized lab administration group |
| Recovery Test | Backup and restore exercises | Restrict access and audit all recovery activity |

Final names, storage paths, quotas, permissions, and retention rules would be selected during implementation and documented only after validation.

## Prerequisites

Before implementation, the lab requires:

- A deployed Windows Server VM with an approved hostname and network placement.
- Completed OU and security-group design in Active Directory.
- A documented least-privilege access model.
- Suitable storage capacity and a backup destination.
- Defined recovery objectives and a rollback plan.
- A monitoring plan that distinguishes endpoint-agent coverage from log forwarding.

## Criteria for deployed status

The design may be promoted to deployed only after:

1. Server identity, network placement, and installed roles are recorded and reviewed.
2. Each share and any DFS feature is configured as designed.
3. Intended users can access only approved data, and denied-access tests succeed.
4. Backup and representative file restoration are tested and documented.
5. Auditing and monitoring produce expected test events without exposing sensitive data.
6. Validation results, limitations, and rollback steps are recorded.
