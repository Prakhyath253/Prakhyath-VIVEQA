# Day 08: Edge Detector Design

## Overview
This folder contains the Verilog HDL implementation of a digital Edge Detector. The circuit is designed to monitor an incoming signal and generate a one-cycle pulse whenever a transition (edge) occurs. It utilizes a D Flip-Flop to store the previous state of the signal, allowing for real-time comparison against the current state.

## Project Files

*   **`edge_detector.v`**: The core hardware design module.
*   **`tb_edge_detector.v`**: The testbench used for simulation.

## Module Descriptions

### `edge_detector.v` (Core Design)
This module is responsible for detecting transitions on the input signal. It works by delaying the input signal by one clock cycle using a D Flip-Flop. Combinational logic then compares the live input against this delayed (previous) state to trigger the appropriate output flags:
*   **Positive Edge:** Triggers when the signal transitions from 0 to 1.
*   **Negative Edge:** Triggers when the signal transitions from 1 to 0.
*   **Any Edge (Both):** Triggers on any state change (either rising or falling).

### `tb_edge_detector.v` (Testbench)
This file provides the simulation environment to validate the edge detection logic. The testbench verifies the module's accuracy by:
*   Generating a continuous system clock.
*   Applying an initial reset sequence.
*   Injecting various input signal transitions (both fast and slow).
*   Monitoring the outputs to ensure the positive, negative, and both-edge flags assert correctly for exactly one clock cycle.
