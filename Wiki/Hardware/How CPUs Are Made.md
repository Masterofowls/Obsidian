---
aliases: [cpu-manufacturing, cpu-fabrication, how-cpus-are-made]
tags: [hardware, cpu, manufacturing, semiconductor]
cssclass: wiki
---
# How CPUs Are Made

## Overview
Making a CPU is one of the most complex manufacturing processes in human history. A single modern CPU can contain billions of transistors etched onto a silicon wafer smaller than a fingernail.

## Step-by-Step Process

### 1. Sand to Silicon
- CPU manufacturing starts with **silicon dioxide (SiO₂)** — essentially pure sand
- The silicon is refined to 99.9999% purity ("nine nines")
- A single crystal ingot (boule) is grown using the **Czochralski process** — a seed crystal is dipped into molten silicon and slowly pulled upward, forming a perfect crystal structure

### 2. Wafer Preparation
- The ingot is sliced into thin discs called **wafers** (~0.75mm thick)
- Wafers are polished to an almost perfectly flat surface

### 3. Photolithography
- A light-sensitive chemical called **photoresist** is applied to the wafer
- A **mask** (stencil) with the circuit pattern is placed over it
- **UV light** shines through the mask, hardening the exposed photoresist
- The unhardened resist is washed away, exposing the silicon beneath

### 4. Etching & Doping
- Exposed silicon is etched away using chemicals or plasma
- **Dopants** (boron, phosphorus, arsenic) are injected into specific areas to create **p-type** and **n-type** regions — forming transistors
- This process is repeated **dozens of times** to build up layers of transistors and interconnects

### 5. Metal Interconnects
- Copper or aluminum wiring is deposited to connect transistors into circuits
- Modern CPUs have **10-20+ layers** of metal interconnects

### 6. Testing & Cutting
- Each die on the wafer is tested for defects
- Working dies are cut out, packaged, and pins/bumps are added

## Key Facts
- A modern process node (e.g., 3nm, 5nm) refers to the size of transistor features
- A single EUV lithography machine costs ~$150 million
- Intel, TSMC, and Samsung are the main manufacturers
- A single wafer can produce hundreds of CPU dies

## Related
- [[Wiki\Hardware\CPU|How CPU Works]]
- [[Wiki\Hardware\Transistor|Transistor]]
