---
id: ofEMyVSSXfsXPcumprwj7
title: Lecture 10
desc: ''
updated: 1638014140383
created: 1638000069171
---

# Programs and Motors (Stepper and DC)

## Extra Programs
* ![](/assets/images/2021-11-27-16-58-48.png)
```c
#include<avr/io.h>

int main()
{
    DDRA = 0x02;
    while(1)
    {
        PORTA.b1 = PINA.b0;
    }
    return 0;
}
```
* Circuit for the above question
    * ![](/assets/images/2021-11-27-17-12-13.png)

## Stepper motors
* Device that translates electrical pulses into mechanical movements.
* Applications include
    * Disk Drives
    * Dot matric printers
    * Robots
    * Industrial Automation
* Some specifications
    * ![](/assets/images/2021-11-27-17-15-49.png)
* Rotor Alignments
    * ![](/assets/images/2021-11-27-17-16-05.png)
* Windings
    * ![](/assets/images/2021-11-27-17-23-49.png)
* Avr connection
    * ![](/assets/images/2021-11-27-17-23-38.png)
* Step Angles
    * ![](/assets/images/2021-11-27-17-24-10.png)
* Step sequences
    * ![](/assets/images/2021-11-27-17-24-29.png)
* Question
    * ![](/assets/images/2021-11-27-17-25-27.png)
    * ![](/assets/images/2021-11-27-17-25-37.png)
    * ![](/assets/images/2021-11-27-17-25-52.png)
    * ![](/assets/images/2021-11-27-17-45-36.png)
    * ![](/assets/images/2021-11-27-17-46-05.png)