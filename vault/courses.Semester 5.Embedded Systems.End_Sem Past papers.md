---
id: xlj6wGdQKowx94MW95Ryg
title: End_Sem Past papers
desc: ''
updated: 1638644975554
created: 1638638927432
---

## [2019 Paper](https://drive.google.com/drive/u/1/folders/1FYfaFuadfY0DujErCQJNTppBCIYFuUYK)

#### A1
![](/assets/images/2021-12-04-23-10-05.png)

#### A3
![](/assets/images/2021-12-04-23-11-14.png)

#### A4
```c
#include<avr/io.h>
void main(){
    DDRA = 0x00;
    DDRB = DDRC = DDRD = 0XFF;
    int temp,x,d1,d2,d3;
    while(1){
        temp = PINA;
        x = temp/10;
        d2 = x%10;
        d1 = temp%10;
        d3 = x/10;
        PORTB = d1;
        PORTC = d2;
        PORTD = d3;
    }
}
```

#### A5
```c
#include<avr/io.h>
#include<avr/interrupt.h>
T0delay(){
    TCCR0 = 0x05;
    TCNT0 = 11;
    while(TIFR&0X01 == 0);
    TIFR = 0X01;
    TCCR0 = 0X00;
}

int i = 9;

void main(){
    DDRA = 0xFF;

    int arr[] = {0x90, 0x80, 0xF8, 0x82, 0x92, 0x99, 0xB0, 0xA4, 0xF9,0xC0}

    MCUCR = 0x01; // Modes of external interrupt 
    GICR = 0x40; // Local interrupt
    sei(); // Global interrupt

    while(1){
        PORTA = arr[i];
        i -= 1;
        if(i == 0)
        {
            i = 9;
        }
        T0delay();
        T0delay();
        T0delay();
        T0delay();
    }
}

ISR(INT0_vect)
{
    i = 9;
}
```

#### A6
* Circuit Diagram
    * ![](/assets/images/2021-12-05-00-36-49.png)


```c
/* 
    Two switches -> b.6,b.7
    Switch press, PORTB.6 or 7 = 1
    4 H bridge switch connected to PORTA 1-4
    Red led at a.6 and greed led to a.7
    a. If input from Pin 6 of Port B is “1” and input from Pin 7 of Port B is “0”, rotate the
    motor in clockwise direction.
    b. If input from Pin 6 of Port B is “0” and input from Pin 7 of Port B is “1”, rotate the
    motor in counter clockwise direction.
    c. In all other input conditions, turn off the motor.
    d. Whenever the motor is ON, rotating in any direction, turn ON the green LED.
    e. Whenever the motor is OFF, turn on the red LED.
*/

#include<avr/io.h>

void main()
{
    DDRB = 0x00;
    DDRA = 0xFF;
    while(1)
    {
        if(PINB.b6 == 1 && PINB.b7 == 0)
        {
            PORTA = 0x92; // Clockwise direction + Green led
        }
        else if(PINB.b7 == 1 && PINB.b6 == 0)
        {
            PORTA = 0x8C; // Anticlockwise + Green led
        }
        else
        {
            PORTA = 0x40; // Motor off + red led
        }
    }
}
```
#### A7
```c
#include<avr/io.h>
vid main(){
    DDRB = 0XFF;
    int i = 0;
    while(1)
    {
        for(i = 0;i<(255/2);i++)
        {
            PORTA = i;
        }
        for(i = (255/2);i>=0;i--)
        {
            PORTA = i;
        }
        for(i = 0;i<(255);i++)
        {
            PORTA = i;
        }
        for(i = (255);i>=0;i--)
        {
            PORTA = i;
        }
    }
}
```

#### A8
```c

```