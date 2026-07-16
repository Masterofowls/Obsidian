---
aliases: [websocket, ws, real-time]
tags: [networking, websocket, real-time, protocol]
cssclass: wiki
---
# How WebSocket Works

## Overview
WebSocket provides **full-duplex, persistent** communication between client and server over a single TCP connection.

## How It Works
1. **HTTP handshake** — Client sends an Upgrade request
2. Server responds with `101 Switching Protocols`
3. Connection is upgraded from HTTP to WebSocket
4. Both sides can send messages at any time (no request-response pattern)
5. Connection stays open until explicitly closed

## WebSocket vs HTTP
| Feature | HTTP | WebSocket |
|---------|------|-----------|
| Direction | Client → Server | Both ways |
| Connection | New each request | Persistent |
| Latency | Higher (headers each time) | Lower (no headers) |
| Use case | Web pages, APIs | Chat, games, live data |

## Use Cases
- Chat applications (Discord, Slack)
- Real-time notifications
- Multiplayer games
- Live stock/crypto tickers

## Related
- [[Wiki\Networking\HTTP/HTTPS|HTTP/HTTPS]]
