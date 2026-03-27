---
title: API
---

## Overview
This page defines the UART message interface for Caleb’s Front Arm subsystem. The Front Arm subsystem receives commands from the HMI, executes motion commands for the arm base, and returns acknowledgements, status messages, and error messages to the team network.

This API defines the message data portion used inside the class UART packet. Prefix, suffix, sender ID, and receiver ID are handled by the class communication protocol.

## Subsystem ID
- Front Arm Board ID: 'a'

## Subsystem Addressing

All subsystems communicate using ASCII character IDs.

### Messages include:
- sender ID
- receiver ID

If a message is not addressed to this subsystem ('a'), it is forwarded unchanged.  
If a message is addressed to this subsystem, it is processed.

## Known Subsystem IDs

| Subsystem | ID |
|----------|----|
| HMI | 'h' |
| Comm | 'c' |
| Wheel | 'w' |
| Pressure | 'p' |
| Arm | 'a' |
| Metal | 'm' |
| Temp | 't' |
| Broadcast | 'X' |

## Message Framing

### All messages are transmitted using the class UART frame:
- `AZ [Sender] [Receiver] [Message Data] YB`

### Examples:
- `AZhaAD:S:U;YB`
- `AZahAA:I:90;YB`
- `AZahAS:S:Done;YB`
- `AZahAE:I:3;YB`

### Where:
- `AZ` = prefix
- `Sender` = subsystem sending the message
- `Receiver` = subsystem receiving the message
- `Message Data` = token-based payload defined below
- `YB` = suffix

## Messages Received

## Message: Arm Drive Mode
Sent from HMI ('h') to Front Arm ('a') to command arm movement.

### Format:
- `AD:S:U`
- `AD:S:D`
- `AD:S:R`
- `AD:S:L`

| Byte | Variable Name | Data Type | Bytes | Min | Max | Description |
|------|---------------|-----------|-------|-----|-----|-------------|
| 1-2 | token | char[2] | 2 | AD | AD | Message token |
| 3 | separator_1 | char | 1 | : | : | Separator |
| 4 | type | char | 1 | S | S | String type |
| 5 | separator_2 | char | 1 | : | : | Separator |
| 6 | command | char | 1 | D | U | Arm direction command: U, D, R, or L |

Total Message Data Length: 6 bytes

### Example:
- `AD:S:U`

### Interpretation:
- `U` = Up
- `D` = Down
- `R` = Right
- `L` = Left

## Messages Sent

### Message: Arm Position Acknowledge
Sent from Front Arm ('a') to HMI ('h') after movement is received or completed.

### Format:
- `AA:I:90`

| Byte | Variable Name | Data Type | Bytes | Min | Max | Description |
|------|---------------|-----------|-------|-----|-----|-------------|
| 1-2 | token | char[2] | 2 | AA | AA | Message token |
| 3 | separator_1 | char | 1 | : | : | Separator |
| 4 | type | char | 1 | I | I | Integer type |
| 5 | separator_2 | char | 1 | : | : | Separator |
| 6-8 | position_value | ASCII integer | up to 3 | -180 | 180 | Arm position acknowledgement value |

Total Message Data Length: 8 bytes max

### Examples:
- `AA:I:90`
- `AA:I:-45`
- `AA:I:180`

## Message: Arm Status
Sent from Front Arm ('a') to HMI ('h') to report current arm state.

### Format:
- `AS:S:Idle`
- `AS:S:Moving`
- `AS:S:Done`
- `AS:S:Halted`

| Byte | Variable Name | Data Type | Bytes | Min | Max | Description |
|------|---------------|-----------|-------|-----|-----|-------------|
| 1-2 | token | char[2] | 2 | AS | AS | Message token |
| 3 | separator_1 | char | 1 | : | : | Separator |
| 4 | type | char | 1 | S | S | String type |
| 5 | separator_2 | char | 1 | : | : | Separator |
| 6-12 | status_text | string | up to 7 | Idle | Halted | Current arm state |

Total Message Data Length: 12 bytes max

### Examples:
- `AS:S:Idle`
- `AS:S:Moving`
- `AS:S:Done`
- `AS:S:Halted`

## Message: Arm Error
Sent from Front Arm ('a') to HMI ('h') when a fault occurs.

###Format:
- `AE:I:0`
- `AE:I:1`
- `AE:I:2`
- `AE:I:3`

| Byte | Variable Name | Data Type | Bytes | Min | Max | Description |
|------|---------------|-----------|-------|-----|-----|-------------|
| 1-2 | token | char[2] | 2 | AE | AE | Message token |
| 3 | separator_1 | char | 1 | : | : | Separator |
| 4 | type | char | 1 | I | I | Integer type |
| 5 | separator_2 | char | 1 | : | : | Separator |
| 6 | error_code | ASCII integer | 1 | 0 | 3 | Error code |

Total Message Data Length: 6 bytes

### Error Codes:
- `0` = No error
- `1` = Stall
- `2` = Overcurrent
- `3` = Collision halt

### Examples:
- `AE:I:0`
- `AE:I:1`
- `AE:I:2`
- `AE:I:3`

## Receiver Behavior
### The Front Arm subsystem:
- receives all UART packets from the daisy chain
- checks for valid prefix and suffix framing
- ignores malformed packets
- ignores unsupported messages
- forwards packets not addressed to this board
- processes packets addressed to this board
- discards packets sent by itself if they loop back
- sends an acknowledgement for each valid supported command

## Sender Behavior
### The Front Arm subsystem:
- sends `AA:` after processing or completing a movement command
- sends `AS:` during or after movement to report current state
- sends `AE:` if a fault occurs
- limits send rate using timer-based non-blocking logic
- prioritizes forwarding incoming packets before sending its own messages

## Supported Message Flow
### Example command flow:
1. HMI sends `AZhaAD:S:R;YB`
2. Front Arm receives and processes the command
3. Front Arm responds with position acknowledgement such as `AZahAA:I:90;YB`
4. Front Arm reports status such as `AZahAS:S:Done;YB`
5. If a fault occurs, Front Arm sends an error such as `AZahAE:I:3;YB`

### Software Link (Will update later)
- [ZIP of source code](./front_arm_api_code.zip)
- [Main repository](./)
