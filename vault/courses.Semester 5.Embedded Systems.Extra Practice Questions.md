---
id: xW8W5qOSZTQ1B2xPNY4gZ
title: Extra Practice Questions
desc: ''
updated: 1633150517035
created: 1633146584123
---

## Question 1
> Program to toggle PB4 every 2ms. Use Timer1, Normal Mode and no prescaler and assume clock frequency = 8MHz.

```c
#include<avr/io.h>

void T1Delay()
{
    TCNT1 = 49536; // TCNT1 Value for 2ms delay
    
    TCCR1 = 0x0001; // TCCR1 value for normal mode, no prescaling.
    /* Can also be written as follows
        TCCR1H = 0x00;
        TCCR1L = 0x01; 
    */
    
    while((TIFR & 0x04) == 0); // Run until timer1 TOV1 flag overflows

    TIFR = 0x04; // Reset flags
    TCCR1 = 0x0000; // Stop clock
}

void main()
{
    DDRB = 0x10; // Declare PORTB.4 as output
    while(1) // Run forever
    {
        PORTB ^= 0x10; // Toggle PORTB.4
        T1Delay(); // Apply delay
    }
}
```

## Question 2
> Assuming that a 1Hz clock pulse is fed into into pin T0 (PB0), use the TOV0 flag to extend Timer0 to a 16-bit counter and display the counter on PORTC and PORTD

```c
#include<avr/io.h>

void main()
{
    DDRC = 0xFF; // Declare PORTC as output
    DDRD = 0xFF; // Declare PORTD as output

    PORTB = 0x01; // Activate pull up
    
    TCCR0 = 0x06; // TCCR value for external clock
    TCNT = 0x00; // Start counter from 0

    while(1) // Run forever
    {
        PORTC = TCNT0; // Transfer content of TCNT0 to PORTC
        while((TIFR & 0x01) == 0) // Run untill roll over
        {
            PORTC = TCNT0; // Transfer continuously to PORTC
        }

        TIFR = 0x01; // Reset flags
        PORTD += 1; // Increment PORTD
    }
}
```

## Question 3
> Assume 1Hz external clock is fed to PB1 (T1). Program for counter1 in rising edge mode to count the pulses and display the TCNT1H and TCNT1L registers on PORTD and PORTC, respectively

```c
#include<avr/io.h>

void main()
{
    PORTB = 0x02; // Activate pull-up

    DDRC = 0xFF; // Output mode for PORTC
    DDRD = 0x0FF; // Output mode for PORTD

    TCCR1 = 0x0006; // External clock source, no prescaling

    TCNT1 = 0x0000; // Set count to 0

    while(1) // Run forever
    {
        // Perform the required task
        PORTC = TCNT1L;
        PORTD = TCNT1H;

        while((TIFR & 0x04) == 0)
        {
            PORTC = TCNT1L;
            PORTD = TCNT1H;
        }

        TIFR = 0x04; // Reset Flag
    }
}
```

