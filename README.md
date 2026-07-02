# Wireless CAN Transceiver

> A concept FPGA-based system for transmitting CAN bus traffic wirelessly

---

## Overview

This project explores the design and implementation of a complete digital communication chain for wireless transmission of Controller Area Network (CAN) traffic.

The system captures CAN frames from a wired CAN bus with the PS side of an AMD/Xilinx SoC. It then processes and packages the data within the PL, modulates the information using BPSK, and generates a digital baseband signal suitable for upconversion and RF transmission with an external DAC, PLL, IQ mixer, then LNA and potentially bandpass filter then finally to an antenna.

The long-term objective is to develop a flexible software-defined radio (SDR) style architecture where each stage of the communication chain is implemented as an independent hardware module.

---

## Project Goals

* Receive CAN traffic from a standard CAN bus
* Parse and buffer CAN frames
* Encode data for wireless transmission
* Generate a BPSK-modulated digital waveform
* Interface with an RF front-end for transmission

---

## System Architecture
(AI made this very nice diagram. I'm not confident that this is exactly what it will look like)
                 Wired CAN Bus
                       │
                       ▼
              ┌─────────────────┐
              │ CAN Controller  │
              └─────────────────┘
                       │
                       ▼
              ┌─────────────────┐
              │ Frame Buffer    │
              └─────────────────┘
                       │
                       ▼
              ┌─────────────────┐
              │ Packet Encoder  │
              └─────────────────┘
                       │
                       ▼
              ┌─────────────────┐
              │ BPSK Modulator  │
              └─────────────────┘
                       │
                       ▼
              ┌─────────────────┐
              │ Pulse Shaping   │
              └─────────────────┘
                       │
                       ▼
              ┌─────────────────┐
              │ DAC / RF Front  │
              └─────────────────┘
                       │
                       ▼
                 Wireless Link
```

---

## Planned Hardware

Current development is based around:

* Digilent Cora Z7 FPGA Development Board
* AMD/Xilinx Zynq-7000 SoC
* External CAN transceiver
* External DAC and RF front end for upconversion hardware
* Vivado / Vitis development environment

The hardware platform may evolve as the project progresses.

---

## Potential Repository Structure

```text
.
├── rtl/            # VHDL source files
├── constraints/    # FPGA pin constraints
├── sim/            # Testbenches and simulation
├── vitis/          # Embedded software
├── docs/           # Documentation and notes
└── README.md

```text