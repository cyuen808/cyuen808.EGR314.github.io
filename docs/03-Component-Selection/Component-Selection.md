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

## Power Management

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

---



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

---



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

---

# 5V Regulator Choice  
**Selected Component:** LM22678TJ-5.0/NOPB  

# Rationale 
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

---


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

---



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


# 3.3V Regulator Choice  
**Selected Component:** LM2651MTCX-3.3/NOPB  

# Rationale  
The LM2651MTCX-3.3/NOPB was selected to power the 3.3V logic rail for the microcontroller and sensors. It provides more than enough current for the system while maintaining good efficiency with its synchronous design. The surface-mount package satisfies project constraints and is easier to work with than smaller wafer-level packages.



### DC Barrel Jack 12V Input

    1. PJ-036AH-SMT-TR  

<img src="https://mm.digikey.com/Volume0/opasdata/d220001/medias/images/884/MFG_PJ-036AH-SMT.jpg?hidebanner=true" width="120">

* $1.37/each  
* [Link to product](https://www.digikey.com/en/products/detail/same-sky-formerly-cui-devices/PJ-036AH-SMT-TR/1530971)

| Pros | Cons |
|------|------|
| Surface-mount, right-angle design. | Rated for 24V and 5A (adequate but not oversized). |
| 2.1mm ID / 5.5mm OD (standard barrel size). | Slightly more expensive than other options. |
| 5A current rating supports motor loads. | Larger footprint. |
| Includes internal switch (can disconnect external supply automatically). | Moderate PCB space required. |

---


    2. 54-00164  

<img src="https://mm.digikey.com/Volume0/opasdata/d220001/medias/images/211/MFG_54-00164.jpg?hidebanner=true" width="120">

* $0.86/each  
* [Link to product](https://www.digikey.com/en/products/detail/tensility-international-corp/54-00164/10459298)

| Pros | Cons |
|------|------|
| Lower cost option. | Slightly lower build robustness compared to Same Sky parts. |
| Surface-mount, right-angle. | 5.5A rating is close to system maximum. |
| 2.1mm ID / 5.5mm OD standard size. | Larger footprint. |
| 48V rating provides voltage margin. | No special locking feature. |

---



    3. PJ-006A-SMT-TR  

<img src="https://mm.digikey.com/Volume0/opasdata/d220001/medias/images/6135/MFG_PJ-006A-SMT.jpg?hidebanner=true" width="120">

* $0.95/each  
* [Link to product](https://www.digikey.com/en/products/detail/same-sky-formerly-cui-devices/PJ-006A-SMT-TR/408456)

| Pros | Cons |
|------|------|
| Surface-mount. | 4A current rating (lower than other options). |
| Standard 2.1mm / 5.5mm barrel size. | 18V rating (less headroom if future input voltage increases). |
| Compact footprint. | Lower current capacity for high motor loads. |
| Lower cost. | Fewer safety margins compared to 5A-rated options. |

---


# Barrel Jack Choice
**Selected Component:** PJ-036AH-SMT-TR (2.1mm ID / 5.5mm OD, right-angle, SMT)

# Rationale  
The PJ-036AH-SMT-TR was selected because it is a surface-mount, right-angle barrel jack with a 5A current rating, giving solid headroom for the rover’s power needs. It uses the standard 2.1mm x 5.5mm barrel size, so it matches common 9–12V adapters. This part also provides a reliable mechanical connection while keeping assembly simple and consistent with the project’s surface-mount design approach.



## Switch

### Homing (Limit) Switch Options

    1. D2F-L  

<img src="https://mm.digikey.com/Volume0/opasdata/d220001/medias/images/2423/D2F-L%2C%20D2F-FL%2C%20D2F-01L%2C%20D2F-01FL.jpg?hidebanner=true" width="120">

* $1.41/each  
* [Link to product](https://www.digikey.com/en/products/detail/omron-electronics-inc-emc-div/D2F-L/83251)

| Pros | Cons |
|------|------|
| High 3A current rating (very durable). | Oversized for logic-level homing signal. |
| Industrial-grade Omron quality. | Larger physical size. |
| 125V AC / 30V DC rating. | Higher cost than needed. |

---



    2. D2F-01  

<img src="https://mm.digikey.com/Volume0/opasdata/d220001/medias/images/2449/D2F-F%2C%20D2F%2C%20D2F-01%2C%20D2F-01F.jpg?hidebanner=true" width="120">

* $1.86/each  
* [Link to product](https://www.digikey.com/en/products/detail/omron-electronics-inc-emc-div/D2F-01/83260)

| Pros | Cons |
|------|------|
| 30V DC rating provides safe voltage margin. | Slightly more expensive than budget options. |
| 100mA rating is more than enough for microcontroller input. | Through-hole mounting. |
| Reliable Omron industrial design. | Moderate footprint size. |
| Compact and widely used for limit switches. |  |

---



    3. TS0101F020P  

<img src="https://mm.digikey.com/Volume0/opasdata/d220001/medias/images/591/TS0101F020P.jpg?hidebanner=true" width="120">

* $0.84/each  
* [Link to product](https://www.digikey.com/en/products/detail/e-switch/TS0101F020P/2639088)

| Pros | Cons |
|------|------|
| Lowest cost option. | Only rated for 6V DC. |
| Compact size. | Lower durability rating. |
| 300mA rating sufficient for signal-level use. | Less robust compared to Omron switches. |

---



# Homing Switch Choice  
**Selected Component:** D2F-01  

# Rationale  
The D2F-01 was selected because it provides reliable SPDT operation with a 30V DC rating, giving a comfortable safety margin for a 3.3V or 5V logic signal. Its 100mA rating is more than sufficient for a homing input while avoiding unnecessary oversizing. This option offers a strong balance of reliability, durability, and cost for the subsystem.



## Actuators

### Servos

    1. CN0193 – 20KG High Torque Servo

<img src="https://mm.digikey.com/Volume0/opasdata/d220001/medias/images/5344/MFG_CN0193.jpg?hidebanner=true" width="120">

* $15.50/each  
* [Link to product](https://www.digikey.com/en/products/detail/sunfounder/CN0193/18668609)

| Pros | Cons |
|------|------|
| Very high torque (20kg·cm). | Largest and heaviest option. |
| Handles heavy arm loads. | Higher current draw. |
| Wide operating range (4.8–7.2V). | More expensive than smaller servos. |

---


    2. Adafruit 1142 – High Torque 5V Servo

<img src="https://mm.digikey.com/Volume0/opasdata/d220001/medias/images/2234/1142.jpg?hidebanner=true" width="120">

* $19.95/each  
* [Link to product](https://www.digikey.com/en/products/detail/adafruit-industries-llc/1142/5154658)

| Pros | Cons |
|------|------|
| Decent torque (140 oz-in). | Higher cost. |
| Operates at 5V. | Lower torque than CN0193. |
| Good build quality. | Slightly bulky. |

---



    3. Adafruit 2307 – Metal Gear Micro Servo

<img src="https://mm.digikey.com/Volume0/opasdata/d220001/medias/images/2129/2307.jpg?hidebanner=true" width="120">

* $11.95/each  
* [Link to product](https://www.digikey.com/en/products/detail/adafruit-industries-llc/2307/5154686)

| Pros | Cons |
|------|------|
| Compact and lightweight. | Lower torque output. |
| Lower current draw. | Not suitable for heavy loads. |
| Metal gears improve durability. | Limited lifting capacity. |

---

# Shoulder / Elbow Choice

**Selected Component:** CN0193  

# Rationale
The CN0193 was selected for the shoulder and elbow joints because these joints experience the highest torque loads. The 20kg·cm rating provides sufficient lifting capability for the arm structure and payload. Although it draws more current and is physically larger, the added torque margin improves reliability and reduces the risk of stalling under load.


# Wrist Choice
**Selected Component:** Adafruit 2307  

# Rationale
The Adafruit 2307 was selected for the wrist because this joint requires significantly less torque. Using a smaller servo reduces weight at the end of the arm, lowering inertia and improving responsiveness. It also reduces power consumption while still meeting the functional requirements of the wrist joint.

## Stepper Motors

    1. MOT-I-81619 – NEMA 17 Hybrid Stepper (7V, 1.2A)

<img src="https://mm.digikey.com/Volume0/opasdata/d220001/medias/images/6243/MFG_MOT-I-81619.jpg?hidebanner=true" width="120">

* $22.96/each  
* [Link to product](https://www.digikey.com/en/products/detail/isl-products-international/MOT-I-81619/23628502)

| Pros | Cons |
|------|------|
| Higher current (1.2A) provides stronger torque capability. | Higher current draw increases power requirements. |
| Standard NEMA 17 frame. | Lower voltage (7V) may require tighter driver control. |
| 200 steps/rev (1.8° resolution). | Moderate cost. |

---

    2. MOT-I-81656 – NEMA 17 Hybrid Stepper (12V, 400mA)

<img src="https://mm.digikey.com/Volume0/opasdata/d220001/medias/images/5786/MFG_MOT-I-81656.jpg?hidebanner=true" width="120">

* $37.06/each  
* [Link to product](https://www.digikey.com/en/products/detail/isl-products-international/MOT-I-81656/22168752)

| Pros | Cons |
|------|------|
| Lower current (400mA) reduces power consumption. | More expensive option. |
| 12V rated (compatible with common 12V systems). | Lower torque than 1.2A option. |
| Standard NEMA 17 footprint. | Longer motor body increases size. |

---

    3. NEMA17-13-04SD-AMT112S – Stepper w/ Integrated Encoder

<img src="https://mm.digikey.com/Volume0/opasdata/d220001/medias/images/496/MFG_NEMA17.jpg?hidebanner=true" width="120">

* $113.45/each  
* [Link to product](https://www.digikey.com/en/products/detail/same-sky-formerly-cui-devices/NEMA17-13-04SD-AMT112S/9477645)

| Pros | Cons |
|------|------|
| Integrated encoder enables closed-loop control. | Very high cost. |
| Higher voltage range (24–48V). | More complex control requirements. |
| Improved positioning accuracy. | Overkill for basic stepper control needs. |

---

# Stepper Motor Selection

**Selected Component:** MOT-I-81619  

# Rationale
The MOT-I-81619 was selected because it provides sufficient torque with a 1.2A current rating while maintaining a standard NEMA 17 footprint. It offers strong performance without the added complexity and cost of an integrated encoder. Compared to the 400mA option, this motor provides better torque margin, which improves reliability under load. The encoder-equipped model was not selected due to cost and unnecessary complexity for this application.


## Stepper Motor Driver

    1. TMC2209-LA

<img src="https://mm.digikey.com/Volume0/opasdata/d220001/medias/images/204/1460%7E28QFN-%2C90-5x5%7EL%7E28.jpg?hidebanner=true" width="120">

* $5.20 each  
* [Link to product](https://www.digikey.com/en/products/detail/analog-devices-inc-maxim-integrated/TMC2209-LA/10249904)

| Pros | Cons |
|------|------|
| Up to 2A output current | QFN package (harder to hand solder) |
| UART configuration capability | 28-pin layout increases PCB complexity |
| Very smooth microstepping (1/256) | Longer lead time |
| Quiet operation (great for robotics) | Requires careful thermal layout |

---

## 2. DRV8889PWPRQ1

<img src="https://mm.digikey.com/Volume0/opasdata/d220001/medias/images/6295/296%7E4224477%7EPWP%7E24.jpg?hidebanner=true" width="120">

* $5.02 each  
* [Link to product](https://www.digikey.com/en/products/detail/texas-instruments/DRV8889QPWPRQ1/11615769)

| Pros | Cons |
|------|------|
| 1.5A output current | Lower current than other options |
| Automotive qualified (AEC-Q100) | Larger footprint |
| SPI interface option | Requires configuration setup |
| 1/256 microstepping | Moderate soldering difficulty |

---

## 3. DRV8434SRGER

<img src="https://mm.digikey.com/Volume0/opasdata/d220001/medias/images/4212/296%7E4204104%7ERGE%7E24.jpg?hidebanner=true" width="120">

* $3.96 each  
* [Link to product](https://www.digikey.com/en/products/detail/texas-instruments/DRV8434SRGER/13627140)

| Pros | Cons |
|------|------|
| Up to 2.5A output current | QFN package (advanced soldering) |
| Wide supply range (4.5V–48V) | Requires careful PCB thermal layout |
| 1/256 microstepping | No advanced stall detection |
| Lower cost | Slightly more design complexity |

---

# Stepper Driver Choice

**Selected Component:** DRV8434SRGER  

# Rationale

The DRV8434SRGER was selected because it provides the highest current capability (2.5A), giving additional torque margin for the NEMA 17 stepper motor. It supports a 12V system comfortably and offers strong microstepping performance at a lower cost. This driver provides the best balance of performance, scalability, and cost for the front arm subsystem.
