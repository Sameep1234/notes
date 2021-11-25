---
id: Y15Z6FWUqPX81EPSFIrUX
title: Lecture 9
desc: ''
updated: 1632825583219
created: 1632821953611
---


## Scheduling Algorithms (Cont.)

## Comparision (FCFS, RR, SPN)

- ![](/assets/images/2021-09-28-15-14-20.png)
- Note that for **round robin**, there is a **constant selection** function because whatever process is there, you run it and block it if the time exceeds time quantum.
- Throughput means number of processes completed in a given time frame.
- Response time means the time when the process is first admitted into the system and it gets first chance to execute.
- **Note that the overhead in round robin is high if the time quantum is too low because of more frequent switching. Thus, we need to swap the overhead of RR with that of SPN int he above image.**

## Shortest Remaining Time (SRT)

- ![](/assets/images/2021-09-28-15-22-39.png)
- The process with the minimum service time will be given the chance.
- **But note that if a process requires service time of 5 units and comes to ready state for I/O operations and has already worked for 3 units of time, then the remaining time i.e 2 units is considered and not the original service time of 5 units.**
- Example
  - ![](/assets/images/2021-09-28-15-28-55.png)
  - Note that both B and D have the same amount of remaining time left and hence any tie breaker can be used and the simplest one that is used here is the FCFS.
  - ![](/assets/images/2021-09-28-15-29-57.png)
  - Compared to SPN, Mean TAT and mean NTAT is less and hence is better than SPN.

## Highest Response Ratio Next (HRRN)

- ![](/assets/images/2021-09-28-15-31-07.png)
- As the name suggest, when current process completes or is blocked, choose next process with the greatest ratio.
- Effect on processes
  - ![](/assets/images/2021-09-28-15-34-20.png)
- It is thus going to balance out each process because of obvious reasons.
- Example
  - ![](/assets/images/2021-09-28-15-38-03.png)
  - ![](/assets/images/2021-09-28-15-38-13.png)
  - Note that when T = 9 "D" had higher ratio than "E" but at T = 13, "E" has the higher raio than "D". Thus, we should always calculate the ratios at each time interval.
  - Also note that mean times in this algorithm is greater than that of SRT and SPN but is somewhere in between and it is lower than that of FCFS.

## Comparision (SPN, SRT and HRRN)

- ![](/assets/images/2021-09-28-15-40-07.png)

## Feedback Scheduling (FB)

- ![](/assets/images/2021-09-28-15-43-17.png)
- ![](/assets/images/2021-09-28-15-49-15.png)
- Here we have multiple ready queues.
- So if a process in the first queue is not completed in the given time quantum, it is appended in the second queue.
- The priority of the second queue is lower than that of the first queue and so on.
- Thus, longer processes are **penalized.**
- **Note that withing each queue, there is FCFD algo being executed except the last queue where RR is being executed.**
- ![](/assets/images/2021-09-28-15-53-31.png)
- Example
  - ![](/assets/images/2021-09-28-15-55-42.png)
  - ![](/assets/images/2021-09-28-15-59-07.png)
  - ![](/assets/images/2021-09-28-15-59-26.png)
  - ![](/assets/images/2021-09-28-16-00-12.png)
- Issues and its solution
  - ![](/assets/images/2021-09-28-16-01-01.png)
  - ![](/assets/images/2021-09-28-16-03-15.png)
  - This means that if a process has spent some amount of time, it should not move to a lower priority queue, it should actually be moved to a higher priority queue.
  - This can reduce the waiting time significantly.
- Note that FB is also called as multi-level feedback strategy because it has multiple levels of queue.

## Other Scheduling Algorithms

- ![](/assets/images/2021-09-28-16-05-48.png)
- Priority scheduling means that based on some criteria you provide some priority.
  - In nonpreemptive version, whichever process is running will continue to run unless it is finished or blocked and then the next process will be selected based on the priority.
  - In preemptive version, the currently running process will be interrupted by a higher priority process in the queue.
- Longest Job First is the direct opposite of SPN.
- Longest Remaining time is the direct opposite of SRT.

> In real operating system, some hybrid versions are used.

