---
aliases: [lan, wlan, local-area-network, wireless-lan]
tags: [networking, lan, wlan, ethernet, wifi]
cssclass: wiki
---
# How LAN and WLAN Work

## LAN (Local Area Network)

### How It Works
- Connects devices in a limited area (home, office, building)
- Uses **Ethernet cables** (Cat5e, Cat6, Cat6a) for wired connections
- Data is sent as **frames** (packets at Layer 2)
- A **switch** forwards frames to the correct device using MAC addresses

### Components
- **Router** — connects LAN to the internet, assigns IP addresses (DHCP)
- **Switch** — connects devices within the LAN
- **Ethernet cable** — physical medium (copper or fiber)

## WLAN (Wireless LAN / Wi-Fi)

### How It Works
- Same as LAN but uses **radio waves** instead of cables
- A **wireless access point (AP)** broadcasts signals on 2.4GHz and 5GHz bands
- Devices connect by associating with the AP's SSID (network name)

### Wi-Fi Standards
| Standard | Frequency | Max Speed |
|----------|-----------|-----------|
| 802.11n (Wi-Fi 4) | 2.4/5 GHz | 600 Mbps |
| 802.11ac (Wi-Fi 5) | 5 GHz | 3.5 Gbps |
| 802.11ax (Wi-Fi 6) | 2.4/5 GHz | 9.6 Gbps |
| 802.11be (Wi-Fi 7) | 2.4/5/6 GHz | 46 Gbps |

## Related
- [[Wiki\Networking\Wi-Fi|Wi-Fi]]
- [[Wiki\Networking\Bluetooth|Bluetooth]]
