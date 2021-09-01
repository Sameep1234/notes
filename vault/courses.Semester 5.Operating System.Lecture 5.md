---
id: WRmiZB2hMRgBOBAUqcUGI
title: Lecture 5
desc: ''
updated: 1630467589276
created: 1630463553632
---

## Suspended Process
* It is possible that at one point all the processes are waiting for I/O and processor will remain idle.
* Issues to address
    * Processor could be idle most of the time.
* Solution
    * **Swap these processes to disk to free RAM and execute some new processes**.
* Blocked state, thus, becomes suspend state when swapped to disk.
* Now 5-state gets converted to 6-state model

## 6-state model
* ![](/assets/images/2021-09-01-08-08-39.png)
* Notice that blocked processes are transferred to suspended processes but suspened processes are directly transfered to ready state.
* OS now has two ways
    * Admit new processes
    * Activate previously suspended processes
* Subsets of suspend state
    * Blocked/Suspend: Process in secondary memory and awaiting an event.
    * Ready/Suspend: 

## 7-state model
* ![](/assets/images/2021-09-01-08-13-46.png)
* Newly created process will remain in ready/suspend state until there is memory avaible to move it to ready state.
* Eg. When booting up, memory is awailable and hence it is possible to directly admit new process into ready state.
* New state transitions
    * ![](/assets/images/2021-09-01-08-22-08.png)

## Characterisitcs of suspended processes
* Process not immediately available for execution because it is in secondary memory.
* It may or may not be waiting for an event. It may be moved only to free some RAM.
* "Agent" puts the process in suspended state. Agents include either itself (Eg. Some process which occur only periodically), parent procees or OS in order to preclude its execution.
* Process may not be removed until agent orders the removal. Most of the time agent is OS.

## Reason for process suspension
* ![](/assets/images/2021-09-01-08-32-36.png)

## Relation between process and resource
> Recap: OS is a resource manager. Process is a program in execution.

![](/assets/images/2021-09-01-08-38-45.png)
* **Main memory as a resource means**
* Virtual memory is extention of secondary memory into main memory.
* Some part of HDD is considered in RAM.

## Data Structures
* OS must have information about current status and all processes and all resources.
* Thus, OS maintains tables for each of the functionalities it offers
* Memory Table
    * Keep tracks of main and secondary memory.
    * Must include information
        * Allocation of main memory to processes.
        * Allocation of secondary memory to processes.
        * Protection attributes for access to shared memory regions.
        * Information required to manage virtual memory.
* I/O Table
    * Manage I/O device and channels of computer.
    * Must include information
        * Availability of I/O device.
        * Status of I/O operation whether I/O device is available or not.
        * Location in main memory for source and destination
* File Table
    * Must include information
        * Existence of files.
        * Location on secondary memory.
        * Current Status.
        * Others (Who can access? etc.)
* Process Table
    * Must include information
        * Location of **process** in the memory.
        * Process attributes.
    * Memory, I/O and files are managed on behalf of processes, so there has to be some reference to these resources in process tables. (Like foreign key)

## Physical manifestation of a process
> Menifestation means presentation.

![](/assets/images/2021-09-01-08-53-11.png)

* Elements of process image
    * User Data
    * User Program
    * User Stack
    * Process Control Block (PCB)

## Process Location
* It is not required in main memory. Someting called virtual memory also exists.
* Process image is maintained as a contiguous block of memory (**in secondary memory**).
* Maintained in secondary memory (majority of its part).
* Some part should be loaded in main or at least in virtual memory.
* Moreover, to execute process, some part must be in main memory.
* Thus, only needs to know which parts of process are in main and secondary memory and where are they located.

## Attributes in PCB
* Process identification
* Processor state information
* Process control information

## Process Identification
* Identifier of this process.
* Identifier of parent process.
* User identifier (To which user this process belongs to?)

## Processor state information
* Need to watch lecture again from here. 