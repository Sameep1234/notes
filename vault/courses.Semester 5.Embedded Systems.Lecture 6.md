---
id: I1yfE0thWPqo0yAmN8xou
title: Lecture 6
desc: ''
updated: 1632723791302
created: 1632723062497
---

# External Hardware Interrupts

## Activation
* ![](/assets/images/2021-09-29-10-43-25.png)
* Now to activate external hardware interrupt, we use GICR and the first 3 LSB side bits should be set according to our use case and in correspondence with the image above.

## Features
* ![](/assets/images/2021-09-29-10-45-07.png)
* When we set the interrupts value to be 00, it is also called as **level-triggered interrupt.**
* **Note that 00 corresponds to lower level interrupt which means on connecting group or providing 0, this interrupt will get triggered and on connecting Vcc or providing 1, this interrupt will be disabled.**
* Interrupt 2
    * ![](/assets/images/2021-09-29-10-50-01.png)
    * **Note that there is onyl one bit for interrupt 2 and hence only 2 possible combinations ar shown in the image above.**
* Now for example, lets say we want to make INT0 interrupt on falling edge triggered. For this, we choose the value of MCUCR = 0x02.
* For INT2, rising edge trigger, write MCUCSR = 0x40. We made D6 to be 1 because the MCUCSR has PIN6 dedicated to interrupt 2.
* **Make sure that if INT2 is asked, you change D6 of MCUCSR and if INT1 or INT0 is asked, you chance (D2, D3) and (D0, D1) respectively.**

## GIFR
* General Interrupt Flag Register.
* ![](/assets/images/2021-09-29-11-01-33.png)
* Programmer need not worry of clearing the flag as it will be done automatically.

## Minimum timing of Interrupt Signal
* Minimum timing of interrupt signal means what should be the minimum time for which the interrupt should last so that it is considered as an interrupt and not as a noise.
* ![](/assets/images/2021-09-29-11-03-22.png)

## Examples
* ![](/assets/images/2021-09-29-11-07-25.png)
```c
#include<avr/io.h>
#include<avr/interrupt.h>

int main()
{
    DDRC = 0x08; // Define PortC.3 as output
    PORTD = 0x02; // Interrupt comes here. We can also write PORTD = 1<<2;
    GICR = (1<<INT0); // Enable external interrupt 0
    sei(); // Enables global interrupts

    MCUCR = 0; // Level triggered mode
    while(1); // Run forever
}

ISR (INT0_vect)
{
    PORTC ^= 0x08; // Toggling whenever INT0 goes low
}
```
## Interrupt Priority
* ![](/assets/images/2021-09-29-11-28-58.png)