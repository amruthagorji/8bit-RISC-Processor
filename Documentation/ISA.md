# Instruction Set Architecture (ISA)

## Overview

The 8-bit RISC Processor uses a custom Instruction Set Architecture (ISA) designed for educational and ASIC implementation purposes.

The processor supports arithmetic, logical, immediate, memory, branch, and shift instructions using a 16-bit instruction format.

---

# Processor Specifications

| Parameter               | Value           |
| ----------------------- | --------------- |
| Data Width              | 8 bits          |
| Instruction Width       | 16 bits         |
| Register Count          | 8               |
| Register Address Width  | 3 bits          |
| Instruction Memory Size | 16 Instructions |
| Data Memory Size        | 256 Bytes       |

---

# Register Organization

The processor contains 8 general-purpose registers.

| Register | Description            |
| -------- | ---------------------- |
| R0       | Constant Zero Register |
| R1       | General Purpose        |
| R2       | General Purpose        |
| R3       | General Purpose        |
| R4       | General Purpose        |
| R5       | General Purpose        |
| R6       | General Purpose        |
| R7       | General Purpose        |

---

# Instruction Formats

## R-Type Format

Used for arithmetic, logical, and shift operations.

| Opcode | RS1    | RS2    | RD     | Unused |
| ------ | ------ | ------ | ------ | ------ |
| 4 bits | 3 bits | 3 bits | 3 bits | 3 bits |

### Bit Mapping

| Bits    | Field  |
| ------- | ------ |
| [15:12] | Opcode |
| [11:9]  | RS1    |
| [8:6]   | RS2    |
| [5:3]   | RD     |
| [2:0]   | Unused |

---

## I-Type Format

Used for immediate, memory, and branch instructions.

| Opcode | RS1    | RD     | Immediate |
| ------ | ------ | ------ | --------- |
| 4 bits | 3 bits | 3 bits | 6 bits    |

### Bit Mapping

| Bits    | Field     |
| ------- | --------- |
| [15:12] | Opcode    |
| [11:9]  | RS1       |
| [8:6]   | RD        |
| [5:0]   | Immediate |

---

# Instruction Encoding

## Arithmetic Instructions

| Instruction | Opcode | Description    |
| ----------- | ------ | -------------- |
| ADD         | 0000   | RD = RS1 + RS2 |
| SUB         | 0001   | RD = RS1 - RS2 |

---

## Logical Instructions

| Instruction | Opcode | Description    |
| ----------- | ------ | -------------- |
| AND         | 0010   | RD = RS1 & RS2 |
| OR          | 0011   | RD = RS1 | RS2 |
| XOR         | 0100   | RD = RS1 ^ RS2 |

---

## Immediate Instructions

| Instruction | Opcode | Description          |
| ----------- | ------ | -------------------- |
| ADDI        | 0101   | RD = RS1 + Immediate |
| SUBI        | 0110   | RD = RS1 - Immediate |
| LI          | 0111   | RD = Immediate       |

---

## Branch Instructions

| Instruction | Opcode | Description          |
| ----------- | ------ | -------------------- |
| BEQ         | 1000   | Branch if RS1 == RS2 |

Branch Condition:

```text
if (RS1 == RS2)
    PC = PC + Immediate;
else
    PC = PC + 1;
```

---

## Shift Instructions

| Instruction | Opcode | Description         |
| ----------- | ------ | ------------------- |
| SLL         | 1001   | Logical Left Shift  |
| SRL         | 1010   | Logical Right Shift |

---

## Memory Instructions

| Instruction | Opcode | Description           |
| ----------- | ------ | --------------------- |
| LOAD        | 1011   | RD = Memory[Address]  |
| STORE       | 1100   | Memory[Address] = RS2 |

---

# ALU Control Encoding

| ALU Control | Operation |
| ----------- | --------- |
| 000         | ADD       |
| 001         | SUB       |
| 010         | AND       |
| 011         | OR        |
| 100         | XOR       |
| 101         | SLL       |
| 110         | SRL       |

---

# Example Instructions

### ADD R3, R1, R2

```text
Opcode = 0000
RS1    = 001
RS2    = 010
RD     = 011
```

Machine Code:

```text
0000_001_010_011_000
```

---

### ADDI R3, R1, #3

```text
0101_001_011_000011
```

---

### LI R2, #5

```text
0111_000_010_000101
```

---

### BEQ R1, R2, +2

```text
1000_001_010_000010
```

---

# Design Goals

The ISA was designed to:

* Maintain simple hardware implementation
* Enable complete RTL-to-GDSII design flow
* Support FPGA implementation
* Demonstrate processor design concepts
* Serve as a learning platform for computer architecture and VLSI design
