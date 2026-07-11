# Day 09: 16-to-4 Priority Encoder (Hexadecimal to Binary Converter)

## Overview
This folder contains the Verilog HDL implementation and supporting files for a 16-to-4 Priority Encoder. The circuit functions as a hexadecimal-to-binary converter, translating a 16-bit one-hot input vector into its corresponding 4-bit binary representation.

## Project Files

*   **`hex_to_binary.v`**
    The core hardware description module. It implements the 16-to-4 encoding logic using a combinational `case` statement to map the one-hot input directly to a 4-bit binary output.
    
*   **`tb_hex_to_binary.v`**
    The simulation testbench. It verifies the logic of the encoder by cycling through valid one-hot input combinations as well as edge cases and invalid states, ensuring the output correctly matches the expected behavior.

*   **`hex_to_binary.xdc`**
    The Xilinx Design Constraints (XDC) file. This is used for physical FPGA synthesis, mapping the logical inputs (switches) and outputs (LEDs) to the actual FPGA package pins and setting the required I/O standard (`LVCMOS33`).
