---
aliases: [os, operating-system, how-os-works]
tags: [software, os, operating-system, kernel]
cssclass: wiki
---
# How Operating Systems Work

## Overview
An OS is **system software** that manages hardware resources and provides services for applications.

## Core Components

### Kernel
- Core of the OS, runs with full hardware access
- Manages: CPU scheduling, memory, device drivers, file systems

### Process Management
- Creates, schedules, and terminates processes
- **Context switching**: rapidly switching between processes to simulate multitasking

### Memory Management
- Allocates and deallocates RAM to processes
- **Virtual memory**: uses disk as extended RAM
- **Paging**: divides memory into fixed-size blocks

### File System
- Organizes data on storage devices
- Provides namespace (file names, directories)
- Examples: NTFS, ext4, APFS

### Device Drivers
- Interface between OS and hardware
- Translates generic commands to device-specific instructions

## Related
- [[Wiki\Hardware\Drivers|Drivers]]
- [[Wiki\Hardware\RAM|RAM]]
