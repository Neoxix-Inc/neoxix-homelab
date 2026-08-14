# Terraform and Proxmox — Planned Learning

## Status

Terraform and Proxmox are planned learning and future lab material. This repository does not currently claim an operational Terraform deployment, provisioned Proxmox virtual machines, or proficiency with either platform.

## Intended learning scope

Future work may cover provider configuration, reusable modules, variable handling, state management, change review, and controlled virtual-machine lifecycle exercises in an isolated lab. Versions, templates, resource identifiers, hosts, and results will be documented only after validation.

## Safe example workflow

Run workflow commands only from a reviewed lab configuration that contains no embedded credentials or sensitive infrastructure details.

```text
terraform fmt
terraform validate
terraform plan -out=reviewed.tfplan
terraform apply reviewed.tfplan
```

The saved plan must be reviewed before apply. Apply should occur only with explicit operator approval and an understood rollback path; automatic approval is not part of this example.

## State and security considerations

- Keep credentials outside configuration files and version control.
- Treat state as sensitive because it may contain infrastructure data or secrets.
- Use protected remote state with access control, encryption, locking, and versioning when appropriate.
- Review provider and module sources before use and pin compatible versions after testing.
- Separate test environments from any infrastructure that must remain stable.
- Review plans for replacement, deletion, or unexpected drift before applying them.

## Destruction controls

Destructive changes require explicit approval after the exact target resources, dependencies, recovery options, and retained data have been reviewed. No unattended or automatically approved destruction workflow is documented here.

## Validation criteria

Future exercises should record prerequisites, sanitized configuration, plan review, observed results, rollback or recovery testing, and known limitations before any capability is described as tested or deployed.
