# 8-Bit RISC Processor with Runtime Workload Monitoring and Adaptive Frequency Scaling

## Overview

This project presents the design, verification, ASIC implementation, FPGA deployment, and architectural enhancement of a custom **8-Bit RISC Processor** developed using **Verilog HDL**.

The processor was designed from scratch and taken through a complete digital design flow including RTL development, functional verification, FPGA implementation, and ASIC physical design using **Cadence Genus** and **Cadence Innovus**.

To extend the capabilities of a conventional educational RISC processor, a **Runtime Workload Monitoring** subsystem and **Adaptive Frequency Scaling (AFS)** mechanism were implemented. The processor continuously monitors instruction execution patterns, classifies workload characteristics, and dynamically adjusts its operating frequency based on the dominant workload type.

This project demonstrates the complete journey from processor architecture design to hardware validation while incorporating runtime architectural optimization techniques inspired by modern processors and System-on-Chips (SoCs).

---

## FPGA & ASIC Implementation Highlights

### FPGA Hardware Validation

* Successfully implemented on Xilinx PYNQ-Z2 FPGA
* Real-time processor validation using onboard switches and LEDs
* Program Counter verification
* ALU verification
* Memory access verification
* Branch execution verification

### ASIC Physical Design

#### Routing

![Routing](ASIC_Flow/routing.png)

#### Post-Route Timing Verification

![Timing Verification](ASIC_Flow/innovus_timing.png)

---

## Project Highlights

### Processor Specifications

| Parameter              | Value           |
| ---------------------- | --------------- |
| Architecture           | Custom RISC     |
| Datapath Width         | 8-bit           |
| Instruction Width      | 16-bit          |
| Register Count         | 8 Registers     |
| Register Address Width | 3-bit           |
| Instruction Memory     | 16 Instructions |
| Data Memory            | 256 Bytes       |
| RTL Language           | Verilog HDL     |

---

## Key Features

### Processor Architecture

* Custom 8-Bit RISC Architecture
* Harvard-Style Memory Organization
* Single-Cycle Processor Design
* Arithmetic and Logical Operations
* Immediate Instructions
* Branch Instructions
* Shift Operations
* Data Memory Access

### Verification & Implementation

* Modular RTL Design
* Functional Verification
* FPGA Hardware Validation
* ASIC Physical Design Flow

### Architectural Enhancement

* Runtime Workload Monitoring
* Observation Window-Based Classification
* Adaptive Frequency Scaling (AFS)
* Dynamic Workload Mode Selection
* Runtime Clock Adaptation

---

## Supported Instructions

### Arithmetic Operations

* ADD
* SUB

### Logical Operations

* AND
* OR
* XOR

### Immediate Operations

* ADDI
* SUBI
* LI

### Shift Operations

* SLL
* SRL

### Memory Operations

* LOAD
* STORE

### Branch Operations

* BEQ

---

## Runtime Workload Monitoring

To enhance processor adaptability, a runtime workload monitoring subsystem was integrated into the processor.

The monitor continuously observes executed instructions and classifies processor activity into:

| Category         | Instructions                                     |
| ---------------- | ------------------------------------------------ |
| ALU Intensive    | ADD, SUB, AND, OR, XOR, ADDI, SUBI, LI, SLL, SRL |
| Memory Intensive | LOAD, STORE                                      |
| Branch Intensive | BEQ                                              |

Three hardware counters are maintained:

* alu_count
* mem_count
* branch_count

The processor operates using a fixed observation window. At the end of each window, the dominant workload type is identified and encoded into a workload mode.

### Workload Modes

| Mode | Description  |
| ---- | ------------ |
| 00   | ALU Heavy    |
| 01   | Memory Heavy |
| 10   | Branch Heavy |

Detailed Documentation:

📄 Documentation/Runtime_Workload_Monitoring_AFS.md

---

## Adaptive Frequency Scaling (AFS)

The Adaptive Frequency Scaling unit receives the workload classification and dynamically selects the processor clock divider.

### Frequency Scaling Policy

| Workload Mode | Operating State   | Divider |
| ------------- | ----------------- | ------- |
| 00            | High Performance  | 10      |
| 01            | Balanced Mode     | 20      |
| 10            | Power Saving Mode | 40      |

Operational Flow:

Instruction Stream
→ Workload Monitor
→ Workload Classification
→ Adaptive Frequency Scaling
→ Clock Divider
→ Processor Clock

---

## Verification Flow

### Module Verification

* ALU
* Register File
* Instruction Memory
* Decoder
* Control Unit
* Execute Unit

### System Verification

* CPU Integration Testing
* Instruction Execution Verification
* Branch Verification
* Memory Access Verification
* Runtime Workload Monitoring Verification
* Adaptive Frequency Scaling Verification

### Tools Used

* Vivado Simulator
* XSim
* Cadence Xcelium

---

## FPGA Implementation

### Platform

* Xilinx PYNQ-Z2
* XC7Z020 FPGA

### Hardware Validation

Successfully validated:

* Program Counter Operation
* ALU Outputs
* Immediate Generation
* Memory Access
* Branch Execution
* Runtime Workload Classification
* Adaptive Frequency Scaling

---

## ASIC Implementation Flow

### Logic Synthesis

Tool:

* Cadence Genus

Generated Reports:

* Timing Report
* Area Report
* Power Report

### Physical Design

Tool:

* Cadence Innovus

Implementation Stages:

* Floorplanning
* Power Planning
* Placement
* Clock Tree Synthesis (CTS)
* Routing
* Timing Verification
* Connectivity Verification
* Geometry Verification

---

## Physical Design Results

### Synthesis Results

| Metric            | Value        |
| ----------------- | ------------ |
| Cell Area         | 3775.560 µm² |
| Timing Violations | 0            |
| Timing Status     | Passed       |

### Power Results

| Metric      | Value            |
| ----------- | ---------------- |
| Total Power | 3.85389 × 10⁻⁴ W |

### Physical Verification

* DRC Violations: 0
* Geometry Violations: 0
* Connectivity Verification: Passed
* Timing Verification: Passed

---

## Repository Structure

```text
8bit-RISC-Processor/
│
├── RTL/
├── Testbench/
├── Simulation/
├── FPGA/
├── ASIC_Flow/
│
├── Runtime_workload_monitoring_AFS/
│
├── Documentation/
│   ├── ISA.md
│   ├── RTL_Design.md
│   ├── Simulation_Results.md
│   ├── FPGA_Implementation.md
│   ├── ASIC_Flow.md
│   └── Runtime_Workload_Monitoring_AFS.md
│
└── README.md
```

---

## Skills Demonstrated

### Digital Design

* Verilog HDL
* RTL Design
* Processor Architecture
* Datapath Design
* Control Unit Design

### Computer Architecture

* Instruction Set Design
* Runtime Workload Analysis
* Dynamic Frequency Scaling
* Processor Optimization

### Verification

* Functional Verification
* Testbench Development
* Simulation Debugging
* Hardware Validation

### Physical Design

* Logic Synthesis
* Floorplanning
* Power Planning
* Placement
* Routing
* Static Timing Analysis

### EDA Tools

* Vivado
* Cadence Genus
* Cadence Innovus
* Cadence Xcelium

---

## Future Work

* Clock Gating Integration
* Dynamic Voltage and Frequency Scaling (DVFS)
* Performance Counter Integration
* Workload Prediction Algorithms
* Calibre DRC
* LVS Verification
* Signoff STA
* GDSII Signoff

---

## Author

**Amrutha Gorji**

B.Tech Electronics and Communication Engineering
SASTRA Deemed University

Research Intern – NIT Warangal

Digital VLSI | RTL Design | ASIC Design | FPGA Design | Computer Architecture
