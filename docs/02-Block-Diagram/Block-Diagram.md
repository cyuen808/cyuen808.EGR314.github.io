---
title: Module's Block Diagram
tags:
- tag1
- tag2
---

## Overview
This block diagram shows how the Front Arm Subsystem for the EGR 314 exploration device is electrically organized. The system is centered around a PIC18F47K42 microcontroller operating at 3.3V and communicating with the rover through a bidirectional UART daisy-chain.

Base rotation is achieved using a NEMA 17 stepper motor controlled by a DRV8434SRGER SPI-based stepper motor driver. Three RC servos (shoulder, elbow, wrist) are included as instructor-approved stretch goals and are driven directly using PWM outputs from the microcontroller.

Separate power regulation is provided for logic and servo subsystems. Homing and fault/status signals are included to ensure safe and reliable operation.

## Block Diagram 

![Front Arm Subsystem Block Diagram](block_diagram.png)


### Key Interfaces
- **UART (2 pins, bidirectional):** Daisy-chain communication with upstream and downstream subsystems  
- **SPI (4 pins):** Control of stepper motor driver for base rotation  
- **SPI (3 pins):** Control of PWM servo driver (stretch goal)  
- **GPIO:** Homing switch input and fault/status feedback  


### Power Architecture
- **14V DC input** via barrel jack  
- **3.3V switching regulator** for MCU and logic  
- **5V regulator** for servo power  
- **14V rail** used directly by the stepper motor driver  

> **Note:** RC servos are included as stretch goals and are an instructor-approved exception to the standard EGR 314 actuator constraints.


