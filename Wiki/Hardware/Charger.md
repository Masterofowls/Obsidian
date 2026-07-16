---
aliases: [charger, how-charger-works]
tags: [hardware, charger, battery, power]
cssclass: wiki
---
# How Chargers Work

## Overview
A charger converts **AC mains power** (wall outlet) into the correct **DC voltage and current** to charge a battery.

## How It Works
1. **AC to DC conversion** — A rectifier converts alternating current (AC) to direct current (DC)
2. **Voltage regulation** — A switching regulator steps down the voltage (e.g., 120V AC → 5V/9V/12V DC)
3. **Current limiting** — Controls how fast the battery charges to prevent overheating
4. **Communication** — Smart chargers negotiate with the device (USB-PD, Quick Charge) for optimal voltage

## USB Power Delivery (USB-PD)
- Negotiates voltage/current between charger and device
- Can deliver up to 240W (48V × 5A)
- Allows fast charging for phones, laptops, tablets

## Related
- [[Wiki\Hardware\Battery|Battery]]
- [[Wiki\Hardware\Wireless Charging|Wireless Charging]]
