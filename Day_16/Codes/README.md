# Day 16 - Mealy Sequence Detector

This directory contains the Verilog HDL implementation of a **Mealy Sequence Detector** designed to detect the binary sequence **111** using D Flip-Flops.

## Files

- `Sequence_Detector.v`
- `seq_det_tb.v`
- `Sequence_Detector.xdc`

## Description

### `Sequence_Detector.v`
This file includes the complete hardware design for the Mealy sequence detector along with the D Flip-Flop module. The D Flip-Flops are used to store the present state, while the combinational logic determines the next state and generates the output. The detector asserts the output HIGH whenever the input sequence **111** is identified.

### `seq_det_tb.v`
This testbench is used to simulate and validate the functionality of the sequence detector. It applies reset conditions and different serial input sequences to verify that the detector correctly recognizes the target sequence and produces the expected output.

### `Sequence_Detector.xdc`
This Xilinx Design Constraints (XDC) file assigns the FPGA board pins for the **24 MHz clock**, **reset button**, **serial input switch**, and **output LED**. It also configures the required **LVCMOS33** I/O standard for successful synthesis and implementation on the FPGA.
