# NetBox IPAM — NAS DS925+

## Information
| Parameter | Value |
|---|---|
| URL | http://10.50.0.5:8081 |
| Version | 4.6.4-Docker |
| Deployment | Docker Compose (NAS) |

## Docker Services
| Container | Image | Port | Status |
|---|---|---|---|
| netbox | netboxcommunity/netbox:latest | 8081 | Running |
| netbox-worker | netboxcommunity/netbox:latest | - | Running |
| netbox-postgres | postgres:16-alpine | 5432 | Running |
| netbox-redis | redis:7-alpine | 6379 | Running |

## Data Populated
- Site: Neoxix-HQ
- VLANs: 10 (VLAN30 → VLAN110)
- Prefixes: 12
- IP Addresses: 9

## Compose File
- Path: /volume1/docker/netbox/docker-compose.yml
