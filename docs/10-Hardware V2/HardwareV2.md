---
title: Hardware V2
tags:
- tag1
- tag2
---


# Hardware V2.0

## Overview

This page outlines the proposed improvements for a second revision of the Front Arm Subsystem PCB. The current Rev 1.0 design is functional and meets the Module Requirements, but bring-up, integration testing, and team-level debugging surfaced several areas where the hardware could be more robust, easier to debug, and better aligned with safer operating margins. The improvements below reference specific blocks of the schematic and PCB documented on the Schematic and PCB pages.

## 1. Increase Input-Voltage Headroom on the 3.3 V Rail

The LM2651 3.3 V regulator (U2 on the schematic) has a maximum input voltage rating of 14 V. The selected GlobTek battery pack reaches **12.6 V at full charge**, leaving only about 1.4 V of headroom before the absolute maximum rating, which is not enough to safely tolerate switching transients on the 12 V bus or the small inductive spikes seen when the stepper motor changes direction. Version 2.0 should replace the LM2651 with a wider-input synchronous buck such as the 28 V max input or the 65 V max input. This change would also let the 3.3 V rail be powered directly from the 12 V battery instead of cascading through the 5 V LM22678 stage as the current Power Budget reflects, which improves overall conversion efficiency.

## 2. Replace the Micro-USB Connector with USB-C

The current design uses a Micro-USB type-B connector (J4) for programming and serial debugging. Micro-USB is mechanically fragile, not reversible, and is being phased out across the industry. A USB-C receptacle with two 5.1 kΩ CC pull-down resistors would provide a more durable connection, reversible insertion, and alignment with the connector standard used on most modern development hosts. This is a low-cost change with no impact on the firmware.

## 3. Add Per-Rail Power-Good Indicator LEDs

The current PCB has a single status LED (D3). When a regulator browns out or fails, there is no fast visual way to identify which rail is the problem, which slowed bench debugging more than once during integration. Version 2.0 should include a small indicator LED on each rail — 12 V, 5 V, and 3.3 V — tied to its rail through a 1 kΩ current-limiting resistor. This adds roughly $0.30 to the BOM and significantly shortens the diagnostic loop when something stops working at the system level.

## 4. Add Inline Current Sensing on the Motor Rail

The Front Arm API defines an "Overcurrent" error code (`AE:I:2`) and a "Stall" error code (`AE:I:1`), but the present hardware can only detect faults flagged by the DRV8434S nFAULT pin. There is no way for firmware to read the actual motor current draw or quantify how loaded the arm is at any moment. Adding a 10 mΩ shunt in series with the DRV8434S VM input and a current-sense amplifier feeding an ESP32 ADC pin would let the firmware report live current to the HMI and trigger graceful shutdown well before the driver itself faults. This also enables a software-side stall detector by watching for current spikes when commanded motion does not produce a corresponding position change at the homing switch.

## 5. Add ESD Protection on the UART Daisy-Chain Lines

The 2x4 ribbon connectors (J2 and J3) carry the team UART RX and TX directly into ESP32 GPIO pins with no protection. Cables get plugged and unplugged repeatedly during integration, and a static discharge from someone handling the cable can permanently damage the MCU. A small TVS diode array placed close to each connector would clamp ESD events to safe levels without affecting signal integrity at UART speeds. This is one of the cheapest insurance changes available and would protect the most expensive part on the board.

## 6. Improve Servo Power Decoupling and Inrush Handling

The 5 V rail (LM22678 output, U3) supplies the CN0193 high-torque servos through J6, J7, and J8. Each servo has a stall current of 2.7 A, and simultaneous startup or rapid direction changes can pull the rail down briefly. The current PCB has only a 100 µF bulk capacitor (C13) on the servo rail. Version 2.0 should add a 470 µF low-ESR electrolytic close to the servo connectors and ideally a small soft-start MOSFET on the 5 V output to smooth the initial inrush when the servos first energize. This would eliminate the brief 3.3 V dip observed during integration when all servos commanded large position changes at once.

## 7. Switch to a Stepper Driver with Built-in Stall Detection

The DRV8434S works well for STEP/DIR control but does not expose the back-EMF-based stall detection found on its larger sibling DRV8434 or the StallGuard feature in the TMC2209. Because the Front Arm protocol already defines a stall error code, a V2 board should consider the TMC2209 (which was a finalist in the original component selection) so the driver can flag a stall over UART without needing an external current sensor. The TMC2209 also runs significantly quieter during slow microstepped motion, which was a noticeable side effect of the DRV8434S configuration on the bench.

## 8. Improve Thermal Management on the DRV8434S

The DRV8434S is in a 24-pin QFN package with a center thermal pad that needs to be soldered down to the inner copper pours through thermal vias. The current PCB places the driver in a relatively dense corner with limited copper around it. Version 2.0 should add at least nine 0.3 mm thermal vias under the pad, increase the GND copper pour around U4, and add a tented exposed-copper area on the bottom layer to act as a heat-spreader. At 1.2 A continuous through the NEMA 17 motor this is preventive rather than urgent, but it gives the design margin to accept a higher-current motor in a future iteration.

## 9. Label Test Points and Add Diagnostic Headers

The PCB exposes 20 test points (TP1–TP20), but the silkscreen does not clearly indicate what each one measures. Reading them required cross-referencing the schematic on a separate screen during bring-up. Version 2.0 should label each test point with the net name on the silkscreen ("3V3", "VREF", "STEP", "MOSI", and so on) and add a 0.1″ pin-header next to the SPI lines so a logic analyzer can be clipped on quickly during driver bring-up.

## Summary

None of the changes above require a fundamental redesign — most are small additions that would substantially improve debuggability, reliability, and safe operating margin. The two highest-impact upgrades are the wider-input 3.3 V regulator (item 1) and the inline motor current sensing (item 4), since both directly close gaps between what the Front Arm API claims to detect and what the hardware can actually measure. Together, these changes would move the Front Arm Subsystem from a working prototype to a board that could plausibly be deployed and serviced in the field.