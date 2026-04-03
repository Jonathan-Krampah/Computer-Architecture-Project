# CPEN 315 - Computer Organization & Architecture Final Project

Author: Jonathan Krampah  
Course: CPEN 315, University of Ghana  
Semester: First Semester 2025/2026  


## Project Overview

This project implements two CPUs:

- **Part A:** 16-bit CPU designed graphically in **Logisim Evolution**  
- **Part B:** 32-bit single-cycle MIPS processor implemented in **VHDL** and verified with **GHDL** and **GTKWave**

All required components and test cases from the lab manual are included and verified.



## Part A: 16-bit CPU in Logisim Evolution

### How to Run

1. Download and install **Logisim Evolution** from https://github.com/logisim-evolution/logisim-evolution
2. Open `PartA_Logisim/16bit_CPU.circ`
3. Go to `Simulate → Tick Enabled` (or press `Ctrl+T`) to start the clock
4. Observe the 7-segment displays showing Register A, Register B, Output Register, and Program Counter

### Program Executed

The CPU executes a fixed program stored in RAM:
- Load value 10 from address 10 into Register A
- Load value 15 from address 13 into Register B
- Add Register A and Register B (10 + 15 = 25)
- Store result (25) back to address 10

---

## Part B: 32-bit MIPS Processor in VHDL

### Requirements

- **GHDL** – VHDL compiler/simulator
- **GTKWave** – Waveform viewer
- Windows users: Use **MSYS2** terminal

### Installation (Windows with MSYS2)

```bash
# Install GHDL and GTKWave
pacman -S mingw-w64-ucrt-x86_64-ghdl
pacman -S mingw-w64-ucrt-x86_64-gtkwave

# Add to PATH
export PATH=/ucrt64/bin:$PATH

## How to Simulate (Example: ALU)

```bash
cd PartB_VHDL/src
ghdl -a ALU_32bit.vhd
ghdl -a ../testbench/ALU_32bit_tb.vhd
ghdl -e ALU_32bit_tb
ghdl -r ALU_32bit_tb --stop-time=120ns --wave=../waveforms/ALU_32bit_wave.ghw
gtkwave ../waveforms/ALU_32bit_wave.ghw

All Test Cases Passed ✓
ALU: 5 operations (ADD, SUB, AND, OR, SLT) ✓

Register File: Write/Read 4 registers ✓

Instruction Memory: 4 MIPS instructions ✓

Control Unit: 8 instructions ✓

Data Memory: Write/Read 1024 and 429496 ✓

Tools: Logisim Evolution 4.1.0, GHDL 6.0.0, GTKWave 3.3.124, MSYS2
