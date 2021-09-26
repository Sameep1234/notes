---
id: pgUnaIZNOzcnS8OQ602Bx
title: Lecture 8
desc: ''
updated: 1632105946469
created: 1631672853178
---

# Uniprocessor Scheduling Algorithms

* We would be discussing only short-term scheduling.
* They mainly include dispatching techniques.
* Algorithms available
    * ![](/assets/images/2021-09-20-08-08-03.png)
* ![](/assets/images/2021-09-20-08-10-10.png)
* Normalized TAT is better quantity.

## CPU Bound and I/O Bound
* If a process spends most of its time in processor, then it is called CPU bound and vice versa is I/O bound.

## FCFS
* ![](/assets/images/2021-09-20-08-14-00.png)
* It is one of the most fair strategy in the **real world.**
* w = waiting time.
* For better efficiency TAT should be as low as possible.
* Normalized TAT is relative delay and it represents how much a process needs to wait.
* We can't have normalized TAT less than 1 because service time can never be more than TAT.
* Issues
    * A short process may have to wait a very long time before it can execute.
    * ![](/assets/images/2021-09-20-08-33-39.png)
    * 

## Extra Points
* DMA - Data memory access is a hardware circuit through which all the data is transfered after an I/O is available.
