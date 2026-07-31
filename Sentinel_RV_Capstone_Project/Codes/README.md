# Sentinel-RV Code Directory Specification

Welcome to the **Codes/** directory of the **Sentinel-RV Capstone Project**. This directory contains all hardware design modules and software applications required to synthesize, program, and operate the secure **RISC-V System-on-Chip (SoC)**.

The project is organized into two main sections:

```
Codes/
├── Verilog/   # Hardware description modules, testbenches, constraints, and Vivado project files
└── Python/    # Desktop GUI applications, live sensor monitoring, and SD card utilities
```

---

# ⚡ Verilog Hardware Modules (`Verilog/`)

This directory contains the complete **32-bit RISC-V hardware design** written in Verilog HDL.

## 📌 Top-Level Core Modules

### `sentinel_rv_board_top.v`

**Description**

* Top-level FPGA board wrapper module.
* Connects physical FPGA peripherals (clock, switches, LEDs, keypad, LCD, and SD card) to the internal SoC.
* Handles board-level initialization and mirrors slide switch status to LEDs.

---

### `sentinel_rv_top.v`

**Description**

* Main System-on-Chip integration module.
* Connects the RISC-V processor, Block RAM, security subsystem, and peripheral controllers through the MMIO bus.
* Manages system memory mapping, keypad shortcuts, and 7-segment display multiplexing.

---

### `picorv32.v`

### `picorv32_wrapper.v`

**Description**

* 32-bit PicoRV32 RISC-V processor implementation.
* Executes embedded firmware directly from on-chip Block RAM.
* Controls system security operations and telemetry processing.

---

### `simple_bram_memory.v`

**Description**

* 4 KB on-chip Block RAM.
* Stores executable firmware and temporary telemetry data.
* Enables single-cycle memory access without external DRAM.

---

# 🛡️ Security & Cryptography Subsystem

### `sentinel_rv_security.v`

**Description**

* Central hardware security engine.
* Integrates cryptographic modules, nonce generation, replay protection, and tamper detection.
* Protects telemetry packets from replay attacks and unauthorized access.

---

### `aes128_encrypt.v`

**Description**

* Hardware implementation of AES-128 encryption.
* Performs complete encryption in approximately 10 rounds.
* Encrypts telemetry packets and SD card audit records.

---

### `nonce_generator.v`

### `replay_protection.v`

**Description**

* Hardware nonce generator and replay protection module.
* Generates unique cryptographic nonces for every telemetry packet.
* Prevents replay and packet injection attacks.

---

### `security_controller.v`

**Description**

* Security state machine.
* Monitors tamper detection signals, voltage glitches, and unauthorized commands.
* Activates buzzer/alarm during intrusion events.

---

# 💾 Storage & Peripheral Controllers

### `audit_log_writer.v`

### `sd_logger.v`

**Description**

* Micro-SD audit logging subsystem.
* Formats encrypted audit records.
* Stores security logs through the SPI interface.
* Provides permanent tamper-evident event storage.

---

### `sevenseg_driver.v`

**Description**

* Multiplexed 4-digit seven-segment display driver.
* Displays temperature, distance, and voltage values.
* Supports multiple sensor display modes.

---

### `lcd_controller.v`

### `lcd_driver.v`

**Description**

* HD44780 16×2 LCD driver.
* Displays user roles such as:

  * ADMIN
  * RESEARCH
  * INTERN
* Provides real-time system status.

---

### `keypad_scan.v`

### `keypad_decoder.v`

**Description**

* 4×4 matrix keypad interface.
* Scans keypad inputs and converts them into ASCII keycodes.
* Supports hardware shortcuts for display selection, buzzer testing, and relay control.

---

### `dht11_controller.v`

### `hc_sr04_controller.v`

**Description**

* Interfaces for environmental sensors.
* Reads:

  * Temperature
  * Humidity
  * Distance
* Supplies real-time data to the telemetry system.

---

### `mcp3202_sampler.v`

### `xadc_monitor.v`

**Description**

* External ADC and internal FPGA XADC monitoring modules.
* Measures analog voltage rails and FPGA die temperature.
* Detects brownout conditions and overheating.

---

### `sentinel_rv.xdc`

**Description**

* Xilinx Design Constraints file.
* Maps FPGA I/O ports to the Artix-7 package pins.
* Defines:

  * Pin assignments
  * LVCMOS33 I/O standards
  * 24 MHz clock constraints

---

# 🐍 Python Desktop Applications (`Python/`)

Desktop applications developed using **Python (PyQt/Tkinter)** for system monitoring and secure communication.

---

### `App1_FPGA_Control_And_Sensors.py`

**Description**

* Main FPGA desktop control application.
* Connects to the FPGA through USB/UART (115200 baud).
* Receives encrypted telemetry packets.
* Displays live sensor graphs including:

  * Temperature
  * Humidity
  * Distance
  * Voltage
* Automatically sends user-role packets (0xA1, 0xA2, 0xA3) to synchronize the FPGA LCD.
* Plays an alarm siren when intrusion events are detected.

---

### `App2_SD_Card_Reader.py`

**Description**

* SD card audit log reader utility.
* Reads raw Micro-SD sectors directly from Windows physical drives.
* Decrypts AES-encrypted audit records.
* Displays historical security logs.
* Requires Administrator (UAC) privileges for raw disk access.

---

# 📂 Project Directory Structure

```text
Codes/
│
├── Verilog/
│   ├── sentinel_rv_board_top.v
│   ├── sentinel_rv_top.v
│   ├── picorv32.v
│   ├── picorv32_wrapper.v
│   ├── simple_bram_memory.v
│   ├── sentinel_rv_security.v
│   ├── aes128_encrypt.v
│   ├── nonce_generator.v
│   ├── replay_protection.v
│   ├── security_controller.v
│   ├── audit_log_writer.v
│   ├── sd_logger.v
│   ├── sevenseg_driver.v
│   ├── lcd_controller.v
│   ├── lcd_driver.v
│   ├── keypad_scan.v
│   ├── keypad_decoder.v
│   ├── dht11_controller.v
│   ├── hc_sr04_controller.v
│   ├── mcp3202_sampler.v
│   ├── xadc_monitor.v
│   └── sentinel_rv.xdc
│
└── Python/
    ├── App1_FPGA_Control_And_Sensors.py
    └── App2_SD_Card_Reader.py
```
