---
id: 0MwJpw5Ai8WlLrE5bLyaQ
title: Lecture 4
desc: ''
updated: 1631896303807
created: 1630240499817
---

# Directions and Planes

## Density Computation
* $\rho$ = $\frac{nA}{VcNa}$
* Here $\rho$ is the density, n is the number of atoms in a unit cell, A is the atomic mass of the element, Vc is the volume of unit cell and Na is the avogadro's number.

## Crystal Directions
> These include linear density and planar density

* ![](/assets/images/2021-08-29-18-16-42.png)

> Always divide by the biggest number. Eg. 4th case in the above image.

## Extra points
* To represent direction, use square brackets.
* To represent plane, use round brackets.
* Parallel planes belong to the same **family** of planes.
* To represent family of planes, use curly brackets.
* To represent family of directions, use angular brackets.
* There should not be comma between numbers in either of the cases.
* Negative coordinates are also possible and are represented by a bar over the number.
* For hcp, the coordinate system is different and contains one more extra coordinate in the xy plane.
* We calculate it using the below formula.
    * ![](/assets/images/2021-09-17-21-44-05.png)


> Why are planes in a lattice important?
* Determining crystal structure
* Plastic deformation
* Transport properties

## Miller Indices
* This is one of the information required to study X-Ray defractogram
* Procedure to find these indices
    * Note the intercepts made by plane in terms of **lattice constants** a,b and c.
    * Note the coefficient of the intercepts.
    * Find inverse of them.
    * Find LCM and multiply them by LCM.
    * These points that you get are the Miller indices.

> Example of calculating Miller indices

![](/assets/images/2021-08-29-18-27-28.png)

## How to draw planes?
* First get the miller indices.
* **Be careful about what is given, if intercepts are given the  calculate miller indices otherwise directly use miller indices provided.**
* Simply select an origin and the plane must pass through the miller indices.
* Make sure to treat miller indices as simple coordinates.

## Angle between planes
![](/assets/images/2021-08-29-18-43-28.png)

## Linear and Planar Density
![](/assets/images/2021-08-29-18-45-11.png)

* This is **atomic** density.
* FCC Structure
    * Case 1 (100)
        * Linear Density = $\frac{number of atoms}{length of the vector}$ = $\frac{1}{a}$
        * Planar Density = $\frac{number of atoms}{area of the plane}$ = $\frac{2}{a^2}$
    * Case 2 (110)
        * Linear Density = $\frac{2}{\sqrt{2}a}$
        * Planar Desity = $\frac{2}{\sqrt{2}a^2}$
    * Case 3 (111)
        * Linear Density = $\frac{1}{\sqrt{3}a}$

## Points to Ponder
* For the area for calculation of planar density, follow these steps
    * Imagine the plane and the crystal lattice.
    * Use [this site](http://calistry.org/calculate/latticePlanesMillerIndices) for better visualization.
    * The corner atoms will contribute 1/4 to the area, the face atoms will contribute 1/2 to the area and the body centered atoms will contribute 1 to the area.