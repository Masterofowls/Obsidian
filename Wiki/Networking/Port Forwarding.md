---
aliases: [port-forwarding, nat, network-address-translation]
tags: [networking, port-forwarding, nat, router]
cssclass: wiki
---
# How Port Forwarding Works

## Overview
Port forwarding allows external devices to access services on a private network by mapping a public port to an internal IP:port.

## The Problem
- Your router has one public IP but many devices behind it (NAT)
- Incoming traffic doesn't know which device to reach
- Port forwarding creates a rule: "Traffic on port X → send to device Y:port Z"

## How It Works
1. External device connects to your public IP on a specific port (e.g., port 8080)
2. Router receives the connection
3. Port forwarding rule matches: "8080 → 192.168.1.50:80"
4. Router forwards the traffic to the internal device

## Common Uses
- Hosting game servers
- Accessing home security cameras
- Running a web server from home
- Remote desktop access

## Security Concerns
- Exposes internal services to the internet
- Always use strong passwords and keep software updated
- Consider VPN as a more secure alternative

## Related
- [[Wiki\Networking\Server|Server]]
- [[Wiki\Networking\Proxy|Proxy]]
