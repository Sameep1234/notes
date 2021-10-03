---
id: xW8W5qOSZTQ1B2xPNY4gZ
title: Extra Practice Questions
desc: ''
updated: 1633244028732
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

## Question 4
> Using Timer0 and Timer1 interrupts, generate square waves on pins PB1 and PB7 respectively while transferring data from PORTC to PORTD

```c
#include<avr/io.h>
#include<avr/interrupt.h>

void main()
{
    DDRB = 0x82; // Declare pins B2 and B7 as output
    DDRC = 0x00; // Input PORTC
    DDRD = 0xFF; // Output PORTD

    TCNT0 = 0x00; // Start timer0 from 0 i.e max delay
    TCNT1H = 0x00;
    TCNT1L = 0x00; // Start timer1 from 0 i.e max delay

    TCCR0 = 0x01; // Normal mode, no prescaler timer0
    TCCR1 = 0x0001; // Normal mode, no prescaler timer1

    TIMSK = 0x05; // Enable local interrupt for timer1 and timer0
    sei(); // Enable global interrupts

    while(1) // Run forever
    {
        PORTD = PINC; // Transfer data from PORTC to PORTD
    }
}

ISR(TIMER0_OVF_vect)
{
    TCNT0 = 0x00; // Reset timer0 again
    PORTB ^= 0x02; // Toggle PORTB.1
}

ISR (TIMER1_OVF_vect)
{
    TCNT1 = 0x0000; // Reset timer1 again
    PORTB ^= 0x80; // Toggle PORTB.7
}
```

## Question 5
> Using Timer0 and Timer1 interrupts, write a program in which PORTA counts up everytime Timer1 overflows (after every 1 sec it overflows) and a pulse is fed into Timer0 where Timer0 is used as counter and counts up. Furthermore whenever the counter reaches 200, it will toggle the pin PORTB.6. All these should happen while transferring data from PORTC to PORTD. Assume XTAL = 1MHz.

```c
#include<avr/io.h>
#include<avr/interrupt.h>

void main()
{
    DDRB = 0x40; // Declare PORTB.4 as output pin
    DDRA = 0xFF; // Declare whole PORTA as output
    DDRD = 0xFF; // Declare whole PORTD as output
    DDRC = 0x00; // Declare PORTC as input

    PORTB = 0x01; // Activate pull-up

    TCNT0 = -200 // Load Initial value of TCNT0
    TCNT1 = 34286 // Value for 1 sec delay using 1:256 prescaler

    TCCR0 = 0x06 // External clock, falling edge, no prescaler
    TCCR1 = 0x0004; // Normal mode, 1:256 prescaler

    TIMSK = 0x05;  // Enable local interrupts for Timer1 and Timer0
    sei(); // Enable Global interrupts

    while(1) // Run forever
    {
        PORTD = PINC; // Transfer data as required
    }
}

ISR(TIMER0_OVF_vect)
{
    TCNT0 = -200; // Reset count value timer0
    PORTB ^= 0x40; //Toggle PORTB.6 
}

ISR(TIMER1_OVF_vect)
{
    TCNT1 = 34286; // Reset count value timer1
    PORTA++; // Increment value as mentioned
}
```

## Question 6
> Assume that the INT0 pin is connected to a switch that is normally high. Write a program that toggles PORTC.3 **only once** whenever INTO pin goes low.

```c
#include<avr/io.h>
#include<avr/interrupt.h>

void main()
{
    DDRC = 0x04; // Declare PORTC.3 as output
    PORTD = 0x04; // Activate External pull-up

    MCUCR = 0x02; // INT0 is falling edge triggered
    GICR = 0x40; // Enable INT0 local interrupt
    sei(); // Enable global interrupts

    while(1); // Run forever and do nothing
}

ISR(INT0_vect)
{
    PORTC ^= 0x04; // Toggle PORTC.3
}
```

> Not clear understanding of Question 6.

## Mid sem 2020 Q6
```c
#include<avr/io.h>
#include<avr/interrupt.h>

T0delay(){

    TCNT0 = 0;
    OCR0 = 75;
    TCCR0 = 0x08;
    while(TIFR&0X02 == 0){}
    TCCR0 = 0x00;
    TIFR = 0x02;
}

void main()
{
    DDRA = 0x0F;
    int i;
    int temp;
    while(1)
    {
        for (i=7;i>=0;i-=2)
        {
            temp = 1<<i;
            temp = temp | (1<<(i-1));
            PORTA = temp;
            T0delay();
        }
    } 
}
```

## Mid sem 2020 Q7
```c
#include<avr/io.h>
#include<avr/interrupt.h>

T0delay(){
    TCNT0 = 156;
    TCCR0 = 0X01;
    While(TIFR & 0X01 == 0);
    TCCR0 = 0;
    TIFR = 0X01;
}
int counter = 0;
void main()
{
    int bin,x,d2,d1;
    DDRD = 0XFF;

    DDRC = 0XFF;
    DDRB = 0XFF;

    DDRA = 0X00; // INPUT

    MCUCR = 0x03;
    GICR = 0x40;
    TIMSK = 0x01;
    sei();

    while(1){
        bin = pinA;
        x = bin/10;
        d1 = bin%10;
        d2 = x%10;
        PORTB = d1;
        PORTC = d2;
    }
}

ISR(TIMER0_OVF_vect){
    PORTD.b7 = 1;
    T0delay();
    PORTD.b7 = 0;
    T0delay();
}

ISR(INT0_vect){
    counter++;
    if(counter<120){
        PORTD.b5 = 1;
        PORT.b6 = 0;
    }
    else{
        PORT.b6 = 1;
        PORT.b5 = 0;
    }
}
```

## Mid sem 2019 Q5
```c
#include<avr/io.h>

void main(){
    DDRA = 0x00;
    DDRB = 0x00;
    DDRC = 0XFF;

    int x,y, combined;
    x = PINA & 0x0F;
    y = PINB & 0X0F;
    if(x%2 ==0){
        combined = y<<4 | x;
        PORTC = combined;
    }
    else{
        combined = x<<4 | y;
        PORTC = combined;
    }
}
```

## Mid sem 2019 Q6
```c
#include<avr/io.h>
#include<avr/interrupt.h>

T0delay(){

    TCNT0 = 163;
    TCCR0 = 0x02; // Prescaler of 1:8
    while(TIFR&0X01 == 0){}
    TCCR0 = 0x00;
    TIFR = 0x01;
}

void main()
{
    DDRA = 0x0F;
    int i;
    while(1)
    {
        for (i=0;i<=7;i++)
        {
            PORTA = 1<<i;
            T0delay();
        }
    } 
}
```

## Mid sem 2019 Q7
```c
#include<avr/io.h>
#include<avr/interrupt.h>

void main(){
    DDRA = 0XFF;
    DDRB = 0x00;
    DDRD = 0X01;

    MCUCR = 0x0B;
    GICR = 0xC0;
    sei();    

    PORTB = 0x01; // Activate Pull-up
    while(1){
        if(PORTA <= 100)
            PORTA ++;
        else 
            PORTA = 0x00;
    }
}

ISR(INT0_vect){
    PORTD.b0 ^= 1;
}

ISR(INT1_vect)
{
    PORTC++;
}
```

## Mid sem 2018 Q4
```c
#include<avr/io.h>

void main()
{
    DDRA = 0x00;
    DDRB = DDRC = DDRD = 0xFF;
    int x, d1,d2,d3, y;

    while(1)
    {
        x = PINA;
        y = x / 10;
        d1 = x % 10;
        d2 = y % 10;
        d3 = y / 10;

        PORTB = d1;
        PORTC = d2;
        PORTD = d3;
    }
}
```

## Mid sem 2018 Q5
```c
#include<avr/io.h>

void T0Delay()
{
    TCCR0 = 0x01;
    TCNT0 = 206;
    while((TIFR & 0x01) == 0);
    TIFR = 0x01;
    TCCR0 = 0x00;
}

void main()
{
    DDRB = 0xFF;
    int i, temp;

    while(1)
    {
        for(i=0;i<8;i++)
        {
            temp = 1<<i;
            PORTB = temp | 1<<(7-i);
            T0Delay();
        }
    }
}
```

## Mid sem 2018 Q6
```c
#include<avr/io.h>
#include<avr/interrupt.h>

void T0Delay()
{
    TCCR0 = 0x08;
    TCNT0 = 0;
    OCR0 = 50;
    while((TIFR & 0x02) == 0);
    TIFR = 0x02;
    TCCR0 = 0x00;
}

void main()
{
    DDRD = 0xFF;
    DDRA = 0x00;
    DDRC = 0xFF;
    int x;

    GICR = 0x40; // Local interrupt
    MCUCR = 0x02; // Mode
    sei(); // Global interrupt

    while(1)
    {
        x = PINA;
        PORTC = (x >> 1);
    }
}

ISR(TIMER0_COMP_vect)
{
    PORTD ^= 0x10;
    T0Delay();
}

ISR(INT0_vect)
{
    PORTD.b5 ^= 1; 
}
```