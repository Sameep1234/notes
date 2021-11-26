---
id: AjAwbCGQG0EQnKwLHQkjF
title: Lecture 9
desc: ''
updated: 1637898856515
created: 1635140067611
---

# Keyboard (Cont.), Switches, Relays and Opto-Isolators

## Points
* ![](/assets/images/2021-10-25-11-39-22.png)

## C program to read keypad and send result to PORTD
* Note that here Columns are connected in PC0 - PC3 and rows are connected to PC4 - PC7.
* ![](/assets/images/2021-11-26-09-02-21.png)
    * The above code maintains all the initialization work.
    * Sets KEY_PRT and other variables to the required values.
* ![](/assets/images/2021-11-26-09-03-22.png)
    * This part of the code checks whether initially keyboard is pressed then allow everything to complete.
    * Then ground all the rows and read the columns
* ![](/assets/images/2021-11-26-09-05-23.png)
    * If key is pressed, check which one is pressed.
    * Thus, one by one we ground the rows and check the value of column.
* ![](/assets/images/2021-11-26-09-07-36.png)
    * Finally, use the lookup array created in the first image and use it to identify which key was pressed.
    * Then, send it to PORTD for output.

## Extra Points
* ![](/assets/images/2021-11-26-09-16-37.png)
* ![](/assets/images/2021-11-26-09-16-46.png)
* BJT (Bi-polar Junction Transistor) as a switch
    * ![](/assets/images/2021-11-26-09-17-35.png)
* Transistors
    * We can switch devices using transistors
    * It amplifies the signals
    * Circuit Diagram
        * ![](/assets/images/2021-11-26-09-18-34.png)
    * Darlington Transistors
        * ![](/assets/images/2021-11-26-09-19-10.png)
    * MOSFET as a switch
        * ![](/assets/images/2021-11-26-09-20-04.png)

## Relays
* ![](/assets/images/2021-11-26-09-20-40.png)
* Components
    * Coil
    * Spring
    * Contacts
* Relay Diagrams
    * ![](/assets/images/2021-11-26-09-21-38.png)
* Limitations of electromechanical relays
    * Low life expectancy
    * High wear and tear
* Advantages of Sold State Relays
    * High life expectancy
    * Low wear and tear

## Opto-Isolators
* ![](/assets/images/2021-11-26-09-24-53.png)
* Components
    * LED
    * Photo-Transistor
* Controlling a lamp via optoisolator
    * ![](/assets/images/2021-11-26-09-27-14.png)