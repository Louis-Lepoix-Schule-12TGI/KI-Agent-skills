---
name: stm32-arduino-coder
description: Generates robust, constrained code snippets for embedded systems using STM32 microcontrollers (STM32 Nucleo). Use when developing or debugging firmware for a specific hardware platform connected to the Arduino IDE workflow.
---

# Embedded Coder: STM32/Arduino Protocol Skill

## Overview
This skill guides the generation of reliable and efficient firmware sketches (`.ino` format) for embedded systems built around the **STM32 Nucleo 64 L152RE** microcontroller, adhering strictly to the Arduino IDE workflow while maintaining low-level control typical of C programming. The core principle is **Defensive Coding**: assume uncertainty until proven otherwise through research.

## Mandatory First Step: Peripheral Manifest Generation
Before writing any code, the model **MUST** prompt the user for a comprehensive **Peripheral Manifest**. This manifest must include:
1.  **Device List:** A list of *all* external chips or sensors connected.
2.  **Connection Details:** For each device, specify its connection type (I2C, SPI, UART), the specific bus/port, and the required addresses/speeds.

## Core Workflows

### 1. Code Generation (The `.ino` Sketch)
*   **Structure:** All code must be wrapped within standard Arduino `setup()` and `loop()` functions.
*   **Principle:** Favor **Interrupts over Polling**. Use interrupt service routines (ISRs) for time-critical or asynchronous events to maintain deterministic timing. The `delay()` function should only be used in clearly labeled 'Prototyping/Non-Critical' sections.
*   **Safety:** Always include comments advising on memory usage, power consumption concerns, and necessary watchdog timer resets.

### 2. Pseudo-Code & Explanation (The Conceptual Layer)
Use this when the user is designing the architecture *before* writing code. This layer focuses on data flow diagrams and state machines to resolve logic ambiguities.

### 3. Wiring Guide Generation
This output must be a clear, markdown table detailing:
| Component | Pin Name (e.g., SDA/SCL) | STM32 Nucleo Pin (GPIO #) | Connection Type | Notes |
| :--- | :--- | :--- | :--- | :--- |
| Sensor A | VCC $\rightarrow$ 3.3V | N/A | Power | Must confirm voltage level. |

## Advanced Research Protocol (ANTI-HALLUCINATION MANDATE)
If any piece of information (e.g., a library function, an I2C address, a pin mapping, or a timing constraint) is uncertain, the model **MUST** execute the following multi-step research process before stating a fact:
1.  `web_search(query="specific topic")`
2.  *Critically Evaluate:* Analyze all search results and select the 2-3 most authoritative URLs (e.g., official datasheets, trusted forum posts).
3.  For *each* selected URL, execute `fetch_content(url=...)`.
4.  Synthesize a final answer based ONLY on the converged evidence from these fetched documents.

## Best Practices & Standards (`bestPractices.md` Reference)
All users MUST be prompted to consult or create a corresponding `bestPractices.md` file detailing their unique setup parameters (e.g., specific global constants, system clock settings, required library versions).
