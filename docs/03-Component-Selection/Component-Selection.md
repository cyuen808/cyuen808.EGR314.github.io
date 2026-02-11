---
title: Module's Selected Major Components
---

## Module's Selected Major Components

The following sections are the selected major components necessary for  .....

>**For each of the following sections, use <ins>one of the two styles</ins> given near the end. *REMOVE THIS NOTE***

### Power Management

(**remove this note/placeholder**: this is where your 3.3 volt switching regulator, any other needed power regulator, and power source {if applicable} **THAT WERE SELECTED**)

For more details, review the ["Appendix - Component Selection Process - Power Mangement"](https://embedded-systems-design.github.io/EGR314DataSheetTemplate/Appendix/01-Componet-Selection/Component-Selection-Process/#power-management) selection.

### Sensor

(**remove this note/placeholder**: if applicable, this is where your  **SELECTED** sensor is shown. Otherwise, remove this section.)

For more details, review the ["Appendix - Component Selection Process - Sensor"](https://embedded-systems-design.github.io/EGR314DataSheetTemplate/Appendix/01-Componet-Selection/Component-Selection-Process/#sensor) selection.


(**remove this note/placeholder**: if applicable, this is where your **Selected** the actuator items go, which includes both the driver and motor. Otherwise, remove this section.)

For more details, review the ["Appendix - Component Selection Process - Actuator"](https://embedded-systems-design.github.io/EGR314DataSheetTemplate/Appendix/01-Componet-Selection/Component-Selection-Process/#actuator) selection.

-----------
> Remove the following before submitting! Use them to present the selected components

## Component Selection

### 5V Buck Regulator


| Component | Pros | Cons |
|-----------|------|------|
| <img src="https://mm.digikey.com/Volume0/opasdata/d220001/medias/images/6347/296%7ETJ7A%7ENDR%7E7.jpg?hidebanner=true" width="120"> <br> **5V Buck Regulator - LM22678TJ-5.0/NOPB** <br> *$7.61/each* <br> [Link to product](https://www.digikey.com/en/products/detail/texas-instruments/LM22678TJ-5-0-NOPB/1951972) | • 5A output capability  <br> • Wide input range (4.5V–42V)  <br> • Fixed 5V output simplifies design  <br> • Surface mount (meets project requirement) | • Requires external inductor, diode, and capacitors  <br> • Larger TO-263 footprint  <br> • Not synchronous (lower efficiency than modern regulators)  <br> • Requires careful PCB layout for switching noise |

| Component | Pros | Cons |
|-----------|------|------|
| <img src="https://mm.digikey.com/Volume0/opasdata/d220001/medias/images/6347/296%7ETJ7A%7ENDR%7E7.jpg?hidebanner=true" width="120"> <br> **5V Buck Regulator - LM22679TJE-5.0/NOPB** <br> *$8.62/each* <br> [Link to product](https://www.digikey.com/en/products/detail/texas-instruments/LM22679TJE-5-0-NOPB/1950780) | • 5A output capability  <br> • Wide input range (4.5V–42V)  <br> • Fixed 5V output  <br> • Surface mount (meets EGR314 requirement)  <br> • SIMPLE SWITCHER series (proven design) | • Requires external inductor, diode, and capacitors  <br> • Large TO-263 footprint  <br> • Not synchronous (lower efficiency vs modern buck ICs)  <br> • Careful PCB layout required for switching noise |

| Component | Pros | Cons |
|-----------|------|------|
| <img src="https://mm.digikey.com/Volume0/opasdata/d220001/medias/images/6347/296%7ETA07B%7ENDZ%7E7.jpg?hidebanner=true" width="120"> <br> **5V Buck Regulator - LM2678T-5.0/NOPB** <br> *$6.99/each* <br> [Link to product](https://www.digikey.com/en/products/detail/texas-instruments/LM2678T-5-0-NOPB/363828) | • 5A output capability  <br> • Proven SIMPLE SWITCHER design  <br> • Lower cost than surface-mount versions  <br> • Easy prototyping (TO-220 package) | • **Through-hole (does NOT meet surface-mount requirement)**  <br> • Larger footprint  <br> • Requires external inductor and diode  <br> • Lower switching frequency (260kHz → larger external components)  <br> • Not synchronous |




1. LM22678TJ-5.0/NOPB  

<img src="https://mm.digikey.com/Volume0/opasdata/d220001/medias/images/6347/296%7ETJ7A%7ENDR%7E7.jpg?hidebanner=true" width="120">

* $7.61/each  
* [Link to product](https://www.digikey.com/en/products/detail/texas-instruments/LM22678TJ-5-0-NOPB/1951972)

| Pros | Cons |
|------|------|
| 5A output capability supports high-current subsystems. | Requires external inductor, diode, and capacitors. |
| Wide input range (4.5V–42V) works well with 9V barrel jack input. | Larger TO-263 footprint increases PCB space usage. |
| Fixed 5V output simplifies power design. | Not synchronous, so efficiency is lower than modern buck regulators. |
| Surface-mount package meets EGR314 requirement. | Requires careful PCB layout to minimize switching noise. |



2. LM22679TJE-5.0/NOPB  

<img src="https://mm.digikey.com/Volume0/opasdata/d220001/medias/images/6347/296%7ETJ7A%7ENDR%7E7.jpg?hidebanner=true" width="120">

* $8.62/each  
* [Link to product](https://www.digikey.com/en/products/detail/texas-instruments/LM22679TJE-5-0-NOPB/1950780)

| Pros | Cons |
|------|------|
| 5A output capability. | Requires external inductor, diode, and capacitors. |
| Wide input range (4.5V–42V). | Large TO-263 footprint. |
| Surface-mount (meets EGR314 requirement). | Not synchronous (lower efficiency than modern buck ICs). |
| SIMPLE SWITCHER series (proven, reliable design). | Careful PCB layout required for switching noise. |


3. LM2678T-5.0/NOPB  

<img src="https://mm.digikey.com/Volume0/opasdata/d220001/medias/images/6347/296%7ETA07B%7ENDZ%7E7.jpg?hidebanner=true" width="120"> 

* $6.99/each  
* [Link to product](https://www.digikey.com/en/products/detail/texas-instruments/LM2678T-5-0-NOPB/363828)

| Pros | Cons |
|------|------|
| 5A output capability. | **Through-hole package (does NOT meet surface-mount requirement).** |
| Proven SIMPLE SWITCHER design. | Larger footprint (TO-220). |
| Lower cost than surface-mount versions. | Requires external inductor and diode. |
| Easy prototyping due to TO-220 package. | Lower switching frequency (260kHz → larger external components). |
