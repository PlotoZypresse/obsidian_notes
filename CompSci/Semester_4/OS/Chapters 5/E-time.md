![[Screenshot 2024-02-22 at 16.48.16.png]]
- The number of different schedules possible for $n$ processes to be scheduled on one processor is given by the formula: $n!$. where $n!$ (n factorial) is the product of all positive integers from 1 to $n$.


![[Screenshot 2024-02-22 at 16.52.41.png]]
- In CPU scheduling, the distinction between preemptive and nonpreemptive scheduling lies in how processes are managed and switched during execution:

- **Nonpreemptive Scheduling**: Once a process starts its execution on the CPU, it cannot be stopped or interrupted until it completes its CPU burst time. In nonpreemptive scheduling, the CPU control is voluntarily released by the process, either by terminating or by switching to waiting state due to I/O request or other forms of waiting. This approach ensures that once a process is in execution, it runs to completion without interruption, leading to predictable execution patterns but potentially less responsive system behavior.

$$
\text{Nonpreemptive scheduling: Process continues execution until completion or voluntary yield.}
$$

- **Preemptive Scheduling**: In preemptive scheduling, the operating system can interrupt and suspend a currently running process to start or resume another process. This decision can be based on priority, time slices (quantum), or other scheduling algorithms. Preemptive scheduling allows for more responsive systems, especially in time-sharing environments, by enabling the CPU to switch among processes more dynamically. However, it introduces the complexity of managing shared resources safely among processes to avoid issues such as deadlocks and race conditions.

$$
\text{Preemptive scheduling: Process execution can be interrupted for another process to execute.}
$$

![[Screenshot 2024-02-22 at 17.08.28.png]]
- For FCFS we simply execute the first process that we get with no respect to its runtime. We the execute the second process and so on until all of the processes are executed. In the real world this can easy be manageed by a FIFO Queue
$$ 
P_1+P_2+P_3 = 8+(8+4-0,4)+12 = 31,6
$$
$$
31,6/3=10,53
$$
- For SJF as the name implies we execute the shortest job first. But in this example the processes don't arrive at the same time. We have to choose between the preemptive and the nonpreemptive version of SJF. The nonpreemptive version executes the shortest job and then goes to the next job in the queue that is shortest. The preemptive version stops the current job if there happens to be a job that is shorter than the remaining time on the current job. For nonpreemtive scheduling the turnaround time looks like this
$$ P_1 + P_2 + P_3 =13 $$
$$
13/3=4,33
$$

| Time | Job | P1 remain | P2 remain | P3 remin |
| ---- | ---- | ---- | ---- | ---- |
| 0 | P1 | 8 | 0 | 0 |
| 1 | P3 | 7 | 4 | 1 |
| 2 | P2 | 7 | 4 | 0 |
| 3 | P2 | 7 | 3 |  |
| 4 | P2 | 7 | 2 |  |
| 5 | P2 | 7 | 1 |  |
| 6 | P1 | 7 | 0 |  |
| 7 | P1 | 6 |  |  |
| 8 | P1 | 5 |  |  |
| 9 | P1 | 4 |  |  |
| 10 | P1 | 3 |  |  |
| 11 | P1 | 2 |  |  |
| 12 | P1 | 1 |  |  |
| 13 |  | 0 |  |  |
| 14 |  |  |  |  |
$$ 12/3=4$$
- C) P3, P2, P1
	$$ 1+ (1+1+4-0,4)+(1+1+4+8)=6,86$$

![[Screenshot 2024-02-22 at 17.58.49.png]]
a) Drawn

b)

| P | FCFs | SJF | Pri | RR |
| ---- | ---- | ---- | ---- | ---- |
| p1 | 2 | 3 | 15 | 2 |
| p2 | 3 | 1 | 20 | 3 |
| p3 | 11 | 20 | 8 | 20 |
| p4 | 15 | 7 | 19 | 12 |
| p5 | 20 | 12 | 13 |  |
|  |  |  |  |  |

c)

| P | FCFS | SJF | Pri | RR |
| ---- | ---- | ---- | ---- | ---- |
| p1 | 0 | 1 | 13 | 0 |
| p2 | 2 | 0 | 19 | 2 |
| p3 | 3 | 12 | 0 | 12 |
| p4 | 11 | 3 | 15 | 9 |
| p5 | 15 | 7 | 8 | 13 |

d)SJF 4,6

![[Screenshot 2024-02-22 at 18.39.55.png]]
a)

b)

c)

d)

![[Screenshot 2024-02-22 at 18.40.27.png]]
- Processes with low cpu bursts get executet first. this means that io bound processes are executed first

![[Screenshot 2024-02-22 at 18.46.46.png]]

a) SJF is a priority queue where the shortest job has the highest priority

b) MFQ could implement FCFS in one of its queues

c) FCFS is a priority queue where the first incoming job has the highest priority

d) No relation because burst time is irrelevant in RR

![[Screenshot 2024-02-22 at 18.51.22.png]]
A CPU scheduling algorithm that favors processes having used the least processor time in the recent past is designed to prioritize I/O-bound programs while still providing CPU-bound programs with opportunities to execute. The reasoning behind this behavior involves understanding the characteristics of I/O-bound and CPU-bound programs:

- **I/O-bound programs** typically perform operations that require waiting for I/O devices (such as disk drives, network interfaces, etc.). They spend more time waiting for I/O operations to complete than executing instructions on the CPU. As a result, their actual CPU usage is low compared to CPU-bound programs. By favoring processes with the least recent processor time, the scheduling algorithm naturally prioritizes I/O-bound processes because they frequently yield the CPU to wait for I/O operations, thus accumulating less processor time.

$$
\text{I/O-bound programs are favored because they accumulate less processor time due to frequent I/O waits.}
$$

- **CPU-bound programs**, on the other hand, spend most of their time executing instructions on the CPU without requiring significant I/O operations. These programs would typically accumulate more processor time quickly. However, they are not permanently starved by the scheduling algorithm for several reasons:
    1. **Fairness mechanism**: Most scheduling algorithms incorporate some form of fairness to ensure that all processes get a chance to execute. This might include increasing the priority of CPU-bound processes gradually as they wait to prevent starvation.
    2. **Dynamic adjustment**: The prioritization based on processor time is typically dynamic. If a CPU-bound process has been waiting for a significant amount of time, its relative processor time usage may decrease in comparison to other processes, especially if those processes have been executing recently. This dynamic adjustment ensures that CPU-bound processes will eventually receive CPU time, preventing permanent starvation.

$$
\text{CPU-bound programs are not permanently starved because the algorithm dynamically adjusts priorities, ensuring fairness.}
$$

This scheduling strategy aims to optimize system responsiveness and efficiency by quickly servicing I/O-bound processes, which often wait for external operations, while also ensuring that CPU-bound processes receive necessary processing time, albeit with potentially lower priority compared to their I/O-bound counterparts.

![[Screenshot 2024-02-22 at 18.55.09.png]]
PCS schedules user level threads .SCS schedules kernel level threads

![[Screenshot 2024-02-22 at 18.57.44.png]]
$$ 
Priority = (recent CPU usage/2)+base
$$
$$
Base = 60
$$
$$
P_1= (40/2)+60=80
$$
$$
P_2= (18/2)+60=69
$$
$$
P_3= (10/2)+60=65
$$
A process with high recent cpu usage will get a bigger priority increase. This means that process with low cpu time (I/O bound processes) get a samller increase to their priority compared to cpu bound processes

![[Screenshot 2024-02-22 at 20.10.17.png]]
I/O-bound programs are more likely to have **voluntary context switches**, while CPU-bound programs are more likely to have **nonvoluntary context switches**. The reasoning behind this distinction lies in the nature of the workloads that each type of program typically handles:

- **I/O-bound programs** spend a significant portion of their execution time waiting for I/O operations to complete. These operations include reading from or writing to a disk, sending or receiving data over a network, interacting with user input, etc. Because these programs often wait for external events, they voluntarily yield the CPU to other processes while waiting, leading to voluntary context switches. This behavior optimizes the CPU usage by allowing other processes to execute while the I/O-bound process waits for its I/O operation to complete.

$$
\text{I/O-bound programs voluntarily yield the CPU during I/O waits, leading to voluntary context switches.}
$$

- **CPU-bound programs**, in contrast, are characterized by their intensive use of the CPU for computation. They spend most of their time performing calculations or processing data and do not frequently wait for I/O operations. Nonvoluntary context switches are more common with CPU-bound programs because the operating system may need to preempt these processes to ensure fair CPU time distribution among all processes, including I/O-bound processes. This preemption is necessary to maintain system responsiveness and prevent any single process from monopolizing the CPU, which could lead to starvation of other processes.

$$
\text{CPU-bound programs are preempted by the operating system to ensure fair CPU distribution, leading to nonvoluntary context switches.}
$$

In summary, the likelihood of voluntary versus nonvoluntary context switches is closely tied to the nature of the programs' workloads, with I/O-bound programs often yielding the CPU voluntarily due to I/O waits, and CPU-bound programs being preempted involuntarily to maintain system fairness and responsiveness.

![[Screenshot 2024-02-22 at 20.19.48.png]]
The BTV scheduler can ensure that higher-priority threads receive more attention from the CPU than lower-priority threads by allocating a greater number of lottery tickets to higher-priority threads compared to those with lower priorities. This approach is based on the principle of probability where the likelihood of an event (in this case, winning the lottery and thus gaining CPU time) is directly proportional to the number of opportunities (lottery tickets) a participant (process) has. Here's how this technique works:

1. **Ticket Allocation**: Each thread is assigned a certain number of lottery tickets based on its priority level. Higher-priority threads are given more tickets than lower-priority threads. This does not mean lower-priority threads are excluded from the CPU allocation; rather, their chances of winning are proportionally less compared to those of higher-priority threads.

$$
\text{Number of tickets per thread} \propto \text{Thread's priority}
$$

2. **Lottery Draws**: When a scheduling decision is to be made (50 times each second in the BTV system), a lottery ticket is randomly selected from the pool of all tickets. The thread holding the winning ticket is granted 20 milliseconds of CPU time.

3. **Ensuring Fairness and Priority**: By adjusting the number of tickets per thread according to priority, the scheduler inherently biases CPU time allocation towards higher-priority threads. The probability of a high-priority thread winning any given lottery is higher than that of a low-priority thread. However, since the lottery is held frequently (50 times each second), all threads, regardless of their priority, have a chance to win CPU time over a given period, thereby preventing starvation.

$$
\text{Probability of winning} \propto \text{Number of tickets held by the thread}
$$

4. **Dynamic Adjustments**: The BTV scheduler can dynamically adjust the number of tickets allocated to each thread based on various factors such as changing priority levels, the need to prevent starvation of low-priority threads, or to reward threads for releasing resources voluntarily. This flexibility allows the system to respond to runtime conditions and workload characteristics effectively.

In summary, the lottery scheduling mechanism in the BTV operating system ensures that higher-priority threads receive more CPU time by allocating a greater number of lottery tickets to them. This method provides a probabilistic yet fair scheduling approach, balancing the need for prioritizing urgent or important processes while still allowing lower-priority processes an opportunity to execute.

![[Screenshot 2024-02-22 at 20.28.26.png]]
a) if $a$ is 0 then $t_{n+1}=t_0$ because the recent history has no effect as a controls the weight of recent and past history

b) as $a$ is very close to 1 almost only the most recent cpu bursts matter as history is irrelevant

![[Screenshot 2024-02-22 at 20.31.41.png]]
- RRRS increases the quantum for CPU bound processes as these are most likely to use up their whole time quantum. I/O bound processes are much more likely to to not use the whole quantum.

![[Screenshot 2024-02-22 at 20.34.29.png]]
a)

b)

c)

![[Screenshot 2024-02-22 at 20.37.08.png]]
B and c

![[Screenshot 2024-02-22 at 20.37.39.png]]
- 


![[Screenshot 2024-02-22 at 20.38.31.png]]
a) does not discriminate in either way as it does not look at process length

b) RR is in favor of short processes as these get processed faster than long processes

c)


![[Screenshot 2024-02-22 at 20.40.35.png]]
- 

![[Screenshot 2024-02-22 at 20.42.20.png]]
- 