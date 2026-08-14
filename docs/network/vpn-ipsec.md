# IKEv2 Remote-Access VPN

## Status

The FortiGate IKEv2 remote-access VPN previously passed a test, was later stopped, and is now under diagnosis pending revalidation. It is not currently operational or presented as an available remote-access service.

## Sanitized design summary

The design uses IKEv2 on the FortiGate for encrypted remote access. Authentication material, external addresses, certificate names, user or client identities, endpoint identifiers, address pools, and live connection details are intentionally excluded.

The intended high-level flow is:

1. An authorized, managed client initiates an IKEv2 connection to the firewall.
2. The firewall validates the configured authentication material and negotiates the protected tunnel.
3. Firewall policy limits authenticated clients to explicitly approved homelab resources.
4. Relevant connection and security events are logged for troubleshooting and review.

This summary is not a deployable configuration and does not establish the current authentication method or cryptographic parameters.

## Diagnosis and safe revalidation

Before the status can be promoted, revalidation should confirm:

- The firewall configuration is internally consistent and uses currently supported secure settings.
- Required authentication material is valid, protected, and trusted only where intended.
- A test from an external network completes without publishing the external endpoint.
- An authorized client can reach only approved test resources.
- An unauthorized client or disallowed destination is rejected.
- Tunnel establishment, traffic flow, disconnection, and relevant alerts appear in sanitized logs.
- The service remains stable after restart and results are documented with secrets removed.

Until these checks pass and are recorded, the VPN remains under diagnosis.
