---
id: 8b9mhqeVaeU3RwyIdctOQ
title: Lecture 5
desc: ''
updated: 1631936415801
created: 1631075486165
---

## X-ray Diffraction (XRD)

> Diffraction occurs when a eave encounters a series of regularly shaped obstacles that are capable of scattering the wave and have spacings that are comparable in magnitude to the wavelength.

## Key Points

- [Site](http://calistry.org/calculate/latticePlanesMillerIndices) to view miller indices and planes easily.
- When two waves are in sync with the phase of each other, it is called constructive interference and vice versa.
- In case of constructive interference, the amplitude of the final wave will be added and vice versa.
- X-Rays are a form of electromagnetic radiation that have high energies and short wavelengths of the order of the atomic spacings for solids.
- ![](/assets/images/2021-09-08-14-54-08.png)
- Here d = interplanar spacing and will remain the same for a particular material.
- We would be using copper k-alpha. Advatage is immediate cooling of the metal.
- Copper k-beta gives very low intensity and hence is avoided for XRD study.
- Wavelength of XRD = 1.54 angstrom (fixed for all calculation).
- **For diffraction to occur, 2dsin($\\theta$) = n$\\lambda$ must be satisfied where n = order of reflexion.**
- **Always take n=1 unless specified. n = 1 implies first order diffraction.**

> Key Question: How to decide which element to take (like Copper, Molebdenum or Cobalt)?
>
> - So in such cases, first we check the intentsity and then the d-spacing as it remains the same for the same material.

## X-Ray Diffractogram Image

- ![](/assets/images/2021-09-18-09-10-15.png)

## Bragg's law

- ![](/assets/images/2021-09-08-14-47-40.png)
- It is the relationship among x-ray wavelength, interatomic spacing and angle of diffraction for **contructive interference.**
- **Note that if the bragg's law is not satisfied then the destructive interference will occur and a very low-intensity diffracted beam will be produced.**

## X-Ray Diffractogram

> Curve between intensity and diffraction angle (2$\\theta$).

## How to identify which crystal structure? (SC, BCC or FCC)

- For that we have to calculate $h^2$ + $k^2$ + $l^2$ where h,k and l are the miller indices.
- Then use the below image.
  - ![](/assets/images/2021-09-08-16-03-14.png)
  - For SC, always calculate till 8th step and **show that 7 is absent/missing.**
  - If 7 comes in the series then multiply the whole series with 2 to get BCC structure.
  - ![](/assets/images/2021-09-08-16-50-04.png)

## How to identify material based on lattice parameter?

- First thing to **remember** is that angle is **2$\\theta$** with **intensity.**
- Then use the below image to follow the steps.
  - ![](/assets/images/2021-09-09-07-53-22.png)
  - **Note: 2$\\theta$ values may differ based on XRD**
  - Now, if any of the first 3 columns comes whole integer, then we get our $h^2$ + $k^2$ + $l^2$.
  - Otherwise, we go on multiplying with 4, then with 5 and so on untill we get a whole integer and that becomes the value of $h^2$ + $k^2$ + $l^2$.
  - To calculate a, find average of the **peaks**.

