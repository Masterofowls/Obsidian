---
aliases: [input-signals, user-input, device-input]
tags: [software, input, signals, hardware]
cssclass: wiki
---
# How Devices Transform User Inputs to Signals

## Overview
User inputs (touch, clicks, keystrokes) are converted into **electrical signals** that the CPU can process.

## Keyboard
1. Key press closes a circuit
2. **Keyboard controller** detects which key was pressed
3. Sends a **scan code** to the CPU via USB/Bluetooth
4. OS maps scan code to a character based on layout

## Mouse/Touchpad
1. Optical sensor takes thousands of photos per second
2. Compares consecutive images to detect movement
3. Sends X/Y movement + button state to CPU

## Touchscreen
1. **Capacitive touch**: Finger disrupts an electrical field
2. Controller detects the disruption point
3. Maps coordinates to screen position
4. Sends touch event to OS

## Related
- [[Wiki\Software\Virtual Keyboard|Virtual Keyboard]]
