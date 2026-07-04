---
aliases: [tcp, transmission-control-protocol, reliable-transport]
tags: [networking, tcp, protocol, transport]
cssclass: wiki
---
# How TCP Works

## Overview
TCP (Transmission Control Protocol) is a **reliable, ordered** transport protocol that ensures data arrives completely and in order.

## How It Works

### Three-Way Handshake (Connection Setup)
1. **SYN** — Client sends "I want to connect"
2. **SYN-ACK** — Server acknowledges and agrees
3. **ACK** — Client confirms → connection established

### Data Transfer
- Data is split into **segments** (packets)
- Each segment has a **sequence number**
- Receiver sends **ACKs** for received segments
- Sender retransmits if no ACK received (timeout)

### Connection Teardown
1. **FIN** — One side says "I'm done sending"
2. **ACK** — Other side acknowledges
3. **FIN** — Other side says "I'm done too"
4. **ACK** — Final acknowledgment → connection closed

## TCP vs UDP
| Feature | TCP | UDP |
|---------|-----|-----|
| Reliability | Guaranteed delivery | Best effort |
| Order | Maintained | Not guaranteed |
| Speed | Slower (overhead) | Faster |
| Use case | Web, email, file transfer | Gaming, streaming, DNS |

## Related
- [[Wiki\Networking\HTTP-HTTPS|HTTP/HTTPS]]
