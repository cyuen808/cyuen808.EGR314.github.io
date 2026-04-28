---
title: Microcontroller Selection
tags:
- tag1
- tag2
---


# Microcontroller Selection

## Overview

The selected microcontroller for this subsystem is the ESP32-S3-WROOM-1. This device was chosen to support UART communication for the team daisy chain network, SPI communication for the stepper motor driver, PWM outputs for servo control, and GPIO inputs for limit switch detection.

The ESP32-S3 provides high performance, integrated wireless capabilities (Wi-Fi and Bluetooth), and extensive peripheral support, making it well-suited for this embedded robotics application.
---

## Project-Specific Resource Requirements

Based on the electrical block diagram, the following hardware resources are required:

- **1x UART** – Daisy chain communication
- **1x SPI peripheral** – Stepper motor driver control
- **2x PWM outputs** – Shoulder & elbow
- **1x Digital input (GPIO)** – Homing switch
- **USB programming interface**
- **Additional GPIO** – Fault input and debugging LEDs

The ESP32-S3 supports all required peripherals simultaneously with no resource conflicts.

---

### Key Features

- 3.3V logic operation  
- Multiple UART, SPI, and I2C peripherals  
- LEDC hardware PWM (ideal for servo control)  
- High GPIO count with flexible pin multiplexing  
- Integrated Wi-Fi and Bluetooth  
- Dual-core processor for high performance  
- Compatible with Arduino IDE and ESP-IDF  

---

### Peripheral Compatibility

Stepper Motor Driver (DRV8434):
- Supports STEP/DIR or SPI interface  
- Compatible with 3.3V logic  
- No level shifting required  

Servos:
- Controlled using PWM (LEDC)  
- Powered separately (5V rail)  
- Signal compatible with ESP32  

Homing Switch:
- Connected to GPIO input  
- Uses pull-up resistor configuration  
- 3.3V logic compatible  

---

### Software Configuration

The ESP32 will be programmed using Arduino IDE or ESP-IDF.

- UART configured for daisy chain communication  
- SPI configured for motor driver (if used)  
- PWM (LEDC) used for servo control  
- GPIO configured for switches and status signals  

---

### Final Selection

Microcontroller: ESP32-S3-WROOM-1

---

### Rationale

The ESP32-S3 was selected because it meets all subsystem requirements while providing greater flexibility and performance than traditional microcontrollers. Its integrated wireless features allow for future expansion, and its peripheral set ensures compatibility with all required components. Additionally, its development ecosystem supports rapid prototyping and debugging.