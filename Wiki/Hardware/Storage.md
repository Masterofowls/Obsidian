---
aliases: [storage, ssd, hdd, how-storage-works]
tags: [hardware, storage, ssd, hdd]
cssclass: wiki
---
# How SSD and HDD Work

## HDD (Hard Disk Drive)

### How It Works
- Uses **magnetic storage** on spinning platters
- A **read/write head** floats nanometers above the platter surface
- Platters spin at 5400-7200 RPM (or 10000-15000 for enterprise)
- The head moves radially to access different tracks

### Components
- **Platters** — spinning magnetic discs
- **Read/write head** — changes magnetic orientation to store bits
- **Actuator arm** — positions the head over the right track
- **Spindle motor** — spins the platters

## SSD (Solid State Drive)

### How It Works
- Uses **NAND flash memory** — no moving parts
- Data is stored as **electrical charges** in floating-gate transistors
- Reads/writes are electrical, not mechanical → much faster

### NAND Flash Types
| Type | Bits/Cell | Speed | Endurance |
|------|-----------|-------|-----------|
| SLC | 1 | Fastest | Highest |
| MLC | 2 | Fast | High |
| TLC | 3 | Medium | Medium |
| QLC | 4 | Slower | Lower |

## Comparison
| Feature | HDD | SSD |
|---------|-----|-----|
| Speed | ~150 MB/s | ~3500-7000 MB/s |
| Latency | ~5-10 ms | ~0.1 ms |
| Durability | Fragile (moving parts) | Rugged |
| Cost | ~$20/TB | ~$60-100/TB |

## Related
- [[Wiki\Hardware\RAM|RAM]]
- [[Wiki\Hardware\CPU|CPU]]
