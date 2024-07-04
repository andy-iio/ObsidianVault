### Concurrency
Concurrency is all about having multiple streams of execution running in parallel, working towards a common goal.
The challenge with concurrency is: 
- Communication among processes
- Sharing/ allocation of resources
- Synchronization of activities
*We need to enforce **Mutual Exclusion** - exclude all other processes from a task/action while one process is allowed to execute that task/action - you do this through semaphores , monitors, and message passing* 
### Important Terms
**Atomic Operation -** an action that can't be broken into smaller peices
**Critical Section -** a small section of code that can only be executed by 1 process/thread at a time
**Deadlock -** 2 or more processes cannot proceed b/c they each hold a lock on a resource needed by the other
- Process A is blocked b/c it needs a resource that is held by process B
- Process B is blocked b/c it needs a resource that is held by process A
**Livelock -** 2 or more processes constantly changing their state in response to the other processes, but not really accomplishing anything
**Race Condition -** 2 or more threads/processes sharing a data item and the outcome is dependent on which thread/process gets there first
**Starvation -** a ready process is not ever executed b/c the scheduler/lock mechanism overlooks it
### The dirty read problem
Problem that can happen when multiple threads/processes are accessing the same data concurrently, and one thread/process tries to read data while the other is ion the process of modifying it.
Here is a good example: 
Suppose we have a banking system with two accounts: A and B. Both accounts have a balance of $100. We have two threads: Thread 1 and Thread 2.

Thread 1 wants to withdraw $20 from account A, so it locks account A and starts the withdrawal process. However, before it can complete the withdrawal, Thread 2 comes along and tries to read the balance of account A.

Thread 2 sees the balance of account A as $100 (because Thread 1 has only locked the account, but not yet updated the balance). Thread 2 then decides to deposit $50 into account A. The balance of account A is now $150 (in Thread 2's view).

Thread 1 finally completes its withdrawal process and updates the balance of account A to $80. But wait, what about Thread 2's deposit? The deposit was made while the account was "dirty" (i.e., being modified by another thread), so the deposit is lost.

In this scenario, Thread 2 has performed a "dirty read", reading the data while it was being modified by another thread. The result is inconsistent and incorrect.

This can be avoided with various concurrency methods.
### Mutual Exclusion
**What must mutual exclusion provide?**
- 'Enforcement' - no process is able to go around, or subvert the mutual exclusion
- No impact / interference to other processes if a process is halted in a non-critical section
- Access to critical section must be given in a timely fashion (deadlock, starvation)
- No delay on process entering critical section if there are no existing mutual exclusions
- Mechanism must be 'physical equipment' agnostic (processors)
- No process can stay in critical section indefinitely
### Mutual Exclusion Mechanisms
##### Semaphores
The semaphore is like a gatekeeper that controls the number of processes that can enter a restricted area (the critical section). The semaphore value represents the available slots for entering the critical section

**Wait Operation (down):**
If the semaphore value is 1, the process or thread performing the wait operation decrements the semaphore value to 0 and continues its execution, entering the critical section or accessing the shared resource.

If the semaphore value is 0, the process or thread is blocked (suspended) until the semaphore value becomes 1

**Signal Operation (up):**
When a process or thread finishes using the critical section or shared resource, it performs the signal operation, which increments the semaphore value from 0 to 1

If there are other processes or threads waiting on the semaphore, one of them is allowed to proceed.

**Example:**
Suppose we have a printer shared by multiple processes. We want to ensure that only one process can print at a time.

- Initialize the semaphore to 1, meaning only one process can print at a time.
- When a process wants to print, it performs a wait operation (decrement). If the semaphore value is 1, it decrements to 0 and allows the process to print.
- When the printing process finishes, it performs a signal operation (increment), incrementing the semaphore value to 1. This signals that another process can now print.

If multiple processes try to print at the same time, they will perform a wait operation and block until the semaphore value becomes 1. When one process finishes printing, its signal operation releases one slot, allowing another waiting process to proceed and print.

In summary, semaphores provide a simple and efficient way to manage concurrent access to shared resources by controlling the number of processes/threads that can enter a critical section at any given time.
##### Mutex (locks)
A mutex is a programming flag used to hold and release an object. 
When data is that cannot be shared is acquired, or processing has started that cannot be performed simultaneously elsewhere in the system, the mutex is set to lock, which blocks other attempts to use it. The mutex is set to unlock when the data are no longer needed, or the routine is finished. 

##### Message Passing
- Message passing in operating systems is a method of communication utilized by processes or threads to share information and coordinate their actions. 
- This facilitates communication and collaboration between various segments of a program or different programs by transmitting and receiving messages. 
- This type of inter-process communication (IPC) is employed to enable effective communication among processes operating simultaneously on a computer system
##### Types of Message Passing
**Explicit Message Passing (Direct):** 
- In direct message passing, processes explicitly send and receive messages to and from each other.
- Typically involves system calls or language-specific mechanisms for sending and receiving messages.
- Examples include explicit function calls, inter-process communication (IPC) mechanisms like pipes, sockets, or message queues 

**Implicit Message Passing (Indirect)** 
- In indirect message passing, communication is facilitated through shared data structures or shared memory.
- Processes communicate by reading from and writing to shared memory locations.
- Additionally, involves the use of synchronization mechanisms (e.g., semaphores or mutexes) to ensure proper coordination.

