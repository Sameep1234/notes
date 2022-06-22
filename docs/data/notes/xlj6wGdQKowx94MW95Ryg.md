
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
void main(){
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
* ![](/assets/images/2021-12-05-10-05-21.png)
* ![](/assets/images/2021-12-05-10-05-52.png)
* ![](/assets/images/2021-12-05-10-06-13.png)
* ![](/assets/images/2021-12-05-10-06-27.png)
* **Note that you must change some values corresponding to 3X3 keyboard as in the above image it is 4x4 keyboard.**

___

9. d
10. b (**Note sure**)
11. Out of syllabus
12. d
13. b

## [2019 paper link](https://drive.google.com/drive/u/1/folders/1FYfaFuadfY0DujErCQJNTppBCIYFuUYK)

#### A1
* ![](/assets/images/2021-12-05-10-14-03.png)

#### A2
* ![](/assets/images/2021-12-05-10-15-06.png)

#### A3
* Out of syllabus

#### A4
```c
#include<avr/io.h>
void main(){
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

#### A5
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
    int i = 0, a, b;
    while(1)
    {
        for(i = 3;i>=0;i--)
        {
            a = 1<<i;
            b = 1<<(7-i);
            PORTB = a | b;
            T0Delay();
        }
    }
}
```

#### A6
```c
/*
    Green --> A.7
    Red --> A.6
*/

#include<avr/io.h>

void main()
{
    DDRA = 0XFC;

    while(1){
        if((PINA.b0 == 1 && PINA.b1 == 0) || (PINA.b0 == 0 && PINA.b1 == 1)) // Only one switch on
        {
            OCR0 = 127;
            TCNT0 = 0x00;
            TCCR0 = 0x69;
            PORTA = 0xA0; // Green led on and motor on
        }
        else if(PINA.b1 == 1 && PINA.b0 == 1)
        {
            OCR0 = 255;
            TCNT0 = 0;
            TCCR0 = 0x69;
            PORTA = 0xA0; // Green led on and motor on
        }
        else
        {
            PORTA.b6 = 1; // Red led on and motor off
        }
    }
}
```
* Circuit Diagram
    * ![](/assets/images/2021-12-05-10-51-45.png)

#### A7
```c
// Pin a.0 = input
// Pin c.1 and c.2 = output
#include<avr/io.h>

void main()
{
    DDRC = 0xFF;
    DDRA = 0x00;
    ADCSRA = 0x87; // Clk/128 prescaler, bit set
    ADMUX = 0xC0; // Internal Vref, right justified, single-ended input

    while(1)
    {
        ADCSRA = 1<<ADSC // Start conversion
        while(ADCSRA & (1 << ADIF) == 0); // Wait for conversion to complete
        int temp = ADCL; // Store ADC output to temp variable
        if(temp > 25 && temp % 2 != 0)
        {
            PORTA.b1 = 1; // Turn on one AC system
        }
        else if(temp > 25 && temp % 2 == 0)
        {
            PORTA.b2 = 1; // Turn on one AC system
        }
        else if(temp < 15)
        {
            PORTA = 0x00; // Turn off all AC's
        }
    }
}
```

___

8. **Doubt**
9. a, b, c
10. d
11. Out of syllabus
12. d
13. b (not sure though)
14. g (not sure though)
15. **Doubt**
16. Out of syllabus
17. **Doubt**
18. **Either Doubt or out of syllabus**
19. a,d
20. b
21. a, b, c, d **Check once**
22. a, b, c, d **Check once**