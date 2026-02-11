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



### 5V Regulator Choice  
**Selected Component:** LM22678TJ-5.0/NOPB  

### Rationale 
The LM22678TJ-5.0/NOPB was chosen because it can supply up to 5A, giving plenty of headroom for motors and other high-current loads. Its wide input range works well with the 9V barrel jack, and the fixed 5V output keeps the design simple. It also meets the surface-mount requirement for the project and is practical to route on the PCB.




### 3.3V Buck Regulator

1. LM2651MTCX-3.3/NOPB  

<img src="https://mm.digikey.com/Volume0/opasdata/d220001/medias/images/4108/296%7E4040064-4%7EPW%7E16.JPG?hidebanner=true" width="120">

* $4.43/each  
* [Link to product](https://www.digikey.com/en/products/detail/texas-instruments/LM2651MTCX-3-3-NOPB/366869E)

| Pros | Cons |
|------|------|
| 3.3V fixed output (ideal for microcontroller rail). | Only 1.5A output current. |
| Synchronous rectifier (better efficiency than older bucks). | 300kHz switching → larger external components than 1MHz designs. |
| Surface-mount (16-TSSOP). | Requires external inductor and capacitors. |
| Input range up to 14V (works with 9V barrel input). | Slightly older architecture. |

2. LM2655MTCX-3.3/NOPB  

<img src="https://mm.digikey.com/Volume0/opasdata/d220001/medias/images/4108/296%7E4040064-4%7EPW%7E16.JPG?hidebanner=true" width="120">

* $5.76/each  
* [Link to product](https://www.digikey.com/en/products/detail/texas-instruments/LM2655MTCX-3-3-NOPB/366873)

| Pros | Cons |
|------|------|
| Higher output current (2.5A). | Not synchronous (lower efficiency than LM2651). |
| 3.3V fixed output. | 300kHz switching frequency. |
| Surface-mount (16-TSSOP). | Requires external inductor and capacitors. |
| Works with 9V input. | Slightly higher cost than 1.5A option. |


3. MAX77503BEWC33+T  

<img src="https://mm.digikey.com/Volume0/opasdata/d220001/medias/images/6256/175%7E21-100250%7EWC%7E12.jpg?hidebanner=true" width="120">

* $2.09/each  
* [Link to product](https://www.digikey.com/en/products/detail/analog-devices-inc-maxim-integrated/MAX77503BEWC33-T/11485809)

| Pros | Cons |
|------|------|
| High switching frequency (1MHz → smaller inductor & caps). | WLP package (very small, harder to solder). |
| Synchronous rectifier (high efficiency). | 1.5A max output current. |
| Compact footprint (excellent for dense PCB layout). | More challenging PCB layout due to small pitch. |
| Lower cost than TI options. | Harder to hand assemble. |


### 3.3V Regulator Choice  
**Selected Component:** LM2651MTCX-3.3/NOPB  

### Rationale  
The LM2651MTCX-3.3/NOPB was selected to power the 3.3V logic rail for the microcontroller and sensors. It provides more than enough current for the system while maintaining good efficiency with its synchronous design. The surface-mount package satisfies project constraints and is easier to work with than smaller wafer-level packages.

