---
id: 9Y10zhASpO3oLcuQUWmfk
title: Lecture 5
desc: ''
updated: 1632116791931
created: 1632116048406
---

# Timer (Cont.) and Interrupt

## Difference between timer 0 and timer 2
* ![](/assets/images/2021-09-20-11-13-11.png)
* Reference to timer 2 means that flags will also differ.
* We have few more prescaling options that are availble in timer 2.
* Timer2 can be used in real time counter.
* In timer 2 we use TSOC1 and TSOC2. So connecting these will activate the timer 2.

## Timer 1
* ![](/assets/images/2021-09-20-11-16-29.png)
* Main difference between timer 1 and timer 0 is that timer 1 is 16 bits.
* We may split the 16 bit into two 8 bit register for HIGH and LOW.
* ![](/assets/images/2021-09-20-11-18-45.png)
    * ![](/assets/images/2021-09-20-11-19-54.png)
* The formula remains the same, **only scaling is required.**

## Interrupt
* While the microcontroller is waiting for the overflow flag to change, we are not using it. That's not desirable.
* Polling vs Interrupt
    * ![](/assets/images/2021-09-20-11-23-47.png)
* ![](/assets/images/2021-09-20-11-24-22.png)
* Example
    * ![](/assets/images/2021-09-20-11-25-23.png)
    * Note that we are simultaneously doing two things.
    * **UNDERSTAND PROGRAM FROM RECORDING**
* **Upon reset, all interrupts are disabled and to enable interrupt set MSB of status register to activate all interrupts.**
* Set bits of individual interrupts in the control registers.
* Status Registers
    * ![](/assets/images/2021-09-20-11-33-07.png)
    * Note that D7 is the MSB that represents globally enabling interrupt.
* ![](/assets/images/2021-09-20-11-34-26.png)
* TIMSK - Timer interrupt mask register
    * ![](/assets/images/2021-09-20-11-36-05.png)

# **LEFT**
