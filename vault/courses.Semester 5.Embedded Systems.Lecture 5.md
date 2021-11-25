---
id: F6rwo77eZsK7lVh72shS4
title: Lecture 5
desc: ''
updated: 1632881828985
created: 1632116048406
---


## Timer (Cont.) and Interrupt

## Difference between timer 0 and timer 2

- ![](/assets/images/2021-09-20-11-13-11.png)
- Reference to timer 2 means that flags will also differ.
- We have few more prescaling options availble in timer 2.
- Timer2 can be used in real time counter.
- In timer 2 we use TSOC1 and TSOC2. So connecting these will activate the timer 2.

## Timer 1

- ![](/assets/images/2021-09-20-11-16-29.png)
- Main difference between timer 1 and timer 0 is that timer 1 is 16 bits.
- We may split the 16 bit into two 8 bit register for HIGH and LOW.
- ![](/assets/images/2021-09-20-11-18-45.png)
  - ![](/assets/images/2021-09-20-11-19-54.png)
- The formula for finding time delay remains the same, **only scaling is required.**

## Interrupt

- While the microcontroller is waiting for the overflow flag to change, we are not using it. That's not desirable.
- The above mentioned process is called polling method in which we are continuously checking the value of flag.
- Polling vs Interrupt
  - ![](/assets/images/2021-09-20-11-23-47.png)
- ![](/assets/images/2021-09-20-11-24-22.png)
- **Always remember that the timer operations are performed under interrupt service routine whereas the main task other than timer is done in main function.**
- Example
  - ![](/assets/images/2021-09-20-11-25-23.png)
  - Note that we are simultaneously doing two things.
  - Here we are performing bitwise OR operation on DDRB to make PIN 5 as output but it is not necessary. We can simply assign it too like we used to do.
  - Then we assign value of TCNT0 that will run 32 times. Roughly it means it is FF - 32.
  - Then, in the main function, we perform the task of transferring data from PORTD to PINC.
  - Now inside ISR, we reassign value of TCNT0 and toggle the PORTB.
- **Upon reset, all interrupts are disabled and to enable interrupt set MSB of status register to activate all interrupts. This means enabling global interrupts.**
- **Set bits of individual interrupts in the control registers. This means enabling local interrupts.**
- Note that we do not have to manually update the value of status register, we just have to call sei() function in C to enable the global interrupt.
- Similarly to disable global interrupt, we have to call cli() function in C.
- Status Registers
  - ![](/assets/images/2021-09-20-11-33-07.png)
  - Note that D7 is the MSB that represents globally enabling interrupt.
- ![](/assets/images/2021-09-20-11-34-26.png)
- sei() and cli() enables and disables **global interrupt** respectively.
- TIMSK - Timer interrupt mask register
  - Note that right now we are concerned with **internal interrupt** only.
  - ![](/assets/images/2021-09-20-11-36-05.png)
  - This means that if you set the appropriate bit (for us, since we are using timer0, we set TOIE0 = 1).
  - Thus, we write TIMSK = (1&lt;&lt;TCIE0) for enabling **local interrupt.**
- interrupt service routine (ISR) (VECTOR TABLE)
- ![](/assets/images/2021-09-29-07-48-38.png)
- TIMER0_OVF_vect means that we are sending overflow flag as a parameter to ISR which will enable the overflow flag **on interrupt** and set the program counter's value to the corresponding location.
- Now inside ISR, we perform timer related operations i.e reassigning TCNT0 value and toggling PORTB's value for generating square.

## Steps in executing an interrupt

- ![](/assets/images/2021-09-29-07-53-22.png)
- Interrupt Vector Table
  - ![](/assets/images/2021-09-29-10-24-57.png)
  - After the first step is completed, based on the interrupt given, the program counter goes to that particular vector address as per the above image shown.

## External Input

- ![](/assets/images/2021-09-29-10-40-57.png)
- The red colored pins are external interrupts.

## Extra Points

- ![](/assets/images/2021-09-29-07-52-43.png)

