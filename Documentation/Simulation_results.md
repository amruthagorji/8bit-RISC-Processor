# Simulation Results

## Overview

Functional verification of the 8-bit RISC Processor was performed using Vivado Simulator.

Each RTL module was verified individually before full CPU integration.

---

# Register File Verification

### Objective

Verify:

* Register write operation
* Register read operation
* Reset functionality
* Constant zero register behavior

### Result

The register file successfully stored and retrieved data values while maintaining R0 as a constant zero register.

### Waveform

![Register File Waveform](../Simulation/Register_file_waveform.jpeg)

---

# Instruction Memory Verification

### Objective

Verify:

* Correct instruction storage
* Correct instruction fetch
* Address-to-instruction mapping

### Result

Instruction memory correctly returned the programmed instruction corresponding to each address.

### Waveform

![Instruction Memory Waveform](../Simulation/instruction_mem_waveform.jpeg)

---

# Decoder Verification

### Objective

Verify instruction decoding into:

* Opcode
* Source Registers
* Destination Register
* Immediate Value

### Result

The decoder successfully extracted all instruction fields according to the ISA specification.

### Waveform

![Decoder Waveform](../Simulation/decoder_waveform.jpeg)

---

# Control Unit Verification

### Objective

Verify generation of:

* ALU control signals
* Register write enable
* Branch control
* Memory control signals

### Result

Control signals matched the expected outputs for all supported instructions.

### Waveform

![Control Unit Waveform](../Simulation/control_unit_waveform.jpeg)

---

# Fetch Unit Verification

### Objective

Verify:

* Program Counter operation
* Sequential instruction fetch
* PC increment logic

### Result

The fetch unit successfully generated instruction addresses and retrieved instructions from memory.

### Waveform

![Fetch Waveform](../Simulation/fetch_waveform.jpeg)

---

# Execute Unit Verification

### Objective

Verify:

* ALU operations
* Immediate operations
* Register writeback
* Branch signal generation

### Result

The execute stage correctly performed arithmetic and logical operations and generated appropriate status signals.

### Waveform

![Execute Waveform](../Simulation/execute_waveform.jpeg)

---

# CPU Verification

### Objective

Verify complete processor operation including:

* Instruction fetch
* Decode
* Execute
* Writeback
* Branch handling

### Result

The integrated CPU successfully executed the programmed instruction sequence and produced the expected outputs.

### Waveform

![CPU Waveform](../Simulation/cpu_waveform.jpeg)

---

# Conclusion

All RTL modules and the complete CPU design passed functional simulation.

The design is now ready for:

1. FPGA Implementation
2. RTL Synthesis
3. ASIC Design Flow
4. Physical Design and GDSII Generation
