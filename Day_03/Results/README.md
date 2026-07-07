# 4-Bit Ripple Carry Adder/Subtractor in Verilog

## Overview
This repository contains a structural level Verilog implementation of a 4-bit Ripple Carry Adder/Subtractor. The circuit uses a control signal (`m`) to switch between addition and subtraction operations using the 2's complement method.

### How It Works
* **Addition (`m = 0`)**: The XOR gates act as transparent buffers, passing the `b` inputs directly to the full adders. The initial carry-in is `0`.
* **Subtraction (`m = 1`)**: The XOR gates invert the `b` inputs (1's complement), and the initial carry-in is `1`. This effectively creates a 2's complement of `b`, allowing the circuit to perform `a - b`.

## Files Included
* **`adder_4bit.v`**: The main design file containing the `half_adder`, `full_adder`, and `adder_4bit` structural modules.
* **`tb_adder_4bit.v`**: The testbench file that verifies the logic for both addition and subtraction using various test cases.

## Simulation
The testbench sequentially applies 4 test vectors for addition mode, followed by the same 4 vectors for subtraction mode, using a 10ns delay step. Output is continuously logged using the `$monitor` system task.

### Tools Used
* Language: Verilog HDL
* IDE / Simulator: [Insert your tool here, e.g., Xilinx Vivado / ModelSim]# 4-Bit Ripple Carry Adder/Subtractor in Verilog
