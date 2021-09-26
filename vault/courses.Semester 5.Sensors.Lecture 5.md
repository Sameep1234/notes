---
id: KzrsbwIvpC6O1heU07aE8
title: Lecture 5
desc: ''
updated: 1632043925100
created: 1630568071794
---


# Control Systems

## Introduction
* System which controls a physical quantity.
* Components of control system
    * Control element (Eg. Timer)
    * Plant (Eg. Heating coil)
* Type of control system
    * Open Loop: Control action is independent of the control variable.
        * We must assume the timer setting to be correct.
        * Block Diagram
        ![](/assets/images/2021-09-02-13-09-13.png)
    * Closed Loop: Control action is dependent of the control variable.
        * User will have manual control.
        * Feedback recieved with the help of human senses. Can also be used as feedback in automatic control systems. For this, the feedback has to be electrical.
        * This means that the control action depends on the output variable.
    * There are various other factors which can't be known and hence are assumed to be constant. For example, ageing and changes in load weight. 
    * The main difference between open loop and close loop system is of feedback which is not present in open loop system.

## Steady state calculation
![](/assets/images/2021-09-02-13-20-17.png)
* A is the gain of the amplifier. It is dimensionless. Also called as the loop gain.
* Km is the motor constant. Upto Km, we will get the **speed** of the motor.
* Ks is the sensor constant. Speed sensors input is speed and output is voltage. Dimension of Ks is opposite tso that of Km. Ks = $\frac{Vf}{N}$.
* N = speed in rpm.
* A*Km*Ks is called the loop gain of the system. So larger its value, the smaller is the difference and hence we get almost equal value to Vs.
* So it is better to obtain loop gain of 100 and it is achievable.

## Specification of control systems
* Accuracy of output in steady state.
* Speed of response.
* Feedback (Improves both).
    * Because of this, the effective time constant is reduced and hence speed and accuracy is improved.

## Steps in analysis of control system
![](/assets/images/2021-09-02-13-49-06.png)

## Example of Oven
* Block Diagram
    * ![](/assets/images/2021-09-19-14-39-38.png)
* The rate of increase depends on thermal resistance and thermal capacitance.
* ![](/assets/images/2021-09-19-14-42-28.png)
* Heat flow is in watts. Theta is in degrees and thus thermal resistance is in degrees per watts.
* ![](/assets/images/2021-09-19-14-45-07.png)
* ![](/assets/images/2021-09-19-14-45-30.png)
* Mathematical model of oven
    * ![](/assets/images/2021-09-19-14-46-21.png)
* **For steady state**
    * ![](/assets/images/2021-09-19-14-47-40.png)
    * 'q' is the coil wattage of the oven.
* Electrical Equivalent
    * ![](/assets/images/2021-09-19-14-50-15.png)
    * Note that the electrical equations are just the analogous equations.

## Set Point and Closed system equivalent
* The temperature reached in steady state is called set point.
* For oven, it is qR.
* ![](/assets/images/2021-09-19-14-53-10.png)
* ![](/assets/images/2021-09-19-14-53-30.png)
* Left hand side part is the steady state voltage and as evident from the figure it has some error.
* However, if Kp is chosen to be very large as compared to 1, this error is highly reduced.
* The coefficient of $\frac{dVo}{dt}$ is time constant and here in our case it is $\frac{RC}{Kp + 1}$.
* Thus, on increasing Kp, time constant is reduced and a faster response is obtained.

## Loading effect in Open Loop System
* ![](/assets/images/2021-09-19-14-57-54.png)
* **Note that the steady state voltage is reduced by half and this is a significant drop.**

## Loaded system with feedback
* ![](/assets/images/2021-09-19-14-58-56.png)
* Slight difference is there in the denominator.

## LTspice simulation
* ![](/assets/images/2021-09-19-15-01-58.png)
* Watch [video](https://drive.google.com/file/d/1-aeTFcX9shA_R6Owlvv1iaxCVnFcwAAQ/view) for better understanding (1:11:00)
