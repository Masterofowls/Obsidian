---
aliases: [proxy, how-proxy-works, proxy-server]
tags: [networking, proxy, server, privacy]
cssclass: wiki
---
# How Proxy Works

## Overview
A proxy server acts as an **intermediary** between your device and the internet.

## How It Works
1. Your device sends request to proxy server
2. Proxy forwards the request to the destination
3. Destination sends response back to proxy
4. Proxy sends response to your device

## Types of Proxies

### Forward Proxy
- Sits between clients and the internet
- Used for: filtering, anonymity, bypassing restrictions

### Reverse Proxy
- Sits between internet and servers
- Used for: load balancing, caching, security (e.g., Nginx, Cloudflare)

### Transparent Proxy
- Intercepts traffic without client configuration
- Used by: ISPs, schools, workplaces

## Related
- [[Wiki\Networking\Server|Server]]
- [[Wiki\Security\CORS|CORS]]
- [[Wiki\Networking\Port Forwarding|Port Forwarding]]
