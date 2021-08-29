---
id: Oj3uiXKth6ZgUASqln4Vi
title: Lecture 3
desc: ''
updated: 1630213402259
created: 1630211824085
---

# System Calls

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
