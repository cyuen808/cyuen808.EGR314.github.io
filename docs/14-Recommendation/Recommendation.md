---
title: Recommendation
tags:
- tag1
- tag2
---


# Reflection: Recommendations for Future Students

The following five recommendations are the things I most wish I had known or done earlier in the semester. They are aimed at the student version of me on day one of EGR 314.

1. **Read the datasheet for every major component all the way through before you commit to it on the schematic**, paying particular attention to the absolute maximum ratings table, the recommended operating conditions, the boot or strapping pin behavior, and the typical application circuit, because these four sections are where almost every silent design mistake originates.

2. **Begin your PCB layout the same week you finish schematic capture, even if you expect minor schematic changes**, because routing the power plane, placing decoupling, respecting antenna keepouts, and adding thermal vias under QFN packages will consistently take more time than you predict and are nearly impossible to fix the night before a manufacturing deadline.

3. **Add at least one test point on every rail, every SPI line, every UART line, and every fault output, and label each one clearly on the silkscreen**, since test points cost almost nothing in BOM or board area but are the single biggest factor in whether you can debug a problem in minutes instead of hours when something does not work the first time you power up.

4. **Lock down your subsystem's API and message format with your team as early in the semester as possible and treat the API document as a contract**, so that you can develop and test your firmware against the spec rather than waiting for other subsystems to be ready, which prevents the entire team from collapsing into a single integration crunch in the final two weeks.

5. **Practice surface-mount soldering on cheap breakout boards before your real PCB arrives**, especially QFN and TSSOP packages with hidden thermal pads, because the first time you use solder paste, a stencil, and a hot-air station should not be on the only PCB you have for a graded assignment.