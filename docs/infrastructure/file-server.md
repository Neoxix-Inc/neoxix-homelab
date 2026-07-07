# File Server — SRV-FILE01

## Information
| Parameter | Value |
|---|---|
| Hostname | SRV-FILE01 |
| IP | 10.50.0.21/24 |
| OS | Windows Server 2025 |
| Domain | neoxix.local |
| VLAN | VLAN50_DC |

## Roles Installed
- File Server
- DFS Namespaces
- DFS Replication

## Shares
| Share Name | Path | Access |
|---|---|---|
| Company | C:\Shares\Company | Domain Admins (Full), Domain Users (Change) |
| Users | C:\Shares\Users | Domain Admins (Full), Domain Users (Change) |
| IT | C:\Shares\IT | Domain Admins (Full) |
| Backup | C:\Shares\Backup | Domain Admins (Full) |

## UNC Paths
- \\SRV-FILE01\Company
- \\SRV-FILE01\Users
- \\SRV-FILE01\IT
- \\SRV-FILE01\Backup

## Monitoring
- Wazuh Agent: v4.12 (Active)
