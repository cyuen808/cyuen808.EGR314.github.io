---
title: Module's Requirements
---

## Module Requirements Overview

This section outlines the key functional and design requirements for the Front Arm Subsystem of the CropScout exploration device. The table below describes the minimum and target performance needed for the front arm to move in a controlled manner, interact safely with its environment, and detect and respond to unsafe conditions to avoid damaging the rover. These requirements help guide decisions in component selection, electrical and firmware design, and overall system integration, while ensuring the module communicates reliably over the UART daisy chain and can be operated remotely through the team’s wireless control system.


## Front Arm Subsystem — Module Requirements Table

| **Requirement Description** | **Measure of<br> Threshold** | **Target<br>Measure** |**Stretch<br>Requirement<br>(Y-N)**|
|-------------------------|--------------------------------|----------------|---------------|
| Surface-mounted 3.3 V switching regulator powers MCU and logic | ≥ 3.2 V output under load | Stable 3.3 V regulated output | No |
| Microcontroller for motion control and communication (PIC18F47K42, programmed via MPLAB Snap) | MCU boots and executes basic control loop | MCC-based firmware with structured messaging and safety logic | No |
| UART interface to system daisy chain network | One-way UART messaging | Two-way command and status messaging | No |
| Compatibility with wireless control via UART-relayed commands | Executes commands originating from wireless node | Supports remote command and telemetry with low latency | No |
| Stepper motor provides base yaw rotation | ≥ 180° rotational sweep | 340° sweep (software-limited) | No |
| Stepper motors provide arm articulation | 2 controlled joints | 3 controlled joints | Yes |
| Stepper motor drivers support selected motors | Basic motion without stalling at low speed | Smooth motion under expected mechanical load | No |
| Serial-controlled stepper driver (SPI/I²C/UART) for actuator compliance | Driver configurable via serial interface | Fault, current, or status readback available | No |
| Homing or reference sensors for repeatable positioning | At least one homing switch | One homing sensor per joint | Yes |
| Overload or fault response behavior | Motion stops on fault detection | Stop, retract to home position, and send error report | No |
