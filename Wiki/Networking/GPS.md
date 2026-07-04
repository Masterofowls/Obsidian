---
aliases: [gps, global-positioning-system, location]
tags: [networking, gps, location, satellite]
cssclass: wiki
---
# How GPS Works

## Overview
GPS (Global Positioning System) uses **satellites** to determine your precise location on Earth.

## How It Works
1. **24+ satellites** orbit Earth at ~20,200 km altitude
2. Each satellite continuously broadcasts its **position** and **precise time**
3. Your GPS receiver picks up signals from multiple satellites
4. Receiver calculates distance to each satellite using **time delay**
5. **Trilateration** — intersection of distances pinpoints your location

## Position Calculation
- 3 satellites → 2D position (latitude, longitude)
- 4 satellites → 3D position (latitude, longitude, altitude) + time correction

## Accuracy
- Standard GPS: ~3-5 meters
- With WAAS/DGPS: ~1-2 meters
- RTK GPS: ~1-2 cm (surveying)

## Related
- [[Wiki\Networking\Radio Signals|Radio Signals]]
- [[Wiki\Networking\Mobile Networks|Mobile Networks]]
