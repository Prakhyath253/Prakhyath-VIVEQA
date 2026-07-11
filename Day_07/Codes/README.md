# Day 07: Multi-Mode Flip-Flop Design

## Overview
This folder contains the Verilog HDL implementation of a configurable flip-flop circuit. The design demonstrates how to build D, T, and JK Flip-Flops by utilizing a single base D Flip-Flop paired with a 3:1 Multiplexer to route the correct logic.

## Project Files

*   **`Top.v`**: The main design module.
*   **`tb_Top.v`**: The testbench for simulation and verification.

## Module Descriptions

### `Top.v` (Core Design)
This module acts as a universal flip-flop. Depending on the 2-bit select signal (`m`), a 3:1 multiplexer chooses which logic path feeds into the common D Flip-Flop:

*   **D Flip-Flop:** The input is routed directly to the flip-flop.
*   **T Flip-Flop:** Implemented using the XOR logic equation $D = T \oplus Q$.
*   **JK Flip-Flop:** Implemented using the combinational equation $D = J\overline{Q} + \overline{K}Q$.

### `tb_Top.v` (Testbench)
This file provides the simulation environment to verify the core module. It tests all three flip-flop modes by:
*   Generating the system clock.
*   Applying the reset sequences.
*   Cycling through different input combinations for the D, T, and JK inputs.
*   Switching the 2-bit multiplexer selector to verify the correct output behavior for each mode.
