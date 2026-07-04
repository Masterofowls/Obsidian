---
aliases: [tls, ssl, tls-ssl, transport-layer-security]
tags: [security, tls, ssl, encryption, protocol]
cssclass: wiki
---
# How TLS/SSL Works

## Overview
TLS (Transport Layer Security) encrypts communication between your browser and a website. SSL is its predecessor (now deprecated).

## TLS Handshake
1. **Client Hello** — Browser sends supported encryption methods
2. **Server Hello** — Server picks a method and sends its certificate
3. **Certificate Verification** — Browser checks the certificate against trusted CAs
4. **Key Exchange** — Both sides generate a shared session key (Diffie-Hellman)
5. **Encrypted Communication** — All data is now encrypted with the session key

## Versions
| Version | Status |
|---------|--------|
| SSL 2.0 | Insecure, deprecated |
| SSL 3.0 | Insecure, deprecated |
| TLS 1.0 | Deprecated |
| TLS 1.1 | Deprecated |
| TLS 1.2 | Current standard |
| TLS 1.3 | Latest, faster handshake |

## Related
- [[Wiki\Networking\HTTP-HTTPS|HTTP/HTTPS]]
- [[Wiki\Security\Data Encryption|Data Encryption]]
- [[Wiki\Security\RSA|RSA]]
