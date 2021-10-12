---
id: XV4krgl1Xqw99yjO9sLyX
title: Lecture 11
desc: ''
updated: 1634037272109
created: 1634037178840
---

# Threads

## Introduction
* ![](/assets/images/2021-10-12-16-45-08.png)
* The unit of dispatching is referred to as a thread or lightweight process.
* Thus, to define thread, we can say that it is an independent path of execution of instruction.
* The unit of resource ownership is referred to as a process or task.

## Multithreading
* ![](/assets/images/2021-10-12-16-47-59.png)
* Threads, in  greneral, run the same set of instructions. 
* However, it might be the case where the interaction with client make some more instructions to execute or some instructions to get skipped.
* Eg. Server pool of threads for each client, Word program checking spelling and displaying output at the same time.

## Single Thread approach and Multi thread approach
* ![](/assets/images/2021-10-12-16-52-16.png)
* ![](/assets/images/2021-10-12-16-53-25.png)

## Relationship between process and multithreading
* ![](/assets/images/2021-10-12-16-55-14.png)

## Multithreaded environment
* When we have one or more threads in process, each thread has the following
    * ![](/assets/images/2021-10-12-16-57-25.png)
* Theoritical Definition: Thread is an **independent** program counter operating **within** a process.

## Thread vs Process
* ![](/assets/images/2021-10-12-17-00-26.png)
* Recap: User address space contains the program and the data.
* Thus, we can see that the user address space is shared with multiple threads within the same process.

## Benefits of threads
* ![](/assets/images/2021-10-12-17-04-46.png)

## Case study - File Server Application
* ![](/assets/images/2021-10-12-17-06-59.png)

## Single User System
* In file server, we can have multiple client requests and multiple threads, but in single user system, it is not the case.
* Foreground/Background processes can be handled using threads individually.
* Asynchronous Processing - Eg. Backing up in background.
* Faster Execution - Read one set of data while processing another set.
* Organization - Eg. For a word processing program, may allow one thread for each file being edited.

## Management of thread at process level and similarities with processes
* ![](/assets/images/2021-10-12-17-11-53.png)
* ![](/assets/images/2021-10-12-17-12-55.png)

## Thread states and its operations
* ![](/assets/images/2021-10-12-17-13-25.png)
* ![](/assets/images/2021-10-12-17-14-36.png)

## Remote Procedure Call
* It means that from one program, we are calling a procedure of another program in the remote machine.
* Distributed computing concept starts with RPCs.
* ![](/assets/images/2021-10-12-17-16-34.png)
* Single Thread Model
    * ![](/assets/images/2021-10-12-17-16-55.png)
* Multi Thread Model
    * ![](/assets/images/2021-10-12-17-17-52.png)

## Uniprocessor Multithreading
* ![](/assets/images/2021-10-12-17-19-06.png)

## Thread Synchronization
* ![](/assets/images/2021-10-12-17-20-26.png)
* ![](/assets/images/2021-10-12-17-23-12.png)

## Categories of Thread Implementation
* 