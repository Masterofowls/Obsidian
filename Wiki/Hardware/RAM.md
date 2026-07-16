---
aliases: [ram, random-access-memory, memory]
tags: [hardware, ram, memory, volatile]
cssclass: wiki
---
# How RAM Works

## Overview
RAM (Random Access Memory) is **volatile** memory that stores data your computer is actively using. It's fast but loses data when power is off.

## How It Works

### DRAM (Dynamic RAM) — most common
- Each bit is stored as a charge in a tiny **capacitor**
- Capacitors leak charge over time → must be **refreshed thousands of times per second**
- Simple design → dense (lots of bits per chip) → cheap

### SRAM (Static RAM) — used in CPU cache
- Each bit uses **6 transistors** to hold the value
- No refresh needed → faster but larger and more expensive
- Used for L1, L2, L3 cache inside the CPU

## DDR (Double Data Rate)
- Modern RAM is DDR — transfers data on **both** the rising and falling edge of the clock signal
- DDR4, DDR5 are current generations

## How Data Is Stored
1. CPU needs data → sends address to RAM via the **memory bus**
2. RAM's **memory controller** finds the right row and column
3. Data is sent back to CPU
4. This happens in **nanoseconds** (DDR5-6400 has ~12.5ns latency)

## RAM vs Storage
| Feature | RAM | SSD/HDD |
|---------|-----|---------|
| Speed | ~50 GB/s | ~3-7 GB/s |
| Volatility | Volatile | Non-volatile |
| Purpose | Active data | Permanent storage |

## Related
- [[Wiki\Hardware\CPU|CPU]]
- [[Wiki\Hardware\VRAM|VRAM]]
- [[Wiki\Hardware\Storage|Storage]]
