---
aliases: [drivers, device-drivers, how-drivers-work]
tags: [hardware, drivers, software, operating-system]
cssclass: wiki
---
# How Drivers Work

## Overview
A driver is a software program that allows the **operating system** to communicate with **hardware devices**.

## What It Does
- Translates generic OS commands into device-specific instructions
- Each hardware device (GPU, printer, network card) needs its own driver
- Without the right driver, the OS cannot use the device

## How It Works
1. **OS sends a request** (e.g., "print this document")
2. **Driver translates** the request into commands the printer understands
3. **Device executes** the command
4. **Driver reports** the result back to the OS

## Types
| Type | Example |
|------|---------|
| Kernel driver | Deep system access (GPU, network) |
| User-mode driver | Printer, USB devices |
| Generic driver | Basic functionality (USB HID) |
| Manufacturer driver | Full feature set |

## Where Drivers Live
- **Windows**: `C:\Windows\System32\drivers\`
- **Linux**: `/lib/modules/`
- **macOS**: `/System/Library/Extensions/`

## Related
- [[Wiki\Software\Operating System|Operating System]]
