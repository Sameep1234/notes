---
id: iulDI2JKiPfwvpMA31XAa
title: Lecture 6
desc: ''
updated: 1630898377574
created: 1630895369961
---

# Process Control and Process Management

> Process management will be studied in UNIX SVR4 file system.

## Functions of OS kernel
* ![](/assets/images/2021-09-06-08-10-29.png)
* ![](/assets/images/2021-09-06-08-13-17.png)
* ![](/assets/images/2021-09-06-08-13-59.png)

## Process Creation
* Once new process is decided to be created, OS performs following tasks
    * Assigning unique ID.
    * Allocating space in memory.
    * Initializing PCB (The most important part of a process).
    * Setting up of appropriate links.
    * Creating or expanding other data structures.

## Process Switching
* For small amount of time, some process will run and then other will run. This time is very small and hence we see it like all the processes are running parallely.
* Thus, when one process goes away and other process needs to be loaded, this is called process switching.
* Process switching is totally different than mode switching. In a process execution, there may occur mode switching. 
* Mode switching means switching from user to kernal mode vice versa.

> So why is process gets switched?
* ![](/assets/images/2021-09-06-08-23-14.png)

* Reasons for switching (Eg.)
    * Clock interrupt (time slice expired)
    * I/O Interrupt (an event occured)
    * Memory fault (trap) - Accessing memory which is not available.

* Mode Switching - When a running process changes its mode from one to other.
    * While switching the mode, processor state information of PCB is saved (user to kernel) and restored back (kernel to user).
    * Mode switch, thus becomes the subset of prcess switch.
    * Thus, process switch will take more time then mode switch.
* Steps in process switch
    * ![](/assets/images/2021-09-06-08-28-44.png)

> Is OS a process?
* Basically OS is a code/program which is in between hardware and application that we run.
* Designs of OS to explain execution of OS
    * ![](/assets/images/2021-09-06-08-33-06.png)

## Different designs
* Non-process Kernel
* Execution within User Processes
    * ![](/assets/images/2021-09-06-08-36-42.png)
* Process-based OS
    * ![](/assets/images/2021-09-06-08-37-48.png)
    * More like microkernel architecture.

## Process management in UNIX SVR4
* SVR4 stands for System V Release 4.
* **Most** of the the OS executes in user process.
* System processes - Kernel mode only
* User Processes
    * User mode to execute user programs and utilities.
    * Kernel mode to execture instructions that belong to kernel
* Process with ID 1 = Linux boots and creates a swapper process which in turn creates init process with ID = 1.
* This init process creates all the process required to run Linux on boot up.
* init process works only in kernel mode.
* Some other process that execute only in kernel mode include dispatcher etc.
* States
    * Two extra states
    * ![](/assets/images/2021-09-06-08-47-29.png)
    * Blocking state is called sleep state.
    * 