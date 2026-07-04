---
aliases: [rsa, asymmetric-encryption, public-key-cryptography]
tags: [security, rsa, encryption, public-key]
cssclass: wiki
---
# What is RSA

## Overview
RSA is an **asymmetric encryption algorithm** that uses a pair of keys (public + private) for encryption and decryption.

## How It Works

### Key Generation
1. Choose two large prime numbers (p, q)
2. Calculate n = p × q
3. Calculate φ(n) = (p-1)(q-1)
4. Choose e such that 1 < e < φ(n) and gcd(e, φ(n)) = 1
5. Calculate d = e⁻¹ mod φ(n)
6. Public key: (e, n) — Private key: (d, n)

### Encryption
- Ciphertext = message^e mod n

### Decryption
- Message = ciphertext^d mod n

## Why It's Secure
- Factoring n into p and q is computationally infeasible for large numbers (2048+ bits)
- Time to break: millions of years with current computers

## Related
- [[Wiki\Security\Data Encryption|Data Encryption]]
- [[Wiki\Security\TLS/SSL|TLS/SSL]]
