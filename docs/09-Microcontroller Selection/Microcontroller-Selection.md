---
title: Microcontroller Selection
tags:
- tag1
- tag2
---


# Microcontroller Selection

## Overview

The selected microcontroller for this subsystem is the **Microchip PIC18F47K42** (surface-mount version). This device was chosen to support UART communication for the team daisy chain network, SPI communication for the stepper motor driver, PWM outputs for servo control, and GPIO inputs for limit switch detection. The PIC18F47K42 provides sufficient hardware resources while maintaining compatibility with MPLAB X and MCC Melody.

---

## Project-Specific Resource Requirements

Based on the electrical block diagram, the following hardware resources are required:

- **1x UART** – Daisy chain communication
- **1x SPI peripheral** – Stepper motor driver control
- **3x PWM outputs** – Shoulder, elbow, and wrist servos
- **1x Digital input (GPIO)** – Homing switch
- **ICSP programming interface** – MPLAB Snap
- **Additional GPIO** – Fault input and debugging LEDs

The PIC18F47K42 supports all of these peripherals simultaneously without resource conflicts.

---

## PIC18F47K42 Key Features Relevant to Design

- 3.3V operation (compatible with logic rail)
- Multiple UART modules
- Multiple SPI modules
- Multiple CCP/PWM modules
- Sufficient GPIO pins for subsystem control
- Supported in MPLAB X with MCC Melody

The device provides excess hardware resources beyond minimum requirements, allowing room for future expansion if necessary.

---

## Peripheral Compatibility Check

### Stepper Motor Driver (DRV8434SRGER)
- SPI-compatible
- Accepts 3.3V logic signals from PIC
- STEP/DIR and control signals supported

### Servos (CN0193 & Adafruit 2307)
- Controlled via PWM
- Operate from 5V rail
- PWM signals generated directly from PIC

### Homing Switch (D2F-01)
- Connected to GPIO input
- Uses pull-up configuration
- Logic-level detection (3.3V safe)

No known hardware conflicts exist between the PIC and selected peripherals.

---

## MCC Configuration

An MPLAB X project has been created using the PIC18F47K42. MCC Melody was used to configure:

- UART module
- SPI module
- PWM modules
- GPIO inputs and outputs

All required pins were successfully allocated without conflicts. No resource errors were reported during configuration.

(Screenshot of MCC configuration to be added.)

---

## Final Microcontroller Choice

**Selected Microcontroller:** PIC18F47K42 (Surface-Mount)

### Rationale

The PIC18F47K42 was selected because it satisfies all subsystem communication and control requirements while maintaining compatibility with team standards. It provides sufficient SPI, UART, PWM, and GPIO resources without exceeding design complexity. The device is fully supported within MPLAB X and MCC, making development and debugging efficient for this subsystem.
