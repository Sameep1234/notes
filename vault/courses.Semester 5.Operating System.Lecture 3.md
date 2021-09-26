---
id: 6IOrGgBzjNQfDz1zCdaUA
title: Lecture 3
desc: ''
updated: 1630430971753
created: 1630211824085
---


# System Calls and Architecture of UNIX

## Intro to system calls
* System calls are the most important and crucial concept in OS. It is basically a link connecting user to the OS.
* Formally, it is a **programming interface (like waiter connecting customers to kitchen in a restaurant)** to use the services provided by the OS. They are the programs that help give access to the functionalities provided by the OS.
*  They are written in a high-level language like C or C++.
* POSIX API is used for Linux and Win32 API is used for windows.

## Implementation of System Call
* Associated with each function call. Eg. If you call a function printf() in C, then it internally calls an associated system call telling the OS to display the written part on the scree.
* Every OS have a list of system call along with ID's.
* System call interface maintains a table with ID's as indices.
* This interface invokes a particular system call in OS kernel and returns the status and return-values if any.
* Details are hidden from programmer by the API.

## Relationship between API, System Call and OS

![](/assets/images/2021-08-29-10-48-06.png)

## Types of system calls
* File Management - Eg. create, open, close etc.
* Device Management - request, release, read, write etc.
* Protection - control access, get and set permissions etc.
* Information maintenance - get time, set process etc.
* Communications - create, delete communication, send or recieve messages etc.

### Architecture of UNIX

* ![](/assets/images/2021-08-29-11-08-15.png)

* UNIX is an OS just like Linux.
* In fact linux is based on UNIX but is more complicated than UNIX.
* UNIX system follows monolithic approach
* UNIX System Kernel

![](/assets/images/2021-08-29-11-10-53.png)

* **In Linux or UNIX, everything is in terms of files. Thus, it becomes crucial to understand file system.**
