# Terraform — Proxmox VM Provisioning

## Information
| Parameter | Value |
|---|---|
| Version | Terraform v1.15.7 |
| Provider | bpg/proxmox v0.111.0 |
| Proxmox | 192.168.2.26:8006 (PVE 9.1.1) |
| Repo | github.com/Neoxix-Inc/neoxix-homelab-terraform |

## VMs Provisioned
| VM | ID | IP | VLAN | RAM | Disk | Role |
|---|---|---|---|---|---|---|
| SRV-ZABBIX | 201 | 192.168.2.201 | Native | 4 GB | 60 GB | Monitoring |
| SRV-WAZUH (Proxmox) | 202 | 192.168.2.202 | Native | 4 GB | 100 GB | SIEM |
| SRV-LINUX-ADMIN | 203 | 192.168.2.203 | Native | 4 GB | 60 GB | Linux Admin |
| SRV-GITEA | 204 | 192.168.2.204 | Native | 4 GB | 60 GB | Git Server |

## Important Notes
- KVM disabled: `qm set <id> --kvm 0`
- Parallelism=1 required: `terraform apply -parallelism=1`
- Template: VM 9000 (ubuntu-22-04-cloud)
- SSH key: ~/.ssh/terraform_neoxix

## Commands
```bash
terraform plan -parallelism=1
terraform apply -auto-approve -parallelism=1
terraform destroy -auto-approve -parallelism=1
```
