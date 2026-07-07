# Full Adder using Half Adders in Verilog

## Overview
This repository contains a structural level Verilog implementation of a 1-bit Full Adder. The full adder is constructed by instantiating two Half Adder modules and an OR gate. A comprehensive testbench is also included to verify the logic.

## Files Included
* **`full_adder.v`**: The main design file containing both the `half_adder` and `full_adder` modules.
* **`full_adder_tb.v`**: The testbench file that iterates through all 8 possible input combinations to verify the truth table.

## Simulation
The testbench applies all possible 3-bit input combinations (from `000` to `111`) using a `for` loop with a 10ns delay between each test vector. 

### Tools Used
* Language: Verilog HDL
* IDE / Simulator: [Insert your tool here, e.g., Xilinx Vivado / ModelSim / Icarus Verilog]
