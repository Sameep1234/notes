---
id: FBmxGBrsGk0Z17PhpmtEh
title: Lecture 3
desc: ''
updated: 1630516069933
created: 1630406115130
---
## Best Fit, Measurement and Control Systems

## Points

- With one value of x, take many values of y and then take the average
- Error can occur at input as well as output side

## Standard Error and Standard Deviation

> Measures how much discrepancy (difference) is likely to be in the sample mean and the population mean.

- Std Dev = Spread of data around the mean

![](/assets/images/2021-08-27-09-42-54.png)

- In excel, multiply by sqrt(nx) and divide by sqrt(nx-1) to get the correct result
  ![](/assets/images/2021-08-27-09-44-23.png)

## Precision

> Degree of reproducibility of a measurement

- Accuracy and precision are different. **Outputs** for calculation is close enough then your calculation is precise but accuracy depends on the whether the output values are close to the actual value means it is accurate.
- It is also possible that the output is more accurate and less precise and vice versa.
  ![](/assets/images/2021-08-31-23-19-59.png)

## Resolution

> Smallest measurable increment

- Eg. Resolution of 1mv is greater than that of 10mv.
- But it also depends on the type of application. If 100mv is the measurement required then 10mv is a nice resolution and 1mv resolution will be redundant

## Span and Range

> Span: Linear operating range

- This means that the relationship between two values must be a linear relation.

> Range: Simple range (No explanation needed)

## Best Fit Line

![](/assets/images/2021-08-27-10-03-26.png)

- Error is the difference between best fit value and the actual value.

![](/assets/images/2021-08-27-10-09-13.png)

> We take n-2 because measured values are mean and not true values and two variables are involved.

## Computerized measurement and control systems

## Development of software

> Question to think: How to store the software or computer program in the circuit board?

- General purpose computer is required to build a software for specific purpose computer.
- Write the code in the laptop and then upload the code on the board.

## Arduino Board

- Components
  - Input Pins (6 Analog Pins)
  - Battery Connector/Receptor
  - Output Pins (Analog)
  - USB Connector
  - 14 Digital pins which can be used as either input or output i.e the pins are configurable.
- Voltages range from 0V to 5V.
- PWM - Pulse wave modulated (Explained in further letures).
- On the actual arduino board, they are represented by a '~' sign.
- Pin13 has built in LED for testing and hence doesn't require any external LED's in order to test the program.

## Analog to Digital converter

- For a 10 bit ADC which is generally found in arduino, there would be 1024 values starting from 0 and going to 1023 with increment as 1.
- This, means that value corresponding to 1023 is 5V.
- **ADC are linear.**

## Sampling rate of ADC

- Sampling rate = 9650 samples/sec. This is fixed for an arduino board.
- Maximum theoretical frequency of the input analog signal is half of this.

## Pulse Wave Modulation (PWM)

![](/assets/images/2021-09-01-22-26-19.png)

- As seen in the above figure, Tw is the pulse width and T is the time period of the wave.
- Average value of periodic wave = $\\frac{Area under one time period}{Time period}$
- Duty cycle ranges from 0 to 255 corresponding to 0% and 100% respectively.

## Program Structure

- ![](/assets/images/2021-09-01-22-31-18.png)
- **Statements under setup function will be executed only once and vice versa for loops.**

