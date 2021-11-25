---
id: 5FAxFWz4cUpEAUCPvyY3f
title: Lecture 2
desc: ''
updated: 1630820936096
created: 1630817213184
---


## Timers

## Timers in AVR

- ![](/assets/images/2021-09-05-10-37-02.png)
- ATMEGA32
  - Timer 0: 8-bit
  - Timer 1: 16-bit
  - Timer 2: 8 bit
- Example
  - ![](/assets/images/2021-09-05-10-48-08.png)
  - Complex Solution
    ![](/assets/images/2021-09-05-10-50-57.png)

## Components

- TCCR: Timer/Counter Control Register
  - 8-bit register
  - ![](/assets/images/2021-09-05-11-18-21.png)
  - When you put 000, timer stops if it is running.
  - Other information given in the image above.
- TOV: Timer Overflow
- TCNT: Timer/Counter Register
  - 8-bit register that increments count.
  - It is a read/write register.
  - **Increments every clock cycle.**
  - Overflow occurs at 0xFF.
  - ![](/assets/images/2021-09-05-11-02-40.png)
- OCR: Output Compare Register
  - It is a read/write 8-bit register.
  - Continuously compared with counter value i.e TCNT value.
  - Used majorly when we are using timer in CTC mode.
- OCF: Output Compare flag
  - If the value compared by the OCR matches the value in TCNT, this flag will be turned on to represent the overflow.

## Circuit (Timer 0)

![](/assets/images/2021-09-05-10-59-49.png)

