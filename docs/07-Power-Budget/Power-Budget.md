---
title: Power Budget
---

# Power Budget

## Overview

This power budget verifies that the selected regulators and external supply can safely power all major components in the subsystem. Maximum current values were taken from component datasheets and a 25% safety margin was added per EGR 314 requirements.

---

# Section A – Major Power-Consuming Components

| Component | Voltage Rail | Max Current (A) |
|------------|--------------|----------------|
| PIC18F47K42 | 3.3V | 0.05 A |
| DRV8434SRGER (logic) | 3.3V | 0.02 A |
| Stepper Motor (MOT-I-81619) | 9V Rail | 1.20 A |
| CN0193 Servo (Shoulder) | 5V | 1.50 A (stall) |
| CN0193 Servo (Elbow) | 5V | 1.50 A (stall) |
| Adafruit 2307 Servo (Wrist) | 5V | 0.80 A (stall) |

*Note: Servo currents represent stall conditions (worst case).*

---

# Section B – Power Rail Totals (With 25% Safety Margin)

## 3.3V Rail

Total current:
0.05 + 0.02 = **0.07 A**

With 25% margin:
0.07 × 1.25 = **0.088 A**

Selected Regulator: LM2651MTCX-3.3 (1.5A max)

✔ Regulator capacity exceeds required current.

---

## 5V Rail

Total servo stall current:
1.50 + 1.50 + 0.80 = **3.80 A**

With 25% margin:
3.80 × 1.25 = **4.75 A**

Selected Regulator: LM22678TJ-5.0 (5A max)

✔ Regulator capacity slightly exceeds required worst-case load.
⚠ Large output capacitors recommended due to servo transients.

---

## 9V Rail (Motor Supply)

Stepper Motor max current:
1.20 A

With 25% margin:
1.20 × 1.25 = **1.50 A**

External Supply Required:
Minimum 9V @ 2A recommended

---

# Section C – Regulator Selection

| Rail | Regulator | Max Output | Required | Status |
|-------|------------|------------|----------|--------|
| 3.3V | LM2651MTCX-3.3 | 1.5A | 0.088A | ✔ Safe |
| 5V | LM22678TJ-5.0 | 5A | 4.75A | ✔ Safe |
| 9V | External Adapter | ≥2A | 1.50A | ✔ Safe |

---

# Section D – External Power Source

Selected External Supply:
9V DC Wall Adapter (minimum 2A rating)

Total Worst-Case System Draw:
Approximately 5–6A combined across rails (not simultaneous peak on all rails due to regulator conversion).

The selected adapter provides sufficient headroom when accounting for regulator efficiency and transient loads.

---

# Conclusion

All power rails meet the 25% safety margin requirement. The selected 5V and 3.3V switching regulators provide sufficient current capacity for worst-case operation. The 9V external supply recommendation ensures adequate power delivery for motor and servo loads.

(Final spreadsheet version to be attached.)


### Power Budget 
![Power Budget](ADD Image)

## Downloads
The Power Budget template can be downloaded below:  

- [Power Budget (.xlsx)](Excel File)  
- [Power Budget (.pdf)](PDF file) 
