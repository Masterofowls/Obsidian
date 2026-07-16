---
aliases: [nfc, near-field-communication, nfc-label]
tags: [networking, nfc, rfid, short-range]
cssclass: wiki
---
# How NFC Works

## Overview
NFC (Near Field Communication) is a **short-range wireless** technology (~4cm) used for contactless payments, access cards, and data transfer.

## How It Works
- Uses **electromagnetic induction** between two coils
- One device generates a **magnetic field** (active)
- The other device induces a voltage from that field (passive or active)
- Data is transferred by modulating the field

## Two Modes

### Active-Active (Peer-to-Peer)
- Both devices have power
- Bidirectional communication
- Example: Two phones sharing data

### Active-Passive (Reader-Tag)
- Reader provides power
- Tag responds
- Example: Contactless payment, NFC tags

## NFC Tags (Labels)
- **Passive** — no battery, powered by reader's field
- Contain a tiny chip and antenna
- Can store up to 8 KB of data
- Used for: smart posters, product info, Wi-Fi pairing

## Related
- [[Wiki\Networking\Radio Signals|Radio Signals]]
- [[Wiki\Security\Two-Factor Auth|Two-Factor Auth]]
