

## Timers (Cont.)

> Program to generate square wave of time period 100 micro second on Pin 1 of Port A and clock frequency of 1Mz

```c
#include<avr/io.h>

void T0Delay() {
    TCNT0 = 206; // Time delay is of 50 microseconds and not 100 microseconds.
    TCCR0 = 0x01; // Normal mode and no prescaling
    while((TIFR & 0x1) == 0); // Check for counter
    TCCR0 = 0; // Stop the clock
    TIFR = 0x1; // Reset flags
}

int main() {
    DDRA = 0x02; // Define PIN 1 of PORTA to be ouput
    while(1)
    {
        PORTA = 0x02; // Turn PIN 1 of PORTA on
        T0Delay(); // Provide time delay
        PORTA = 0x00; // Turn PIN 1 of PORTA off
        T0Delay(); // Proivde time delay
        // This will generate a square wave form.
    }
    return 0;
}
```

* * *

> ![](/assets/images/2021-09-13-11-42-59.png)

- The outside signal will come from pins of ports as they can have alternate functions too.
- These pins will take the input from port.
- Follow this for more functions
  - ![](/assets/images/2021-09-13-11-44-23.png)
- For internal purpose, assume that the clock frequency is 1Mz. **Note that 1Hz is from outside world.**

```c
#include<avr/io.h>

int main() {
    DDRB = 0x00; // Declare whole port as input because this is where external signal will arrive.
    DDRC = 0xFF; // Declare whole port as output because this is where we will be displaying the count of TCNT.
    PORTB = 0x00; // Set PORTB to 0
    while(1) { // Run forever
        TCCR0 = 0x06; // External clock with falling edge value from the table
        PORTC = TCNT0; // Display contents of TCNT0 on PORTC
    }
    return 0;
}
```

## CTC Mode

- It is compare mode. This means that instead of going till 0xFF, it will drop at the set value.
- It may or may not be equal to 0xFF.
- Now to compare the flag, we compare with 0x02. (i.e flag 1 instead of flag 0).
- **This is because the overflow flag is not affected, the compare flag is affected.**

> Program to generate a square wave of time period 150 microseconds on PIN 1 of PORT A. Assume cystal frequency = 1MHz. use timer in CTC mode.

- Note that the delay of 150 microseconds is for the whole wave.
- Thus, if we need a delay for only one part of the wave, we need to use a delay of 75 microseconds.
- Now we want to write the value of OCR0.
- Make sure to change the value of TCCR0 for CTC mode.
- Now, the time duration will depend not only on TCNT0 but also on OCR0.
- In normal mode, we are concerned with FF - TCNT0 value but here we are concerned with OCR0 - TCNT0 which must be 75.
- Note that one must always be careful about which flag are we going to use.
- In **normal mode**, we are waiting for **overflow flag** whereas in **CTC mode** we are waiting for the **compare flag**.
- For simplicity, you can put TCNT0 value to be 0 and OCR0 value to be 75. **The concept remains the same i.e OCR-TCNT should be 75.**
-

```c
#include<avr/io.h>

void T0Delay() {
    TCNT0 = 0; // TCNT0 = 0
    OCR0 = 75; // OCR0 - TCNT0 = 75 and TCNT0 = 0
    TCCR0 = 0x09; // TCCR0 value for CTC mode and no prescaling
    while( (TIFR & 0x2) == 0); // Check 1st bit
    TCCR0 = 0; // Stop clock
    TIFR = 0x2; // Reset flags
}

int main() {
    DDRA = 0x02; // Set PORTA.1 as output pin
    while(1) { // Run forever
        PORTA = PORTA ^ 0x02; // Toggle value at PORTA
        T0Delay(); // Apply time delay
    }
    return 0;
}
```

- Now suppose, we start the value of TCNT0 with 200, then how will the OCR value change?
- For this case, we find the extra distance i.e find from where it "rolls over".
- Thus, the value of OCR must be 19 becuase from 200 to 256, we would have covered 56 values and then 19 values remain to provide a proper delay of 75 microseconds.

