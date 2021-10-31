---
id: javcf3PHyxIZemUP0ry6l
title: Lecture 7
desc: ''
updated: 1631260876454
created: 1631247844382
---
## Process/Processor Scheduling

> Note that we have assumed uniprocessor system and hence we will be studying uniprocessor scheduling

## Sceduling

- OS handles resources and hence called as resource manager.

- Processor provides resources in terms of its execution time.
  > Aim: Assign processes to be executed by processor over time, in a way that meets system objectives.

- Response time means the time elapsed between process creation and the **first response** from that process.

- Throughput means rate of job completion. This means how many processes can be completed in one unit time is called throughput.

- Processor efficiency means that processor should not be idle and hence should be used to its fullest.

- Objectives
  - ![](/assets/images/2021-09-10-10-00-58.png)
  - Starvation of a process means deprived of processor time.
  - Example of overhead is process switching.

- Types
  - ![](/assets/images/2021-09-10-10-03-11.png)
  - Short-term sheduling is also known as dispatcher.
  - ![](/assets/images/2021-09-10-10-04-24.png)

## State transition diagram

- ![](/assets/images/2021-09-10-10-05-29.png)
- We can put a newly created process directly into ready state if there is enough memory and if there is not enough memory, we put it in ready/suspended state.
- This task is done by long-term scheduling and the rest is self-explanatory.
- **Swapping** happens when the process is **swapped** from {ready and ready/suspend} and {block and blocked/suspend}.
- Same thing in a different way
  - ![](/assets/images/2021-09-10-10-13-06.png)

## Long-Term Scheduling

- ![](/assets/images/2021-09-10-10-13-29.png)
- Some questions
  - Will it be possible to predict the I/O requirements?
    - In case of interactive jobs, it is not possible, but for **batch jobs**, it is possible.
  - Similar for expected execution time

## Medium-Term Scheduling

- ![](/assets/images/2021-09-10-10-17-23.png)

## Short-Term Scheduling

- ![](/assets/images/2021-09-10-10-17-45.png)
- Whenever there is a need for **process switch**, dispatcher comes into the picture.
- Process needs to switch when process is terminated, interrupt occurs, I/O operations etc.
- Criterias of classification of short-term scheduling
  - User-oriented
    - Response time
    - This means to give response as fast as possible from user perspective.
  - System-oriented
    - Effective and efficient utilization of the processor.
    - Designers must keep in mind while deciding the dispatcher strategy, the processor should not be underutilized.
  - Performance related
    - Quantitative and easily measure.
    - Eg. Response time and throughput.
  - Non-performance related
    - Qualitative and hard to measure.
    - Eg. User-Satisfaction
- Interdependency in criterias
  - User oriented and performance related.
    - ![](/assets/images/2021-09-10-10-29-24.png)
    - Turnaround time is approriate for batch jobs and not for interactive jobs because in interative jobs, user interaction plays a key role. 
    - For example, a process is waiting for a user input and the user has gone to take a break, then it will remain stagnant and hence turnaround time will increase drastically.
    - The deadlines are in real-time systems or embedded systems.
  - User oriented and non-performance related
    - ![](/assets/images/2021-09-10-10-39-44.png)
  - System-oriented and performance related
    - ![](/assets/images/2021-09-10-10-40-58.png)
  - System-oriented and non-performance related
    - ![](/assets/images/2021-09-10-10-43-31.png)
    - In the third criteria, we require medium-term and long-term scheduling because memory is one of the resource that is used by the process and processor.

## Priority based scheduling

- ![](/assets/images/2021-09-10-10-45-56.png)
- Each ready queue has different priority, but processes inside the **same ready queue, have the same priority.**

> Now this may lead to starvation problem. Suppose, there are 3 ready queues and at any particular instance of time, there is at least one process in the first two ready queues. This means that the processes in the third queue will not be allocated any time. This is the starvation problem. 

> To solve this, we allow a process to change its priority-based on its age or execution history. This means that whenever some process has been executed for some time and is to be again inserted in the ready queues, its priority should be lowered down.

## Various Scheduling Policies

- ![](/assets/images/2021-09-10-10-55-01.png)
- Out of all these, round robin and feedback are the most practical theories.
- Others are good in theory, but not in practice.

## Selection Function

- ![](/assets/images/2021-09-10-10-56-15.png)

## Decision Mode

- Specifies the instance in time at which the selection function is executed.
- Two categories
  - ![](/assets/images/2021-09-10-11-00-20.png)
  - For non-preemptive, the OS will never put a process in blocked/removed state unless it is fully terminated or blocked because of I/O.
  - Round robin is a strategy where every process is assigned some amount of time and even if process is still able to run, it is not blocked, it is put back directly into Ready state and the next process is dispactched to running state.

> Which mode should be preffered?
>
> - Preemptive as it prevents one process from **monopolizing** the processor.
> - This means that a very big process will not block others till it iterminates.
> - Even though there would be some overhead of frequent switching of the process, but its advantage outweighs its disadvantage.

## Process States for Linux

- ![](/assets/images/2021-09-10-13-24-18.png)
- Commands related to processes in ubuntu
  - lscpu = Gives information regarding the processor in your system.
  - ps -aux = Gives information about the processes that are currently there in the system.
  - Note: ps itself is the command but it won't provide much information as ps -aux.
- System calls
  - fork() = Create a new process
  - exec() = Execute other programs in current process
  - wait() = Wait for child process to terminate
  - exit() = Terminate the execution

