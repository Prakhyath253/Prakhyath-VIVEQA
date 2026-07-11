# Day 10: 8-Bit Arithmetic Logic Unit (ALU)

## Overview
This folder contains the Verilog HDL implementation for a combinational 8-bit Arithmetic Logic Unit (ALU). The design extracts two 4-bit operands (`A` and `B`) from hardware slide switches and executes one of 16 distinct arithmetic or logical operations based on a keypad selection. The computed result is then driven to the onboard LEDs.

## Project Files

*   **`alu.v`**
    The core hardware description module for the ALU. It implements the combinational logic required to perform the operations. The module reads an 8-bit switch bus (split into two 4-bit operands) and uses a 16-bit input bus from a keypad to determine which arithmetic or logical operation to execute. The result is output to an 8-bit LED bus.

*   **`alu_tb.v`**
    The simulation testbench. It verifies the ALU's functionality by supplying various test vectors for the operands and cycling through all 16 keypad command inputs, ensuring the simulated LED outputs match the expected mathematical and logical results.

*   **`alu.xdc`**
    The Xilinx Design Constraints (XDC) file for physical FPGA implementation. This file handles the hardware pin routing and electrical standards:
    *   **Operands:** Maps slide switches to `push[7:0]`.
    *   **Operation Select:** Maps keypad buttons to `key[15:0]`.
    *   **Result:** Maps the output register to the LEDs via `led[7:0]`.
    *   **I/O Standard:** Configures all mapped hardware pins to use the `LVCMOS33` voltage standard.
