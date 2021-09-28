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
* Selection Function
    * ![](/assets/images/2021-09-20-08-10-10.png)
* Normalized TAT is better quantity to compare two scheduling algorithms.
* Normalized TAT is relative delay and it represents how much a process needs to wait.
* We can't have normalized TAT less than 1 because service time can never be more than TAT.

## Decision Mode
* Specifies the instants in time at which the slection functions is exercised.
* Two Types
    * Nonpreemptive - Once a process is in running state, it will continue until it terminates or blocks itself for I/O.
        * This means it can't be forcefully stopped.
    * Preemptive - Currently running process may be interrupted and moves to ready state by the OS.
        * This normally occurs when new process arrives, on an interrupt or periodically.
        * In simple terms, this will occur when a new process is inserted or an interrupt is passed or periodically this premption is performed.
* Normally preemptive mode is preferred even though it increases overhead because of more frequent process switching but it also prevents one process from monopolizing the processor.
* For example, a process requires a user input and if user is on a break, the process will block all other processes which otherwise would have ran. This is called monopolizing the processor.

## CPU Bound and I/O Bound
* If a process spends most of its time in processor, then it is called CPU bound and vice versa.
* Example of I/O bound process includes chatting. It uses I/O for most of the time because it is waiting for the user to enter the values.

## FCFS
* ![](/assets/images/2021-09-20-08-14-00.png)
* It is one of the most fair strategy in the **real world.**
* w = waiting time.
* For better efficiency TAT should be as low as possible.
* Example
    * ![](/assets/images/2021-09-28-10-54-38.png)
* Issues
    * A short process may have to wait a very long time before it can execute.
    * ![](/assets/images/2021-09-20-08-33-39.png)


## Extra Points
* DMA - Data memory access (DMA) is a hardware circuit through which all the data is transfered after an I/O is available.
