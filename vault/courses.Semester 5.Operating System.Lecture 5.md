---
id: BjGodSmGeG11e3UACx3wt
title: Lecture 5
desc: ''
updated: 1631162424572
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
> Processor state is always **stored in register.**

* User Visible registers
    * Most of the times they are the address registers and data registers
    * It means that these registes can be directly visible by programs running in user-mode.
    * Generally they are 8-32 regsiters but some RISC implementations may have over 100.
* Control and status registers
    * Program counter - Contains address of the next instruction.
    * Condition codes - Result of the most recent ALU operation.
    * Status information - Contains inturrept flags and execution mode (They are also known as program/process status mode).
* Stack Pointers (Registers)
    * Process image uses stack to maintain parameters and calling addresses for procedures and system calls.
    * There could be multiple stacks and each stack has a stack pointer pointing to the top of the stack.

## Process control information
> Manages additional information that is needed by the OS to control and coordinate the various active processes.

* These include the following
    * ![](/assets/images/2021-09-09-10-01-56.png)
    * IPC stands for Inter-process communication
    * Process privileges includes "What area can be accessed by the process" or "Which mode?" etc.
* Scheduling and State information
    * ![](/assets/images/2021-09-09-10-03-54.png)
* Data Structuring
    * ![](/assets/images/2021-09-09-10-04-13.png)
    * For each state (blocked, ready etc.) there would be one queue and generally they are made using linked list.
* IPC
    * ![](/assets/images/2021-09-09-10-05-14.png)
    * It occurs when two process talk to each other
* Process privileges
    * ![](/assets/images/2021-09-09-10-05-56.png)
    * What kind of file, area of memory etc.
* Memory Management
    * ![](/assets/images/2021-09-09-10-06-58.png)
* Resource Ownership and Utilization
    * ![](/assets/images/2021-09-09-10-06-39.png)

> ## What does Process image contain?
* ![](/assets/images/2021-09-09-10-08-11.png)

## Role of PCB
* It is the most important DS.
* It contains most of the information regarding a process excpet stack pointers.
* It manages the processes.
* Thus, it requires protection.
    * If not done then,
        * It may damage the block and destroy OS's ability to manage the processes.
        * Any change in design will affect many other modules of OS.
