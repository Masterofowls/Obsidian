---
aliases: [two-factor-auth, 2fa, mfa, multi-factor]
tags: [security, authentication, 2fa, mfa]
cssclass: wiki
---
# How Two-Factor Authentication Works

## Overview
2FA adds a **second layer of security** beyond just a password. Even if your password is stolen, attackers need the second factor.

## The Three Factors
1. **Something you know** — password, PIN
2. **Something you have** — phone, hardware token
3. **Something you are** — fingerprint, face, iris

## Common 2FA Methods

### SMS/Email Code
- Server sends a 6-digit code
- User enters the code to verify
- **Weakness**: SIM swapping, email compromise

### Authenticator App (TOTP)
- App generates a new 6-digit code every 30 seconds
- Based on shared secret + time
- Examples: Google Authenticator, Authy

### Hardware Token
- Physical device generates codes
- Examples: YubiKey, Google Titan
- Most secure option

## How TOTP Works
1. Server and app share a secret key
2. Both generate the same code using: `HMAC(secret, time / 30)`
3. Codes match → verified

## Related
- [[Wiki\Networking\Passkeys|Passkeys]]
- [[Wiki\Security\Data Encryption|Data Encryption]]
