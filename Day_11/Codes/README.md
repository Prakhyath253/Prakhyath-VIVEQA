# Day 11: Switch-to-LED Interface (Basys 3 FPGA)

## Overview
This folder contains the Verilog HDL implementation for a fundamental hardware interface on the Basys 3 FPGA board. The design demonstrates direct combinational routing by mapping the onboard slide switches directly to the onboard LEDs, providing immediate visual feedback for hardware inputs.

## Project Files

*(Note: File names have been standardized to match the project structure)*

*   **`switch_to_led.v`**
    The core hardware description module. It implements an 8-bit interface where eight slide switches (`switch[7:0]`) are wired directly to eight LEDs (`led[7:0]`) using a continuous `assign` statement. Because this is purely combinational logic, toggling any switch instantly updates the state of its corresponding LED.

*   **`switch_to_led_tb.v`**
    The simulation testbench. It verifies the combinational mapping by driving various 8-bit test patterns into the switch inputs and confirming that the LED outputs mirror the inputs precisely without delay.

*   **`switch_to_led.xdc`**
    The Xilinx Design Constraints (XDC) file. This handles the physical synthesis mapping for the Basys 3 board:
    *   Maps the physical hardware slide switches to the logical `switch[7:0]` input port.
    *   Maps the physical hardware LEDs to the logical `led[7:0]` output port.
    *   Configures the required `LVCMOS33` I/O voltage standard for all routed FPGA pins.
