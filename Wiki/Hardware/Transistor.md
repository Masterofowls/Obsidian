---
aliases: [transistor, how-transistor-works]
tags: [hardware, electronics, transistor, semiconductor]
cssclass: wiki
---
# How Transistors Work

## Overview
A transistor is a semiconductor device that acts as a **switch** or **amplifier**. It's the fundamental building block of all modern electronics — CPUs contain billions of them.

## Types of Transistors

### BJT (Bipolar Junction Transistor)
- Has three layers: **Emitter**, **Base**, **Collector**
- A small current at the base controls a larger current between emitter and collector
- Used in older circuits and analog applications

### MOSFET (Metal-Oxide-Semiconductor Field-Effect Transistor)
- The dominant type in modern chips
- Has three terminals: **Gate**, **Source**, **Drain**
- A voltage at the gate creates an electric field that allows current to flow between source and drain

## How a MOSFET Works

### N-Channel MOSFET (simplified)
1. **Off state** — No voltage at gate → no current flows (switch is OFF)
2. **On state** — Positive voltage at gate → attracts electrons, creates a channel between source and drain → current flows (switch is ON)

### As a Switch
- Digital electronics uses transistors as binary switches: **0 (off)** or **1 (on)**
- Billions of these switches together perform computation

### As an Amplifier
- In analog circuits, small voltage changes at the gate produce larger current changes — amplifying signals

## Why Silicon?
- Silicon is a **semiconductor** — it conducts electricity sometimes, and sometimes not
- By doping silicon with impurities, we control its conductivity precisely
- Silicon is abundant, well-understood, and forms a natural oxide (SiO₂) that's a great insulator

## Related
- [[Wiki\Hardware\CPU|How CPU Works]]
- [[Wiki\Hardware\How CPUs Are Made|How CPUs Are Made]]
- [[Wiki\Physics\Electric Resistance|Electric Resistance]]
