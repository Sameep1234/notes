---
id: mzJZRHgKtfV2f6W4Q3wbz
title: Lecture 7
desc: ''
updated: 1631854754508
created: 1631851490710
---
## Stress and strain

## Hook's Law

- Amount of deformation is proportional to the force applies to any object.
- ![](/assets/images/2021-09-17-09-41-24.png)
- F = k\*(Change in length)
- **Note that the force should be small for the relationship to be linear.**
- If force greater than the threshold is applied than the relationship is not linear.
- Elstic region corresponds to the range of force where the object will retain its shape.

## Axial vs Transverse force

- This is called tensile force.
- ![](/assets/images/2021-09-17-09-45-18.png)
- Transverse strain means along the length of the object at perpendicular angle.

## Compressive Force

- ![](/assets/images/2021-09-17-09-48-42.png)
- $\\frac{F}{A}$ is called stress or pressure.
- Units of young's modulus is same as stress or pressure i.e N/m\*2 or Pascal (Pa).

## Strain Gauge

- Sensor for measuring strain
- ![](/assets/images/2021-09-17-10-07-40.png)
- ![](/assets/images/2021-09-17-10-10-23.png)
- Now to calculate change in resistance, we measure the change in current or change in voltage and indirectly find change in resistance.
- $\\frac{Change in R}{R}$ is very small and adding "1" might just lead to nothing.
- To avoid this, we need to set a circuit such that the voltage across the resistor is linearly proportional to $\\frac{Change in R}{R}$.
- We need a wheatstone bridge to get the linear proportionality.
  - ![](/assets/images/2021-09-17-10-16-43.png)
- **Understand the equation formed.**
- Bridge circuit for strain measurment
  - In the above figure, R4 is the strain gauge whereas others are normal resistors which are all equal.
  - In bending strain or a tensile strain, the formula still remains the same becuase in either of the cases, the length of the resistor in the strain gauge will change and hence, resitance will change.
  - ![](/assets/images/2021-09-17-10-22-11.png)
  - Final Equation
    - ![](/assets/images/2021-09-17-10-24-07.png)
  - **Note that the strain will always be positive.** According to the equation the negative value might change as change in voltage (Vo) might be negative if R4 gets too high.

