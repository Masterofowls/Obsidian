---
aliases: [passkeys, passwordless, fido2, webauthn]
tags: [networking, passkeys, authentication, security]
cssclass: wiki
---
# How Passkeys Work

## Overview
Passkeys are a **passwordless authentication** standard (FIDO2/WebAuthn) that replaces passwords with cryptographic key pairs.

## How It Works

### Registration
1. Server sends a challenge
2. Device generates a **key pair** (public + private)
3. Private key stored securely on device (Secure Enclave/TPM)
4. Public key sent to server

### Authentication
1. Server sends challenge
2. Device signs the challenge with private key
3. Server verifies with stored public key
4. No password transmitted — nothing to phish

## Benefits
- Immune to phishing (no password to steal)
- No password reuse across sites
- No need to remember passwords
- Biometric unlock (fingerprint/face) to authorize

## Related
- [[Wiki\Security\Two-Factor Auth|Two-Factor Auth]]
- [[Wiki\Security\TLS/SSL|TLS/SSL]]
