


## Feedback control
* Here we are considering the example of an engine of the car.
* ![](/assets/images/2021-09-03-09-49-46.png)
* Motor is used for getting a particular position and not a particular speed.
* Particular position will ensure that the desired speed is achieved.

## Pulse Width modulation
* Width of the pulse determines the average voltage. Higher the width of the pulse, higher the voltage and vice versa.
* Control of the DC Voltage would not be very efficient if you use a potentiometer and this is because the potentiometer will decipate a lot of power.
* Thus, we use pulse width modulation because changing the pulse of a wave does not require much power and can be easily done.
* ![](/assets/images/2021-09-19-15-25-30.png)

## Important relationships
* Note that this is for throttle vavle and potentiometer outpur for a car.
* However, the pedal angle does not go from 0 to 90 degrees. It goes from 0 to 45 degrees and hence to make the throttle valve equal to the pedal valve, we use amplifier or simply use a double Vcc for pedal potentiometer.
* ![](/assets/images/2021-09-03-09-55-04.png)

## H bridge
* ![](/assets/images/2021-09-19-15-43-30.png)
* We have achieved to reverse the direction of rotation of motor without reversing the polarity using H bridge.
* **Note that the switches shown are mechanical but in real life, they are electrical.**
* Electrical H Bridge IC
    * ![](/assets/images/2021-09-19-15-45-17.png)

## Extra Points
* 90 degrees means full open valve and **don not confuse it with 360 degrees**
