---
aliases: [cpu, processor, central-processing-unit]
tags: [hardware, cpu, processor, computing]
cssclass: wiki
---
# How CPU Works

## Overview
The CPU (Central Processing Unit) is the "brain" of a computer. It executes instructions from programs by performing basic arithmetic, logic, control, and input/output operations.

## Basic Structure

### Components
- **ALU (Arithmetic Logic Unit)** — performs math and logic operations
- **Control Unit (CU)** — directs the flow of data between CPU and other components
- **Registers** — small, fast storage locations inside the CPU
- **Cache** — fast memory built into or near the CPU

### How It Executes Instructions
1. **Fetch** — The CPU retrieves an instruction from memory (RAM)
2. **Decode** — The Control Unit interprets what the instruction means
3. **Execute** — The ALU performs the operation (add, compare, move data)
4. **Store** — The result is written back to a register or memory

This cycle repeats billions of times per second (measured in GHz — a 3 GHz CPU performs ~3 billion cycles per second).

## Clock Speed
- Each cycle is a "tick" of the CPU's internal clock
- Higher GHz = more cycles per second = generally faster
- Modern CPUs can execute multiple instructions per cycle (IPC — Instructions Per Cycle)

## Cores & Threads
- A **core** is an independent processing unit — multi-core CPUs have multiple cores on one chip
- **Hyper-threading / SMT** allows one physical core to handle two threads simultaneously, improving efficiency

## Pipelining
CPUs don't wait for one instruction to finish before starting the next — they pipeline instructions so multiple stages of different instructions are processed simultaneously.

## Branch Prediction
The CPU guesses which code path a program will take next and pre-loads those instructions. Wrong guesses waste cycles but correct predictions keep throughput high.

## Related
- [[Wiki\Hardware\How CPUs Are Made|How CPUs Are Made]]
- [[Wiki\Hardware\Transistor|Transistor]]
- [[Wiki\Hardware\RAM|RAM]]
- [[Wiki\Hardware\GPU|GPU]]
