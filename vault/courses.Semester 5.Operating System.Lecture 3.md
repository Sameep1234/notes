---
id: Oj3uiXKth6ZgUASqln4Vi
title: Lecture 3
desc: ''
updated: 1630215776285
created: 1630211824085
---

# System Calls and Architecture of UNIX

## Intro to system calls
* System calls is the most important and crucial concept in OS. It is basically a link connecting user to the OS.
* Formally, it is aprogramming interface to use the services provided by the OS. They are the programs that help give access to the functionalities provided by the OS.
*  They are written in a high-level language like C or C++.
* POSIX API is used in Linux and Win32 API is used in windows.

## Implementation of System Call
* Associated with each system call.
* Every OS have a list of system call along with ID's.
* System call interface maintains a table with ID's as indices.
* This interface invokes a particular system call in OS kernel and returns the status and return values if any.
* Details are hidden from programmer by API.

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

* Linux is based on UNIX but is more complicated than UNIX.
* UNIX system follows monolithic approach
* UNIX System Kernel

![](/assets/images/2021-08-29-11-10-53.png)

* **In Linux or UNIX, everything is in terms of files. Thus, it becomes crucial to understand file system.**