---
id: 8zzCqwP3wrOrk1Q9JsHx0
title: Lecture 5
desc: ''
updated: 1632042380325
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
    * 