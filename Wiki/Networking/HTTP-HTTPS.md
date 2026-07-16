---
aliases: [http, https, http-and-https, hypertext-transfer-protocol]
tags: [networking, http, https, web, protocol]
cssclass: wiki
---
# What is HTTP and HTTPS

## HTTP (HyperText Transfer Protocol)
- Foundation of data communication on the web
- **Request-response** model: client sends request, server sends response
- Stateless — each request is independent
- Default port: 80

## How HTTP Works
1. Client sends a request (GET, POST, PUT, DELETE)
2. Server processes the request
3. Server sends back a response (status code + data)

## HTTPS (HTTP Secure)
- HTTP + **TLS encryption**
- Encrypts all data in transit (no eavesdropping)
- Server identity verified by **SSL certificate**
- Default port: 443

## Key Difference
- HTTP → data in **plain text** (can be intercepted)
- HTTPS → data is **encrypted** (safe from interception)

## Status Codes
| Code | Meaning |
|------|---------|
| 200 | OK |
| 301 | Moved Permanently |
| 404 | Not Found |
| 500 | Server Error |

## Related
- [[Wiki\Security\TLS/SSL|TLS/SSL]]
- [[Wiki\Security\CORS|CORS]]
