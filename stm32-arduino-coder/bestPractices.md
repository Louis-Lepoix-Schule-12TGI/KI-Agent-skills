# Best Practices and Project Manifest - STM32 Nucleo

This document serves as the single source of truth for this project's hardware, software constraints, and development standards. **It must be updated whenever a change is made to the physical setup or core library dependencies.**

## ⚙️ Hardware Manifest (Required Input)
*   **Microcontroller:** STM32 Nucleo 64 L152RE.
*   **Primary Peripherals:** [USER MUST LIST ALL DEVICES HERE]
    *   *Example: LCD Screen:* Requires interfacing via [Protocol, e.g., I2C]. Needs physical address [0xXX].
    *   *Example: Sensor:* Uses UART communication at [Baud Rate].
*   **Memory/Power:** Note any known SRAM leakage points or power-intensive components that require sleep modes.

## 💻 Software Manifest (Required Input)
*   **Toolchain:** Arduino IDE Environment (C/C++).
*   **Core Libraries:** List all necessary libraries and their version constraints (e.g., `LiquidCrystal_I2C` v1.x). *Do not rely on external, undocumented functions.*
*   **Timing Policy:** Primary timing mechanism shall be interrupt-driven logic. `delay()` is strictly reserved for initial prototyping only.

## ⚡ Coding Standards & Constraints
1.  **Pin Mapping:** All GPIO pin usage must be explicitly declared in the Manifest and cross-referenced in the wiring guide to prevent conflicts.
2.  **Interrupts:** When using interrupts, ensure all ISRs are minimal and execute as quickly as possible to maintain system responsiveness.
3.  **Data Integrity:** For communication buses (I2C/SPI), implement necessary error checking (e.g., ACK checks, CRC calculation) where the protocol requires it.

***REMINDER: The model will automatically prompt for updates to this file if critical dependencies are mentioned in a new request.***
