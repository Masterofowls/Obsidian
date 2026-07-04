---
aliases: [data-encryption, encryption, decrypt, cryptography]
tags: [security, encryption, cryptography, data]
cssclass: wiki
---
# How Data Encryption Works

## Overview
Encryption converts **readable data (plaintext)** into **unreadable data (ciphertext)** that can only be decrypted with a key.

## Symmetric Encryption
- Same key encrypts and decrypts
- Fast, used for large data
- Examples: AES-256, ChaCha20
- Problem: How to share the key securely?

## Asymmetric Encryption
- Public key encrypts, private key decrypts
- Slower, used for key exchange and signatures
- Examples: RSA, ECC
- Used in: TLS, SSH, GPG

## How TLS Uses Both
1. Client and server use **asymmetric** encryption to exchange a session key
2. All subsequent communication uses **symmetric** encryption with that session key
3. Best of both worlds: secure key exchange + fast data transfer

## Related
- [[Wiki\Security\RSA|RSA]]
- [[Wiki\Security\TLS/SSL|TLS/SSL]]
