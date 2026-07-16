---
aliases: [server, how-server-works, web-server]
tags: [networking, server, web, backend]
cssclass: wiki
---
# How Servers Work

## Overview
A server is a computer that **listens for requests** and **responds** with data or services.

## How It Works
1. Server runs a program that **listens on a port** (e.g., 80 for HTTP)
2. Client sends a request to the server's IP + port
3. Server processes the request
4. Server sends back a response (HTML, JSON, files, etc.)

## Types of Servers
| Type | Purpose |
|------|---------|
| Web server | Serves web pages (Apache, Nginx) |
| Application server | Runs business logic (Node.js, Django) |
| Database server | Stores/retrieves data (PostgreSQL, MySQL) |
| File server | Stores files (NAS, FTP) |
| Mail server | Handles email (Postfix, Exchange) |

## Related
- [[Wiki\Networking\HTTP-HTTPS|HTTP/HTTPS]]
- [[Wiki\Networking\Port Forwarding|Port Forwarding]]
