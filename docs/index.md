---
title: Welcome
tags:
- tag1
- tag2
---
<center>
<font size= "4">Caleb Yuen's Datasheet</font><br>
as part of<br>
<font size= "8"> Exploration Device Project</font><br>
<font size= "7"> S.C.O.U.T.S</font><br>
Super Cool Original and Unique Technology Systems<br>
<font size= "5"> Team 202 </font><br>

**Submission: May, 01, 2026**
</center>

## Introduction

Welcome to my individual subsystem datasheet for **CropScout**, a modular agricultural exploration rover developed in EGR 314.
This page documents the design, implementation, and verification of my **Front Arm Actuation Subsystem**. The purpose of this datasheet is to provide a standalone technical reference that clearly explains what this board does, how it operates, and how it integrates into the team’s UART daisy-chain system.
This document is written so that a reader can understand my subsystem without needing to reference the team report.


### Project Summary

* This needs to be updated to reflect <ins>your version</ins> of the team project, so when shared not via the team's report, the reader gets an idea of the direction of the project and how your work will contribute to the overall success.
* Add context that ties into the link to your [EGR 314 Team 202 Report.](https://egr314-s-2026-202.github.io/)

**CropScout** is a modular agricultural exploration device designed to simulate crop monitoring, environmental sensing, and controlled mechanical interaction.

The full system consists of seven independent subsystems:

- Human Machine Interface (HMI) Subsystem  
- Wireless Communication Subsystem  
- Mobility Drive Actuation Subsystem  
- Accelerometer Subsystem  
- Front Arm Actuation Subsystem (This Board)  
- Metal Sensor Subsystem  
- Temperature & Humidity Subsystem  

Each subsystem is implemented as its own PCB and communicates using a standardized UART daisy-chain network over an 8-wire ribbon cable. Every board includes its own regulated power supply and must be verified independently before full system integration.

For a complete system-level overview including Team Organization, Concept Design, Project Requirements and Block Diagram, visit the  
**[EGR 314 Team 202 Report](https://egr314-s-2026-202.github.io/)**
\

### My Contribution

I designed and implemented the **Front Arm Actuation Subsystem**, which is responsible for controlled mechanical motion of CropScout’s manipator assembly.

My responsibilities included:

- Selecting and integrating the ESP32 microcontroller  
- Designing the 3.3V switching regulator and power architecture  
- Implementing bus power and barrel jack isolation jumpers  
- Interfacing with a serial stepper motor driver  
- Designing the full schematic and PCB layout  
- Developing the UART messaging API  
- Implementing command parsing and motor control logic  
- Verifying safe communication and hardware operation prior to integration  

This subsystem enables reliable, addressable actuation within CropScout while maintaining safe operation on the shared UART network.
