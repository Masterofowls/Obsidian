---
aliases: [bluetooth, how-bluetooth-works]
tags: [networking, bluetooth, wireless, short-range]
cssclass: wiki
---
# How Bluetooth Works

## Overview
Bluetooth is a **short-range wireless** technology for connecting devices (headphones, keyboards, mice, speakers).

## How It Works
- Uses **2.4 GHz ISM band** (same as Wi-Fi)
- Low power → short range (~10m for Class 2)
- **Frequency-hopping spread spectrum (FHSS)** — rapidly switches between 79 channels (1600 times/second)

## How Bluetooth Signals Don't Mix
- Each connection uses a **unique hopping pattern** determined during pairing
- Multiple Bluetooth devices in the same area use different hopping sequences
- **Adaptive frequency hopping** avoids channels used by Wi-Fi

## Pairing Process
1. Devices discover each other (inquiry)
2. Exchange security keys
3. Establish encrypted link
4. Define profiles (A2DP for audio, HID for keyboards)

## Bluetooth Versions
| Version | Key Feature |
|---------|-------------|
| 4.0 | Low Energy (BLE) |
| 5.0 | 4× range, 2× speed |
| 5.3 | Improved power efficiency |

## Related
- [[Wiki\Networking\Wi-Fi|Wi-Fi]]
- [[Wiki\Networking\Radio Signals|Radio Signals]]
