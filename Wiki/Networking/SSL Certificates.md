---
aliases: [ssl-certificate, tls-certificate, ssl-tls]
tags: [networking, ssl, tls, certificate, security]
cssclass: wiki
---
# What are SSL/TLS Certificates

## Overview
An SSL/TLS certificate is a digital document that **verifies a website's identity** and **enables encryption**.

## What It Contains
- Domain name the certificate is issued to
- Public key of the website
- Certificate authority (CA) that issued it
- Expiration date
- Digital signature

## How It Works
1. Browser connects to server
2. Server sends its certificate
3. Browser verifies the certificate against trusted CAs
4. Browser uses the public key to establish an encrypted session
5. All subsequent communication is encrypted

## Certificate Authorities (CAs)
- Let's Encrypt (free)
- DigiCert, Comodo, GlobalSign (paid)
- Browsers/OS maintain a list of trusted CAs

## Related
- [[Wiki\Networking\HTTP-HTTPS|HTTP/HTTPS]]
- [[Wiki\Security\TLS/SSL|TLS/SSL]]
