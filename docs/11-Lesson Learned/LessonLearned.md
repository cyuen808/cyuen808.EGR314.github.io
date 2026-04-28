---
title: Lesson Learned
tags:
- tag1
- tag2
---


# Reflection: Lessons Learned

The following ten lessons capture the most important things I took away from designing, building, and integrating the Front Arm Subsystem this semester. They are drawn from feedback I received during the design review, issues that surfaced during bring-up, and content I discussed in status reports.

1. **Read the absolute-maximum-ratings table before committing to a part.** I selected the LM2651 3.3 V regulator early in the project and only later realized that its 14 V maximum input is uncomfortably close to the 12.6 V peak of the 3S Li-ion battery pack. The part still worked, but the lesson is that "typical operating conditions" and "absolute maximum ratings" are two different tables in a datasheet, and the second one decides whether your design has any safety margin at all.

2. **Start the PCB layout earlier than feels necessary.** Schematic capture finished quickly, but the routing of the DRV8434S thermal pad, the ESP32-S3 antenna keepout zone, and the 12 V power planes took far longer than I had budgeted for. By the time I caught small mistakes there was very little time left to redo them. I will treat "schematic done" as roughly the halfway point of the hardware effort on the next project, not three-quarters.

3. **ESP32-S3 strapping pins must be respected at boot.** I ran into a boot-mode problem early on where GPIO0 and GPIO45 had unintended pull conditions that prevented the chip from entering normal application mode. After reviewing the boot configuration section of the datasheet I added explicit pull-up and pull-down resistors on the strapping pins and the issue cleared immediately. The lesson is that strapping-pin behavior is non-negotiable, and any nearby circuitry has to be checked against it.

4. **The DRV8434S needs both a VREF resistor divider and SPI register configuration.** I initially assumed setting VREF would be enough to limit motor current, but the DRV8434S also requires the IFS and CTRL registers to be programmed over SPI before the driver behaves correctly. Until both were set, the motor either ran weakly or at unsafe current levels. Modern stepper drivers are not drop-in replacements for older STEP/DIR ICs — they are programmable peripherals, and you have to drive them like one.

5. **Decoupling capacitor placement is not a formality.** When I first powered the board, the ESP32 reset randomly under stepper-motor load. The root cause was a 0.1 µF cap that I had placed about 8 mm from the ESP32 VDD pin, behind a via. Moving it directly under the pin on the bottom layer eliminated the resets. "Close to the pin" really does mean within a couple of millimeters, especially when there is a switching motor driver on the same board.

6. **A non-blocking UART forwarding loop is essential for daisy-chain networks.** My first version of the message parser used `delay()` calls and a blocking read, which caused the entire team ring to stall whenever my board was processing a command. Rewriting the parser around a state machine with `millis()`-based timing fixed the stall and is the structure I will reuse on any future serial-protocol project. Forwarding has to take priority over local processing.

7. **QFN packages are solderable by hand, but only with the right tools.** The DRV8434S is in a 4 mm × 4 mm QFN-24 package with a center thermal pad. I tried hand-soldering it with an iron and immediately bridged pins. A stencil with paste plus a hot-air rework station produced a clean joint on the first try. If a part is QFN, plan the assembly process before ordering — do not assume an iron will work.

8. **Test points pay for themselves the first time you need one.** I added 20 test points scattered around the board, and during bring-up I used at least half of them to verify rails, scope SPI, and watch the STEP signal. The test points cost nothing in the BOM and almost nothing in board area, and they made debugging dramatically faster. I will be even more aggressive about adding them next time and label each one clearly on the silkscreen.

9. **Power architecture should be drawn out separately from the schematic.** Trying to track which rail feeds what from the main schematic alone got confusing fast, especially when deciding between a 12 V → 5 V → 3.3 V cascade and 12 V → 5 V plus 12 V → 3.3 V in parallel. A one-page power-tree drawing would have saved me from a couple of bad early choices, and I would draw one before starting schematic capture in any future project.

10. **Defining the API early protects you from your teammates' changes.** The Front Arm API was one of the first things our team agreed on, and it stayed almost unchanged through the whole semester even as other parts of the system evolved. Because the message format was locked, I could test my subsystem independently against the spec instead of waiting for the HMI to be ready. The clearer the contract between subsystems, the less integration time you spend later.