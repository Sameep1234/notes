---
id: HaLC0S6nmXGxECDqZ0RXF
title: Lecture 10
desc: ''
updated: 1632849363575
created: 1632829724691
---

# Scheduling Algorithm (Cont.)

## Fair-share scheduling
* ![](/assets/images/2021-09-28-17-22-11.png)
* ![](/assets/images/2021-09-28-22-08-43.png)
* ![](/assets/images/2021-09-28-22-10-49.png)
* ![](/assets/images/2021-09-28-22-13-43.png)
* The algorithms discussed till now does not include who is the user that created the process, which groups are being used etc.
* This algorithm takes care of such things.
* Please note that fair share does not necessarily mean equal, but it can also mean that if weight assigned to a process is more, the work completed by it is expected to be more in the long run.
* Implementation
    * ![](/assets/images/2021-09-28-22-17-59.png)
    * ![](/assets/images/2021-09-28-22-23-39.png)
* Some calculation
    * ![](/assets/images/2021-09-28-22-25-10.png)
    * CPUj(i) means time utilized by a process j till "i" interval.
    * ![](/assets/images/2021-09-28-22-29-51.png)
    * The second point can be easily visualised with the help of formula.
* Example
    * ![](/assets/images/2021-09-28-22-37-44.png)
    * It is given in the question that the Process B and C combined are assigned 50% and Process A alone is assigned 50% weightage.

## Traditional (older) UNIX Scheduling
* ![](/assets/images/2021-09-28-22-39-46.png)
* Some calculations
    * ![](/assets/images/2021-09-28-22-42-57.png)
* ![](/assets/images/2021-09-28-22-43-23.png)
* The purpose of the nicej is to maintain that the priority of any particular process does not go too down with increasing value of CPUj(i) and remains between the **assigned band.**
* Types of band with **decreasing order of priority**
    * ![](/assets/images/2021-09-28-22-46-13.png)
    * From the above figure, we can conclude that the swapper band has the highest priority whereas the user processes have the lowest priority.
* Example
    * Note that in the below example, we are only considering **user processes.**
    * ![](/assets/images/2021-09-28-22-49-26.png)
    * **Note that the process which will be executing next will be that whose priority value is lowest which means highest priority.**
