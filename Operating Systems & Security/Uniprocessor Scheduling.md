- The key to multiprogramming is scheduling (multiple programs running at  the same time from possibly multiple users).

	- An illusion in a uniprocessor world (*In this lesson we will focus on uniprocessor systems)
	- In a multiprocessor world: n concurrent programs for n processors (later)

•4 types of scheduling
	- Long term, Medium term and Short term
	- I/O scheduling (Later)

The goal:
- The goal of processor scheduling is to assign processes to be executed by  the processor(s) over time, in a way that meets the system objectives:
	- Response time
	- Throughput
	- Processor utilization
### Important Terms
**Turnaround time** - This is the interval of time between the submission  of a process and its completion. Includes actual execution time plus time  spent waiting for resources, including the processor. 
**Response time** - For an interactive process, this is the time from the  submission of a request until the initial response is received. 
**Deadlines** - When process completion deadlines can be specified, the  scheduler should subordinate other goals to that of maximizing  the percentage of deadlines met.
**Predictability** - A given job should run in about the same amount of  time and at about the same cost regardless of the load on the system. A  wide variation in response time or turnaround time is not desirable
**Quantum -** Time quantum or time slice. It is a fixed, predefined amount of time for which a process is allowed to run on the CPU before the operating system's scheduler interrupts it and switches to another process.
**Preemptive** - In preemptive scheduling, the operating system can interrupt a currently running process and allocate the CPU to another process.
**Cooperative (non-preemptive)** - In non-preemptive scheduling, a running process cannot be interrupted; it runs until it completes its execution or voluntarily releases the CPU.

### Scheduling Objectives
**Throughput** - The scheduling policy should attempt to maximize the  number of processes completed per unit of time. This is a measure of how  much work is being performed. This clearly depends on the average  length of a process, but is also influenced by the scheduling policy, which  may affect utilization.
**Processor utilization** - This is the percentage of time that the processor  is busy. For an expensive shared system, this is a significant criterion. In  single-user systems and in some other systems, such as real-time systems,  this criterion is less important than some of the others.
**Fairness** - In the absence of guidance from the user or other
system-supplied guidance, processes should be treated the same, and no  process should suffer starvation.
**Enforcing priorities** - When processes are assigned priorities, the  scheduling policy should favor higher-priority processes.
**Balancing resources** - The scheduling policy should keep the resources  of the system busy. Processes that will under-utilize stressed resources  should be favored. This criterion also involves medium-term and long-term scheduling. 

### Long-Term Scheduling
Long-term scheduling (Admission Control) refers to the scheduling that is performed when a new  process is created.

•A decision must be made on whether a new process should be allowed to  join the set of already active processes.

•The request would likely be denied is the system determines that the system  objectives would be noticeably impacted.

•The more processes that are created, the less time each has on the CPU

•If admitted, the newly created process joins the queue belonging to the  short-term scheduler (the entity responsible for allocating CPU time)

The long-term scheduler may have a queue of processes waiting to be  admitted:

•A waiting process will be admitted into the short-term scheduler’s ready  queue when an existing process terminates. The mechanism for selecting  this process may be based on:

•FCFS (first come, first served)

•Process priority

•Expected execution time

•I/O requirements
### Mid-Term Scheduling
•Used when a process is moved from blocked to blocked/suspended and back.

•The scheduler has to make a decision on which of the blocked/suspended processes are moved to the blocked state and vice versa

•If the scheduler calculates that the process in the blocked state may wait for longer than expected time for its I/0 operation to complete, it might consider moving it to the blocked/suspended state.
### Short-Term Scheduling
•Also known as the dispatcher

•Short term scheduling corresponds to the actual decision of  which ”ready” process will execute next.

•The relationship between the states (and the  allowed transitions) are shown here.
The short term scheduler is invoked whenever an event occurs that could  affect the state of the running process. These events include:

•Clock interrupts (time-slice)

•I/O interrupts

•Operating System calls

•Signals (eg: semaphore, mutex, etc)

The clock interrupt is the mechanism that triggers a preemption
### Scheduling Algorithms
##### FCFS
The simplest scheduling policy is first-come-first-served (FCFS), also known as  first-in, first-out (FIFO) or a strict queuing scheme.

As each process becomes ready, it joins the ready queue. When the currently  running process ceases to execute, the process that has been in the ready  queue the longest is selected for running

Once a process completes its execution or gets blocked, the next process in the ready queue is selected.

**Pros?**
•Simple
•Good for long, generally similar processes/jobs

**Cons?**
•Does quite poorly with a mix of short and long jobs
•Tends to favor longer (computationally intensive) jobs
##### Round Robin
A clock interrupt is generated at periodic intervals. When the interrupt  occurs, the currently running process is placed in the ready queue, and the  next ready job is selected on a FCFS basis (This reduces the penalty that  short jobs suffer with FCFS).

This technique is also known as time slicing, because each process is given a  slice of time before being pre-empted

**Pros?**
•Effective in a general-purpose time-sharing system or transaction  processing system.

**Cons?**
•Context switching costs
##### SPN
Another approach to reducing the bias in favor of long processes inherent in  FCFS is the shortest process next (SPN) policy.

This is a non-preemptive policy in which the process with the shortest  expected processing time is selected next. (Thus, a short process will jump to  the head of the queue past longer jobs.)

**Pros?**
•Overall performance is significantly improved in terms of response  time
**Cons?**
•Need to know (or at least estimate) the required processing time of each  process.
•Variability of response times is increased, especially for longer processes,  and thus predictability is reduced.
•Possible starvation for longer processes, as long as there is a steady supply  of shorter processes.
##### SRT
The shortest remaining time (SRT) policy is a preemptive version of SPN.

**Pros?**
•Does not have the bias in favor of long processes found in FCFS
•Unlike round robin, no additional interrupts are generated, reducing  overhead
•SRT should also give superior turnaround time performance to SPN,  because a shorter job is given immediate preference to a running longer job

**Cons?**
• elapsed service times must be recorded, contributing to overhead.
### Linux Completely Fair Scheduler
The Completely Fair Scheduler (CFS) is a process scheduler used in the Linux kernel.

The CFS algorithm is part of the kernel's scheduler, which is responsible for determining which process should run next on the CPU.

•**Fairness:** CFS aims to provide fairness among all processes. It assigns each process a "virtual runtime" based on the amount of CPU time it has consumed. The process with the smallest virtual runtime is scheduled to run next.

•**Dynamic Priority:** Instead of using fixed priorities, CFS uses dynamic priorities based on the virtual runtime. This allows the scheduler to adapt to changes in process behavior over time.

•**Scheduling Entities**: CFS treats both processes and threads as scheduling entities. Each scheduling entity is assigned a weight that determines its share of the CPU time. The scheduler adjusts the virtual runtime based on the weight.

•**Proportional Share Scheduling**: CFS provides proportional share scheduling, meaning that processes with higher weights get more CPU time than those with lower weights. This allows for efficient resource allocation in a multi-tasking environment.

•**Low Latency:** While fairness is a primary goal, CFS also aims to keep latency low. Processes should be able to start quickly when they need CPU time.

virtual_runtime=current_time + load_weight​/weight
•current_time is the overall processing time consumed by the process so far (Zero when the process is newly created)
•load_weight is the weight of the scheduling entity assigned initially by the scheduler
•weight is the system-wide weight (of all processes) as calculated by the scheduler
### Windows Priority Scheduler
Windows uses a priority-based scheduling algorithm to manage the execution of processes and threads. The priority queue in Windows is implemented through the Windows Scheduler

**Priority Levels:**
•Each process and thread in Windows is assigned a priority level, which determines its relative importance in the scheduling queue.
•Priority levels range from 0 to 31, where 0 is the lowest priority, and 31 is the highest.

**Dynamic Priority Adjustment:**
•Windows uses a dynamic priority adjustment mechanism. The priority of a thread can be adjusted dynamically based on its behavior and resource usage.
•Threads that have been waiting for CPU time may receive a priority boost to increase their chances of being scheduled.

**Foreground and Background Priority**
•Windows distinguishes between foreground and background processes. Foreground processes typically have higher priority than background processes to ensure a responsive user experience.
•Interactive processes, such as those associated with the user interface, are given higher priority.

**Priority Classes**
•Processes are categorized into priority classes, such as "Realtime(16-31)," "High," "Normal," "Idle(0)," etc.
•Each priority class has a default priority level, and the scheduler uses this information to assign initial priorities (and then changes it dynamically)