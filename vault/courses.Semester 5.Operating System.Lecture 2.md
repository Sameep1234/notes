---
id: ZKzaoK7e6QRUgxr5sYaHB
title: Lecture 2
desc: ''
updated: 1630430485504
created: 1630169451366
---


# Evolution of OS and Kernel

## Evolution of OS
* Serial Processing
* Simple Batch Systems
* Multiprogrammed Batch Systems
* Time Sharing Systems
* many others

## Serial Processing
* There was no OS.
* To run the program, we would have to type a command for everything.
* A program at that time was called a job which is a set of instructions along with the data on which the instructions need to be executed.
* Issues
    * Scheduling
        * Fixed amount of time allocated to each instruction.
        * Conflict between instructions requiring more or less time.
    * Setup Time
        * Loading of compiler and program is time consuming

## Simple Batch System
* Monitor Program were used which were kind of OS - A very rudimentary OS.
* It is a software that controls the sequence of events.
* No direct access to users unlike Serial Processing.
* Job is submitted to an operator who batches similar instructions together and places them on the input device/hardware.
* In this way, the time consumed is averaged out and the processor can be utilized to its maximum.
* Control is given back to monitor after program gets terminated.

> Monitor is a special program that manages execution of each program in the **batch**. It controls the sequence of events. Resident monitor (another name for simple monitor) is software always in memory. It reads in job and gives control to the processor which in turn returns the control back to monitor

> Processor executes instructions from the memory i.e monitor which resides in the memory. It gains control from monitor to execute the task and once completed returns the control to monitor.

> JCL (Job control language) - It is a programming language that provides instruction to the monitor about the compiler and data to be used.

* Modes of operation
    * User mode (Analogy: Normal Mode) - Programs submitted by the user to the memory are executed in this mode. **Not all instructions may be executed.**
    * Kernal mode (Analogy: Admin Mode) - Part of a modern OS that actually performs I/O Management, Process Management etc. Nowadays, we have many other utility programs running which are a part of OS, but kernal is the most important one which manages the above mentioned things.

* Issues
    * Processor remains idle.
    * Slow compared to processor even with automatic job sequence.

![](/assets/images/2021-08-28-23-38-27.png)

## Uniprogramming

> Processor must wait for I/O instruction to complete before proceeding further.

## Multiprogramming

> Opposite of uniprogramming. Still there will be some waiting time but at least it can be reduced and hence is better than uniprogramming.

## Time sharing systems
* The program is being shared through different users and different monitors. Thus, can be used to handle multiple interactive jobs.
* Processor time is shared among multiple users.
* This time is in milli or micro seconds. This is called short burst or quantum of computation.

![](/assets/images/2021-08-29-00-06-36.png)

## OS Structure
* *For general purpose OS, the program is very large.*
* Ways to structure OS
    * Monolitic Approach (Analofy coding in C where there are no classes) - Everything combined in one place.
        * Eg. Older LINUX and UNIX
        * Advantages
            * Speed as everything is connected
            * Performance
        * Disadvantages
            * Difficult to maintain and modify
    * Layered Approach - OS divided into number of layers.
        * Layer 0 = hardware and Layer n = user interface layer
        * A particular layer can use functions and services of **lower-level layers only (layers below it).**
        * Eg. Older windows versions
    * Microkernels - Move as much functionalities as possible to user mode from kernel mode. 
        * Unlike that in layered and monolithic where majority of the functionalities is available in only kernal mode.
        * I\O and interrupt management, primitive memory management, inter-process communication and basic scheduling were kept in kernel mode.
        * All other functionalities will be running in user mode.
        * Advantages
            * Time is reduced significantly as the time to change the mode from user to kernel and vice versa is almost completely diminished.
            * Porting of OS to newer architecture becomes easier (will be covered in upcoming lectures).
            * More reliable because less code is running in kernel mode.
            * More secure as less code has to be valudated in kernel.
        * Disadvantages
            * Performance overhead to change the mode.
        * Eg. Mach, MINIX, Windows NT Client-Server
    * Modules - Most moedern OS implement kernel modules
        * These are loadable kernel module
        * Uses OOP
        * Similar to layers but is more flexible
        * Eg. Device Drivers (These are loaded as needed within the kernel)
        * Solaris Modular Approach (will be covered in upcoming lectures).
    * Hybrid Approach - Combines multiple approaches to address performance, security and usability.
        * Eg. Linux and Solaris = monolithich + modular, windows = monolithic + microkernel and Mac OS and IOS = Darwin which is microkernel and BSD Unix kernel implemented over layered model
