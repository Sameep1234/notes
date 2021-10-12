---
id: Y8Eu4fgviDeYqILunOUEG
title: Lecture 3
desc: ''
updated: 1630910764458
created: 1630905993189
---


# Timer (Cont.)

## Extra Points
* If prescaling is applied, we multiply the time period of the AVR microcontroller by the same amount as the prescaling ratio.
* Prescaler simply means that we are increasing the time period of the clock. Consequently, we are decreasing the frequency of the clock.
* Time Delay
    * Hex Value
        * ![](/assets/images/2021-09-06-11-10-19.png)
    * Decimal Value
        * ![](/assets/images/2021-09-06-11-11-09.png)
* To clear any flag, write logic **"1"** to it.

## Steps for programming
* ![](/assets/images/2021-09-06-11-23-39.png)
* ![](/assets/images/2021-09-06-11-32-17.png)

> Question that remains is how to store/measure overflow flag?
* For that we use TIFR (Timer/Counter Interrupt Flag Register). It has dedicated 1-bit to store every flag that we may encounter.

## TIFR Circuit
* It is an 8-bit register.
* Stores flags and **overflow flag is set on 0th bit**.
* Value "1" implies overflowed and vice versa.
> The below given figure will be provided for reference in exam.
* ![](/assets/images/2021-09-06-11-37-11.png)

* Prescalers slows down the clock. Hence increases the time period.
* Thus, multiply the prescaler to clock time period to get the adequate delay.
* Overflow flag is located on 0th bit. Hence to check overflow we check TIFR & 0x1 to be 0.
* **Make sure that to reset the flag by putting "1" to the flag.**
* The reason for this could be understood using an analogy. These are not the direct registers. These like control registers which means they act as a switch. We are pressing the "reset" switch (by putting "1") and in turn it is telling the actual register to reset the values. Thus, instead of 0, we are passing 1.
* Example questions
    * ![](/assets/images/2021-09-06-11-40-28.png)
    * ![](/assets/images/2021-09-06-11-42-27.png)
    * Toggle bits on 4th Pin of PORTB continuously with delay of 70 microseconds. Use Timer0, normal mode and 1:8 prescaler. Frequency of clock is 8MHz.
```c
#include<avr/io.h>

void T0Delay() {
    TCNT0 = 0xBA; // Calculated using the formula
    TCCR0 = 0x02; // 1:8 prescaler value using the table
    while((TIFR & 0x1) == 0); // Continuously run until flag is activated
    TCCR0 = 0; // Stop the clock
    TIFR = 0x1; // Reset the values.
}

void main() {
	DDRB = 0x10; // PORTB.4 is declared as output pin
	while(1) // Run forever
	{
		PORTB = 0x10; // Turn on
        T0Delay(); // Apply delay
        PORTB = 0x00; // Turn off
        T0Delay(); // Apply delay
	}
}
```
* Author's method
    * ![](/assets/images/2021-09-06-12-12-18.png)
