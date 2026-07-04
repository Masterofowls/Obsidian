---
aliases: [cors, cross-origin-resource-sharing, same-origin-policy]
tags: [networking, cors, security, browser]
cssclass: wiki
---
# How CORS Works

## Overview
CORS (Cross-Origin Resource Sharing) is a mechanism that allows or blocks web requests to **different domains**.

## The Problem
- **Same-Origin Policy** — browsers block requests from `site-a.com` to `site-b.com`
- This prevents malicious sites from stealing data
- But legitimate APIs need cross-origin access

## How CORS Works
1. Browser sends a **preflight request** (OPTIONS) to the server
2. Server responds with allowed origins, methods, headers
3. Browser allows or blocks the actual request

## Headers
- `Access-Control-Allow-Origin: https://example.com`
- `Access-Control-Allow-Methods: GET, POST, PUT`
- `Access-Control-Allow-Headers: Content-Type, Authorization`

## Related
- [[Wiki\Networking\HTTP-HTTPS|HTTP/HTTPS]]
- [[Wiki\Networking\Proxy|Proxy]]
