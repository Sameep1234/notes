---
id: ckKKWyITAGuTpRuAzzfzu
title: Lecture 6
desc: ''
updated: 1632723791302
created: 1632723062497
---

![](/assets/images/2021-09-27-11-41-28.png)
```c
#include<avr/io.h>
#include<avr/interrupt.h>

int main()
{
    DDRC = 0x08;
    PORTD = 1<<2;

    sei(); // Enables global interrupt

    while(1); // Wait here
}

ISR (TIMER0_vect)
{
    PORTC ^= 0x08;
}
```