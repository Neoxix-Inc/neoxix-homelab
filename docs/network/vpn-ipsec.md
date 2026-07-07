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
| [REDACTED_VPN_IDENTITY] | [REDACTED_VPN_IDENTITY] | Neoxix-Root-CA | 2028-06-18 | FortiGate Local Certs |
| CA_Cert_1 | Neoxix-Root-CA | Neoxix-Root-CA | - | FortiGate CA Certs |
| [REDACTED_VPN_IDENTITY]-client | [REDACTED_VPN_IDENTITY] | Neoxix-Root-CA | 2028-06-18 | iPad Keychain |

## Tunnel Config
- Name: Neoxix-VPN
- IKE Version: 2
- Encryption: AES256
- Hash: SHA256
- DH Group: 14

## Client Config (iOS Native IKEv2)
- Server: [REDACTED_PUBLIC_VPN_ENDPOINT]
- Remote ID: [REDACTED_VPN_IDENTITY]
- Local ID: [REDACTED_VPN_IDENTITY]
- Certificate: [REDACTED_VPN_IDENTITY]

## Status
- Tunnel: Configured (test pending from external network)
