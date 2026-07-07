# IPsec VPN IKEv2 — FortiGate 60F

## Information
| Parameter | Value |
|---|---|
| Protocol | IPsec IKEv2 |
| Authentication | X.509 Certificates (ADCS) |
| Interface | BELL_WAN1 (wan1) |
| IP Pool | 10.200.0.100-200/24 |
| Transport | UDP/500, UDP/4500 |

## Certificates
| Certificate | CN | Issuer | Expiry | Location |
|---|---|---|---|---|
| fortigate-vpn-server | fortigate-60f | Neoxix-Root-CA | 2028-06-18 | FortiGate Local Certs |
| CA_Cert_1 | Neoxix-Root-CA | Neoxix-Root-CA | - | FortiGate CA Certs |
| kodjo-client | kodjo | Neoxix-Root-CA | 2028-06-18 | iPad Keychain |

## Tunnel Config
- Name: Neoxix-VPN
- IKE Version: 2
- Encryption: AES256
- Hash: SHA256
- DH Group: 14

## Client Config (iOS Native IKEv2)
- Server: 76.64.201.138
- Remote ID: fortigate-60f
- Local ID: kodjo
- Certificate: kodjo

## Status
- Tunnel: Configured (test pending from external network)
