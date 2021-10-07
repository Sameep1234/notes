---
id: e0FBpv1BzFYLcG066iQoi
title: Lecture 1 (Lab)
desc: ''
updated: 1633113352753
created: 1632801343461
---


# Selection and Coding

> #### This was the lab session but theory was taught.

## Criteria's to select microcontroller
* Computational need - Efficiency, cost etc.
    * 8-bit vs 16-bit vs 32-bit
    * Speed
    * Power Consumption
    * Packaging
        * Space
        * Assembling
        * Prototyping end product
    * Amount of RAM and ROM on chip
    * No. of I/O pins
    * No. of timers
    * Upgradability to new versions
    * Cost per unit
* Availability of software development tools
    * Availability of
        * Assemblers
        * Debugger
        * Code-efficient C-language compiler
        * Technical Support
        * In-house and outside expertise
* Reliable source of microcontroller
    * Number of companies supplying controller.
    * Are they reliable?
    * Will it support in future?

> We would be using AVR Microcontrollers

## Harvard vs Princeton
* Harvard
![](/assets/images/2021-09-04-18-21-51.png)
* Princeton
* ![](/assets/images/2021-09-04-18-22-18.png)

## RISC vs CISC
* CISC
    * Complex Instruction Set Computer
    * Single instruction can execute several low-level operations (including load from memory, artihmetic operations and memory store).
    * Capability of multi-step operations.
* RISC
    * Reduced Instruction Set Computer
    * Low complexity
        * Speed-up
        * Less errors in implementation
    * Less transistors
    * More space and registers
* Conclusion
![](/assets/images/2021-09-04-18-30-30.png)

## AVR Microcontrollers
* Follows Harvard Architecture
* Follows RISC architecture with CISC instruction set
* Full-form - Advanced Virtual RISC
* 8 Bit Bus (For our application)
* Pin count between 8 to 100
* Scalable
* 32 working registers
    * All connected to ALU
* Single Cycle Execution
    * One instruction per external clock
    * Low power consumption
* Efficient core
* High system level integration

## Extra points
* ![](/assets/images/2021-09-04-18-37-03.png)
* For ATMEGA, we have 4 ports each of 8 bit.
* Each pin is configurable
* Types of configuration
    * Input with internal pull-up
    * Input with no pull-up
    * Output (Driven Low)
    * Output (Driven High)
* Each Port will have **3 main registers**
    * DDRx - Data Direction Register
        * For configuring data direction (whether input or output)
    * PORTx - Port output/Driver Register
        * Output Mode
    * PINx - Port Input Register
        * Reading Mode

> **How to give direction?**

* For any Pin, if it is defined 0, then it represents input pin and vice versa.

## Examples of Program
* ![](/assets/images/2021-09-04-18-45-38.png)
* ![](/assets/images/2021-09-04-18-48-57.png)
