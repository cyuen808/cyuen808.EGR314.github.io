---
title: Module Bill of Materials
tags:
- tag1
- tag2
---

## Overview

The Front-Arm Subsystem controls a NEMA 17 stepper motor and three RC servos using an ESP32-S3-WROOM microcontroller. The system operates from a 14.4V Li-Ion battery or 14V Barrel Jack and includes onboard 5V and 3.3V switching regulation. The stepper motor driver communicates via SPI, and the subsystem connects to the team UART daisy-chain bus.

Quantities include extra components per assignment requirement for prototyping and redundancy.

## Bill of Materials

| **Part Name / Description** | **Qty** | **Unit Cost ($)** | **Total Cost ($)** | **Manufacturer** | **Manufacturer #** | **Vendor Link** |**Datasheet Link** | **Schematic Ref** |
|:--------------------|:----|:---------------|:-----|:--------|:-----|:-----|:----|:-----|
3.3V Buck Regulator, 1.5A     | 3 | 4.430  | 13.29 | Texas Instruments | LM2651MTCX-3-3-NOPB | [DigiKey](https://www.digikey.com/en/products/detail/texas-instruments/LM2651MTCX-3-3-NOPB/366869) | [datasheet link](chrome-extension://efaidnbmnnnibpcajpcglclefindmkaj/https://www.ti.com/lit/ds/symlink/lm2651.pdf?ts=1772500009965)  | U2               |
5V Buck Regulator, 5A         | 3 | 7.610  | 22.83 | Texas Instruments | LM22678T-5.0-NOPB   | [DigiKey](https://www.digikey.com/en/products/detail/texas-instruments/LM22678TJ-5-0-NOPB/1951972) | [datasheet link](https://www.ti.com/general/docs/suppproductinfo.tsp?distId=10&gotoUrl=https%3A%2F%2Fwww.ti.com%2Flit%2Fgpn%2Flm22678)   | U3               | 
Stepper Motor Driver (SPI)    | 3 | 3.960  | 11.88 | Texas Instruments | DRV8434SRGER        | [DigiKey](https://www.digikey.com/en/products/detail/texas-instruments/DRV8434SRGER/13627140) | [datasheet link](chrome-extension://efaidnbmnnnibpcajpcglclefindmkaj/https://www.ti.com/lit/ds/symlink/drv8434s.pdf)   | U4               |
D2F-01F (Homing Switch)            | 2 | 1.050  | 2.10  | Omron             | SW502-ND            | [DigiKey](https://www.digikey.com/en/products/detail/omron-electronics-inc-emc-div/D2F-01F/83266) | [datasheet link](chrome-extension://efaidnbmnnnibpcajpcglclefindmkaj/https://mm.digikey.com/Volume0/opasdata/d220001/medias/docus/875/D2F_0318_DS.pdf)    | SW1              |
Barrel Jack (SMT)             | 3 | 1.370  | 4.11  | Same Sky          | PJ-036AH-SMT-TR     | [DigiKey](https://www.digikey.com/en/products/detail/same-sky-formerly-cui-devices/PJ-036AH-SMT-TR/1530971) | [datasheet link](chrome-extension://efaidnbmnnnibpcajpcglclefindmkaj/https://www.sameskydevices.com/product/resource/pj-036ah-smt-tr.pdf)    | J1               |
High Torque Servo             | 4 | 15.500 | 62.00 | SunFounder        | CN0193              | [DigiKey](https://www.digikey.com/en/products/detail/sunfounder/CN0193/18668609) | [datasheet link](chrome-extension://efaidnbmnnnibpcajpcglclefindmkaj/http://wiki.sunfounder.cc/images/9/9a/TD-8120MG_Digital_Servo.pdf)    | J6, J7, J8       |
Schottky Diode 80V 3A         | 4 | 0.600  | 2.40  | onsemi            | SS38FSCT-ND         | [DigiKey](https://www.digikey.com/en/products/detail/onsemi/SS38/1053651) | [datasheet link](chrome-extension://efaidnbmnnnibpcajpcglclefindmkaj/https://www.onsemi.com/pdf/datasheet/ss39-d.pdf)    | D1, D2           |
3A 1206 Fuse                  | 2 | 1.580  | 3.16  | Littelfuse        | 0468003.NR          | [DigiKey](https://www.digikey.com/en/products/detail/littelfuse-inc/0468003-NR/700870) | [datasheet link](chrome-extension://efaidnbmnnnibpcajpcglclefindmkaj/https://www.littelfuse.com/assetdocs/fuse-468-datasheet?assetguid=6b7857dc-f79c-4aae-8bcc-a9ef11ddef09)    | F1               |
14.4V Li-Ion Battery Pack     | 1 | 88.970 | 88.97 | GlobTek | BL5000C21704S2PTFM106IBC2NN-ND | [DigiKey](https://www.digikey.com/en/products/detail/globtek-inc/BL5000C21704S2PFTM106IBC2NN/22531453?s=N4IgTCBcDaIEIBkCsAGNBhMBGA7CgLAMpgAKAYgCogC6AvkA) | [datasheet link](chrome-extension://efaidnbmnnnibpcajpcglclefindmkaj/https://spec.globtek.info/spec/pdf/BL5000C21704S2PFTM106IBC2NN)  | J9 |
NEMA 17 Hybrid Stepper (7V, 1.2A) | 2  | 22.960  | 45.92 | ISL Products | MOT-I-81619 | [DigiKey](https://www.digikey.com/en/products/detail/isl-products-international/MOT-I-81619/23628502) | [datasheet link](chrome-extension://efaidnbmnnnibpcajpcglclefindmkaj/https://mm.digikey.com/Volume0/opasdata/d220001/medias/docus/6257/MOT-I-81619.pdf)  | J5 |
6.8µH Inductor (6.4A)         | 3 | 1.130  | 3.39 | Codaca | VSHB0754T-6R8MCCT-ND | [DigiKey](https://www.digikey.com/en/products/detail/codaca/VSHB0754T-6R8MC/16731499) | [datasheet link](chrome-extension://efaidnbmnnnibpcajpcglclefindmkaj/https://www.codaca.com/Private/pdf/VSHB0754T.pdf)  | L2 |
68µH Inductor (2A)            | 3 | 1.130  | 3.39 | Codaca | VSHB0754T-680MCCT-ND | [DigiKey](https://www.digikey.com/en/products/detail/codaca/VSHB0754T-680MC/16731515) | [datasheet link](chrome-extension://efaidnbmnnnibpcajpcglclefindmkaj/https://www.codaca.com/Private/pdf/VSHB0754T.pdf)  | L1 |

SPDT Mini Toggle Switch 3-Pin 2 Position           | 1 | 7.99  | 7.99 | Taiss  | B0799HC3VY | [Amazon](https://www.amazon.com/MTS-102-125VAC-Position-Miniature-Toggle/dp/B0799HC3VY/ref=sr_1_3?crid=1N6TI53Q9JPVU&dib=eyJ2IjoiMSJ9.aIvYwZPbygsJl1_JSs8UfgDGq9zJ7tq0wmId8w-J5SP5-AQxHyOXeuP40qNgUP4F3PVK-Ih19fI0P9Sv1viCsTbqEOftvtvQ63TFwbfWjTLORUnBGGPlBvlvlVxcLtEPt94nvMDuUeun-8yhGsmREVrf_r1_WEW72bBsXdaaaPaJmOc-DfosLa8imHHIGyYaJzDzPAdJY12KJAUymEkMZ7A_LXTSSQnR4d-YQlWL9ZM.fKxb6_T1VjGbYp_Rj9Y3PcTZM-VsZJ4pnRNc6fFDESk&dib_tag=se&keywords=SWITCH%2BTOGGLE%2BSPDT%2B0.4VA%2B20V&qid=1772473593&sprefix=switch%2Btoggle%2Bspdt%2B0.4va%2B20v%2Caps%2C158&sr=8-3&th=1) | [datasheet link]()  | SW4 |

0.1µF 0805 Ceramic Capacitors | 11 | --- | --- | Peralta | --- | --- | --- | C3,C5,C6,C8,C11,C12,C15,C16,C17,C18,C20|
22µF Bulk Capacitors | 4 | --- | --- | Peralta | --- | --- | --- | C1,C2,C14,C19|
2.2nF Capacitors | 1 | --- | --- | Peralta | --- | --- | --- | C7,C13|
100µF Capacitors | 2 | --- | --- | Peralta | --- | --- | --- | C9| 
0.22µF Capacitors | 1 | --- | --- | Peralta | --- | --- | --- | C10|
10kΩ Resistors | 5 | --- | --- | Peralta | --- | --- | --- | R3,R4,R6,R7,R9|
15kΩ Resistors | 1 | --- | --- | Peralta | --- | --- | --- | R1|
47kΩ Resistors | 1 | --- | --- | Peralta | --- | --- | --- | R2|
330Ω Resistors | 1 | --- | --- | Peralta | --- | --- | --- | R8|

## Resources

The Bill of Material as a PDF download is available [*here*](PDF_For_BOM_EXAMPLE.pdf).