---
aliases: [app-signing, code-signing, application-signing]
tags: [security, signing, certificates, trust]
cssclass: wiki
---
# How Application Signing Works

## Overview
Code signing uses **digital certificates** to verify that software comes from a trusted source and hasn't been tampered with.

## How It Works
1. Developer generates a **key pair** (public + private)
2. Developer requests a certificate from a **Certificate Authority (CA)**
3. Developer signs the application with their private key
4. OS/browser verifies the signature with the developer's public key
5. If signature is valid → trusted

## What It Proves
- **Identity** — the software is from who it claims
- **Integrity** — the software hasn't been modified since signing

## APK Signing (Android)
- All APKs must be signed to install
- **Debug keystore** — for development
- **Release keystore** — for production
- Google Play requires **Google Play App Signing**

## Related
- [[Wiki\Security\SSL Certificates|SSL Certificates]]
- [[Wiki\Software\APK|APK]]
