---
aliases: [wifi, wi-fi, wireless-internet]
tags: [networking, wifi, wireless, internet]
cssclass: wiki
---
# How Wi-Fi Works

## Overview
Wi-Fi uses **radio waves** to transmit data between devices and a router/access point.

## How It Works
1. Router converts data to radio signals (2.4GHz or 5GHz frequency)
2. Antenna broadcasts the signal omnidirectionally
3. Device antenna receives the signal
4. Device demodulates the signal back to data

## Frequency Bands

### 2.4 GHz
- Longer range, better wall penetration
- More interference (microwaves, Bluetooth, other networks)
- Slower speeds

### 5 GHz
- Faster speeds, less interference
- Shorter range, worse wall penetration

### 6 GHz (Wi-Fi 6E/7)
- Even faster, even less interference
- Shortest range

## How Wi-Fi "Sees" Objects and People
- Wi-Fi signals **reflect, absorb, and diffract** off objects
- Humans are ~60% water → absorb 2.4GHz signals well
- **Wi-Fi sensing** uses signal strength changes to detect movement, presence, and even gestures
- Routers can detect motion by analyzing **CSI (Channel State Information)** — changes in signal amplitude/phase across subcarriers

## Security
- **WEP** — broken, never use
- **WPA2** — current standard, AES encryption
- **WPA3** — newer, more secure

## Related
- [[Wiki\Networking\LAN and WLAN|LAN and WLAN]]
- [[Wiki\Networking\Bluetooth|Bluetooth]]
- [[Wiki\Networking\Radio Signals|Radio Signals]]
