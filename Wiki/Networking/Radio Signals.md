---
aliases: [radio, radio-signals, how-radio-works]
tags: [networking, radio, wireless, electromagnetic]
cssclass: wiki
---
# How Radio Signals Work

## Overview
Radio signals are **electromagnetic waves** that travel through space at the speed of light. They carry information by modulating a carrier wave.

## How It Works

### Transmission
1. An electrical signal (audio, data) is fed to an **antenna**
2. The antenna converts it into **electromagnetic waves**
3. The waves propagate through space

### Reception
1. Receiving antenna picks up the waves
2. A **demodulator** extracts the original signal
3. The signal is amplified and processed

## Frequency Modulation
- **AM (Amplitude Modulation)** — encodes data in wave amplitude
- **FM (Frequency Modulation)** — encodes data in wave frequency (better noise resistance)

## How Multiple Radio Channels Don't Mix
- Each station broadcasts on a **unique frequency**
- Receivers are tuned to **one specific frequency**
- **Frequency-division multiplexing** — multiple signals coexist by using different frequencies
- Filters reject signals on other frequencies

## How Location Tracking Works
- **Cell tower triangulation** — measures signal strength from multiple towers
- **GPS** — satellites broadcast precise timing signals; receiver calculates position
- **Wi-Fi positioning** — maps of known Wi-Fi access points determine location

## Related
- [[Wiki\Networking\Wi-Fi|Wi-Fi]]
- [[Wiki\Networking\Bluetooth|Bluetooth]]
- [[Wiki\Networking\Mobile Networks|Mobile Networks]]
