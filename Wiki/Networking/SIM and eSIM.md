---
aliases: [sim, esim, subscriber-identity-module]
tags: [networking, sim, esim, mobile]
cssclass: wiki
---
# How SIM and eSIM Work

## SIM Card
- **Subscriber Identity Module** — small chip card
- Stores: IMSI (subscriber ID), authentication key, contacts
- Identifies you to the mobile network
- Allows you to swap phones by moving the SIM

## How It Works
1. Phone inserts SIM → reads IMSI
2. Phone sends IMSI to cell tower
3. Network verifies subscription
4. Network authenticates using shared secret (Ki)
5. Encrypted session established

## eSIM (Embedded SIM)
- **Soldered directly** into the device (no physical card)
- Profile downloaded remotely via QR code or carrier app
- Can store **multiple profiles** (switch between carriers)
- Used in: modern phones, smartwatches, laptops, IoT devices

## Benefits of eSIM
- No physical SIM to swap
- Instant carrier switching
- Better water resistance (no SIM tray)
- Ideal for travel

## Related
- [[Wiki\Networking\Mobile Networks|Mobile Networks]]
- [[Wiki\Networking\Radio Signals|Radio Signals]]
