---
aliases: [ssh, secure-shell, remote-access]
tags: [security, ssh, remote, terminal]
cssclass: wiki
---
# What is SSH

## Overview
SSH (Secure Shell) is a protocol for **secure remote access** to servers and devices.

## How It Works
1. Client connects to server on port 22
2. Server sends its public key
3. Client verifies the key (first time: "Are you sure?")
4. Key exchange establishes an encrypted session
5. User authenticates (password or key-based)
6. Encrypted terminal session established

## Key-Based Authentication
```bash
ssh-keygen -t ed25519          # Generate key pair
ssh-copy-id user@server        # Copy public key to server
ssh user@server                # Login without password
```

## Common Uses
- Remote server administration
- File transfer (SCP, SFTP)
- Git operations over SSH
- Tunneling and port forwarding

## Related
- [[Wiki\Security\Data Encryption|Data Encryption]]
