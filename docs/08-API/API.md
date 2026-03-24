---
title: API
---

## Overview
This page defines the UART message interface for Caleb’s Front Arm subsystem. The Front Arm subsystem receives commands from the HMI or wireless subsystem, executes motion commands for the arm base, and returns acknowledgements and status messages to the team network.

This API only defines the message data field inside the class packet. Prefix, suffix, sender ID, and receiver ID are handled by the class UART packet format.

## Subsystem ID
- Front Arm Board ID: 5   <!-- replace with your actual ID -->

## Messages Received

### Message: SET_POSITION
Used to command the front arm to move to a target position.

| Byte | Variable Name | Data Type | Bytes | Min | Max | Description |
|------|---------------|-----------|-------|-----|-----|-------------|
| 1 | message_type | uint8_t | 1 | 0 | 255 | Message ID for SET_POSITION |
| 2 | angle_deg | int16_t | 2 | -180 | 180 | Desired arm angle in degrees |

Example:
- angle_deg = 90

### Message: JOG_ENABLE
Used to enable or stop jog motion.

| Byte | Variable Name | Data Type | Bytes | Min | Max | Description |
|------|---------------|-----------|-------|-----|-----|-------------|
| 1 | message_type | uint8_t | 1 | 0 | 255 | Message ID for JOG_ENABLE |
| 2 | enable | uint8_t | 1 | 0 | 1 | 1 = move, 0 = stop |

### Message: COLLISION_STATUS
Sent from the accelerometer subsystem to allow or stop motion.

| Byte | Variable Name | Data Type | Bytes | Min | Max | Description |
|------|---------------|-----------|-------|-----|-----|-------------|
| 1 | message_type | uint8_t | 1 | 0 | 255 | Message ID for COLLISION_STATUS |
| 2 | safe_flag | uint8_t | 1 | 0 | 1 | 1 = safe to continue, 0 = halt |

## Messages Sent

### Message: ACK_POSITION
Sent after the front arm reaches the requested position.

| Byte | Variable Name | Data Type | Bytes | Min | Max | Description |
|------|---------------|-----------|-------|-----|-----|-------------|
| 1 | message_type | uint8_t | 1 | 0 | 255 | Message ID for ACK_POSITION |
| 2 | actual_angle_deg | int16_t | 2 | -180 | 180 | Final measured or commanded position |

### Message: ARM_STATUS
Reports current arm state.

| Byte | Variable Name | Data Type | Bytes | Min | Max | Description |
|------|---------------|-----------|-------|-----|-----|-------------|
| 1 | message_type | uint8_t | 1 | 0 | 255 | Message ID for ARM_STATUS |
| 2 | status_code | uint8_t | 1 | 0 | 3 | 0 = idle, 1 = moving, 2 = done, 3 = halted |

### Message: ARM_ERROR
Reports arm faults.

| Byte | Variable Name | Data Type | Bytes | Min | Max | Description |
|------|---------------|-----------|-------|-----|-----|-------------|
| 1 | message_type | uint8_t | 1 | 0 | 255 | Message ID for ARM_ERROR |
| 2 | error_code | uint8_t | 1 | 0 | 10 | 0 = none, 1 = stall, 2 = overcurrent, 3 = collision halt |

## Receiver Behavior
The Front Arm subsystem:
- receives all UART packets from the daisy chain
- ignores bytes outside a valid frame
- ignores malformed packets
- ignores packets larger than the buffer
- forwards packets not addressed to this board
- processes packets addressed to this board
- discards packets sent by itself if they loop back
- sends an acknowledgement for each valid supported command

## Sender Behavior
The Front Arm subsystem:
- sends ACK_POSITION after motion completes
- sends ARM_STATUS during or after motion
- sends ARM_ERROR if a fault occurs
- limits send rate using a timer-based non-blocking interval
- prioritizes forwarding incoming messages before sending its own

## Software Link
- [ZIP of source code](./front_arm_api_code.zip)
- [Main repository](./)