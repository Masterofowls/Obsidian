---
aliases: [arm, arm-architecture, arm-processors]
tags: [software, arm, architecture, cpu]
cssclass: wiki
---
# What is ARM

## Overview
ARM (Advanced RISC Machines) is a **CPU architecture** based on **RISC** (Reduced Instruction Set Computing).

## ARM vs x86
| Feature | ARM | x86 |
|---------|-----|-----|
| Philosophy | Simple instructions (RISC) | Complex instructions (CISC) |
| Power | Very efficient | Higher power consumption |
| Used in | Phones, tablets, Macs, IoT | Desktops, servers, laptops |
| Examples | Apple M-series, Snapdragon | Intel Core, AMD Ryzen |

## Why Systems Can't Handle All Architectures the Same Way
- **x86**: Complex instructions, variable length
- **ARM**: Simple instructions, fixed length (4 bytes)
- **x86-64**: 64-bit extension of x86
- **AArch64**: 64-bit ARM
- Machine code is **architecture-specific** — binary compiled for x86 won't run on ARM
- **Emulation** (like Rosetta 2) can translate at runtime but with performance cost

## Related
- [[Wiki\Hardware\CPU|CPU]]
- [[Wiki\Software\Code Execution|Code Execution]]
