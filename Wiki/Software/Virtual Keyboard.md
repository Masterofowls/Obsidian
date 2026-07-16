---
aliases: [virtual-keyboard, on-screen-keyboard, input-method]
tags: [software, virtual-keyboard, input, touch]
cssclass: wiki
---
# How Virtual Keyboards Work

## Overview
Virtual keyboards display an **on-screen keyboard** that users tap to input text.

## How It Works
1. Touch/key event is detected at specific screen coordinates
2. Coordinates are mapped to a key based on the keyboard layout
3. Key character is sent to the active input field
4. Visual feedback (highlight, pop-up) confirms the tap

## On Phone
- Touch screen detects finger position via **capacitive sensors**
- OS maps touch coordinates to the nearest key
- Autocorrect and prediction algorithms suggest next words

## On PC
- Can be triggered by accessibility settings
- Used with touchscreens, stylus, or mouse
- Same coordinate-mapping principle

## Related
- [[Wiki\Software\Input Signals|Input Signals]]
