---
id: IAitwZmx61XZ9UP1erPM2
title: Lecture 8
desc: ''
updated: 1632913252461
created: 1632896897487
---
## Strain Sensitivity and Force Sensor

## Sensitivity and Bridge Circuit

- ![](/assets/images/2021-09-29-15-47-15.png)
- In a bridge circuit, the larger the value of drop for the same strain, the larger would be the sensitivity.
- To acheive this we use two strain gauges, one for changing the value of R4 and other to change the value of R3.
- Note that on increasing the value of R4, the potential was dropping. To acheive the same, we need to attach the strain guage in such a fashion that the value of R3 decreases.
- Only if R3 decreases will the drop increase.
- Now to further increase the sensitivity, we use strain guage in place of R1 and R2 also.
- The manner of attaching the strain guage gets reversed because we want to decrease the value of R1 to increase the value of potential drop.
- Types of bridges
  - Quater - Only one strain guage is used.
  - Half - Two strain guages are used.
  - Full - Four starain guages are used.
- Note that we should use the same/identical strain guages for (R4, R3) pair and (R1, R2) because the strain resistance is a function of temperature also and we want the conditions to be almost similar for both the strain guages.
- This is also the reason as to why three strain guages are not used in a bridge. (This is because we want to acheive temperature independence).
- It is obvious that full bridge is the best in terms of sensitivity but it is costlier than others.

## Quater Bridge Configuration

- ![](/assets/images/2021-09-29-16-30-21.png)

## Half Bridge Configuration

- ![](/assets/images/2021-09-29-16-32-36.png)

## Full Bridge Configuration

- Bending Strain
  - ![](/assets/images/2021-09-29-16-34-20.png)
- Axial Strain
  - ![](/assets/images/2021-09-29-16-35-18.png)

## Force Sensing Resistance

- Conducting foam is pressed and the contact resitance will decrease.
- This is the method by which we define a relationship with force and resistance.
- Types
  - Shunt Mode Force Sensitive Resistor
    - Foam is only on one side.
  - Thru Mode force sensitve resistor
    - Froam is on both the sides.

## Force vs Voltage

- We are benefitted if the change in resistance is somehow reflected by the change in voltage.
- To achieve this, we use the below given circuit.
- ![](/assets/images/2021-09-29-16-45-49.png)
- Make sure to select R1 as 1k unless specified otherwise.

## Force Alarm

- ![](/assets/images/2021-09-29-16-47-54.png)
- Vref depends on problem and hence it is not fix that the value of Vref must be 4V.

