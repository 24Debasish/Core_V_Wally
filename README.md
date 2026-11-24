
# Physical Design Implementation of CORE-V Wally

A study of the CORE-V Wally RISC-V SoC architecture and its key design considerations, including bus connectivity, memory, peripherals, power intent, clocking, PVT corners, synthesis, and top-level integration.

## Objective

The objective of this project is to study the CORE-V Wally RISC-V system and understand the major components and design considerations involved in integrating the processor core into a complete System-on-Chip (SoC).

## Project Overview

RISC-V is an open-source instruction set architecture (ISA) based on Reduced Instruction Set Computing (RISC) principles. CORE-V is a family of open-source RISC-V cores curated within the OpenHW Foundation ecosystem.

This project explores the CORE-V Wally architecture and its supporting SoC components, with emphasis on interconnection architecture, memory, peripheral interfaces, power management, clock specifications, PVT corners, synthesis, and design hierarchy.

## Architecture and Design Components

### 1. RISC-V and CORE-V

- **RISC-V:** An open-source ISA that supports flexible processor design.
- **CORE-V:** A family of open-source RISC-V cores developed within the OpenHW Foundation ecosystem.

### 2. Bus Architecture

The SoC uses two main bus interfaces:

| Bus / Component | Purpose |
|---|---|
| AHB | Used mainly for core connections. |
| APB | Used mainly for peripheral connections. |
| AHB-to-APB Bridge | Supports communication between core-side and peripheral-side buses. |
| System Controller | Manages the interconnections. |

### 3. Memory Components

- **RAM:** Provides fast access to data during processor operation. RAM is volatile and requires power to retain its contents.
- **EEPROM:** Provides non-volatile storage and retains data without power. EEPROM may be shut down when it is not required.

### 4. Peripheral Interfaces and Signals

The following GPIO signal allocations are covered:

| GPIO Range | Interface / Function | Signals |
|---|---|---|
| GPIO[31:30] | UART | 2 |
| GPIO[29:22] | SPI | 8 |
| GPIO[21:0] | General I/O | Described as 8-bit signals in the presentation |

### 5. Power Management (UPF)

Power intent is defined using an extension of the Tool Command Language (Tcl).

The power-management components include:

- Power Domains
- Power Supply Network
- Power State Table
- Isolation Strategies
- Retention Strategies
- Level Shifter Strategies
- Repeater Strategies

### 6. Clock Specifications

| Clock | Domain / Connection | Period | Bus |
|---|---|---|---|
| CLK | Top Module | — | — |
| EDGE_CLK | Core | 4 ns | AHB |
| T_clk | Uncore | 6 ns | APB |

### 7. PVT Corners

PVT represents **Process, Voltage, and Temperature** variations. These corners are used for timing and reliability verification.

- **LVT:** Low Threshold Voltage.
- **HVT:** High Threshold Voltage.
- **PVT:** Process, Voltage, and Temperature variations.

### 8. Synthesis Flow

Synthesis is the process of converting high-level hardware descriptions (RTL) into a gate-level netlist while optimizing the design for performance, area, and power constraints.

### 9. Wrapper Module

A wrapper module serves as a boundary between an embedded core and the surrounding chip logic.

Its key functionalities include:

- Supporting observability and controllability of core inputs and outputs during testing.
- Isolating the core from external logic and preventing unwanted signal interference.
- Enabling reuse of previously generated test patterns at the top level.
- Providing a standardized interface for Test Access Mechanisms (TAM) to transfer test data between chip-level and core-level logic.

### 10. Top Module

The top module represents the highest level of the design hierarchy.

Its primary responsibilities include:

- Connecting all submodules and interfaces.
- Integrating the complete SoC design.
- Managing the overall design hierarchy.

## Topics Covered

- RISC-V and CORE-V fundamentals
- CORE architecture and SoC bus connectivity
- AHB, APB, and AHB-to-APB bridging
- RAM and EEPROM
- GPIO, UART, and SPI interfaces
- UPF-based power management
- Clock specifications and clock periods
- PVT corners, including LVT and HVT
- RTL-to-gate-level synthesis
- Wrapper modules and test access mechanisms
- Top-level SoC integration

## Author

**Debasish Ghosh**

- **Email:** your-email@example.com
- **LinkedIn:** https://www.linkedin.com/in/your-profile/

