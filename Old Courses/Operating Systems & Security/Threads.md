### What are threads?

A thread is a single flow of execution within a program. It's a sequence of instructions that the CPU (Central Processing Unit) executes, but it's not a separate program. eg. a single strand in a rope -> it's part of the larger rope, but it has its own distinct properties and behavior.

Here are some key characteristics of threads:

1. **Lightweight**: Threads are lighter than processes, which are separate programs with their own memory space and resources. Threads share the same memory space as the parent process.
2. **Concurrent execution**: Multiple threads can run concurrently, sharing the same resources and memory space. This allows for efficient use of CPU time and improved responsiveness. (intra-process concurrency)
3. **Independent execution**: Each thread has its own program counter, stack, and registers, which allows it to execute independently of other threads.
4. **Shared resources**: Threads share the same memory space and resources as the parent process, which means they can access and modify shared variables and data structures.
5. **Communication**: Threads can communicate with each other using various synchronization primitives, such as locks, semaphores, and shared memory.

Threads are created by a process, which is a self-contained unit of execution. A process can create multiple threads, and each thread can execute its own code, but they all share the same memory space.

eg. threads are like multiple hands working together to complete a puzzle. Each hand represents a thread, and they all work together to solve the puzzle (execute the program), but each hand has its own specific role and responsibility.

In summary, threads are lightweight, concurrent flows of execution within a program that share resources and memory space, allowing for efficient and flexible execution of tasks. 
### Single vs Multiple Threads
Multithreading: 
- In a multithreaded system (like Linux and Windows), the OS supports multiple, concurrent paths of execution within a single process.
- This means that a single process can have multiple threads running simultaneously, sharing the same memory space and resources.
- Each thread has its own program counter, stack, and registers, but they all share the same memory space and resources as the parent process.
- The OS schedules the threads, deciding which one to execute next, based on factors like priority, availability of resources, and other scheduling algorithms.

Single-threaded approach: 
- In a single-threaded system (like MS-DOS), there is only one path of execution within a process.
- A single process can only execute one thread at a time; there is no support for concurrent execution of multiple threads within the same process.
- Each process is like a separate, self-contained unit that executes its code sequentially, without sharing resources or memory space with other processes.

So... 
- Multithreading allows multiple paths of execution within a single process, enabling concurrent processing and efficient use of resources.
- Single-threaded approach limits each process to a single path of execution, making it less efficient and less responsive.
![[Pasted image 20240619180626.png]]
- 
### Thread Contents
Threads consist of:
- Program counter
- Register set
- Stack Space

A thread SHARES with its peer threads:
- Code segment
- Data segment
- Operating system resources (eg. when one thread alters a code segment memory item (global variable) all other threads see that. Or a file opened by one thread is available to others

Each process will have 1+ threads, and each thread has: 
- An execution state (ready, running, blocked)
- A thread context (single representation of where the thread is in the execution of instructions)
- A stack
- Thread local storage (for specific local variables) -> threads have local scope and local variables
- Access to the memory and resources of the process

 ![[Pasted image 20240619180922.png]]
### Thread States
READY -> thread is ready to run, but it's not currently executing
RUNNING -> currently being executed by the CPU
BLOCKED -> not executing, waiting for some event or resource to become available before it can continue executing

**Who manages them?**

1. **User-level**: User-level threads are managed by the application or process itself. The application creates and manages its own threads using libraries or APIs provided by the operating system. The OS provides a set of APIs for creating, scheduling, and synchronizing threads.
2. **Kernel-level**: Kernel-level threads are managed directly by the operating system kernel. The kernel creates and schedules kernel-level threads, which are used for system-level tasks like disk I/O, network I/O, and interrupt handling. The kernel manages these threads using its own scheduling algorithms and data structures
![[Pasted image 20240619181532.png]]
### Advantages and Disadvantages of Threads

**Advantages of user-mode threads:**
- FASTER THREAD SWITCHING: when switching b/t threads, the OS doesn't need to switch contexts (i.e change address space or environment of the program) This makes it faster. (no context-switching overhead)
- CUSTOM SCHEDULING: Each application can create its own scheduling algorithm for managing threads. This means that different applications can use different strategies to decide which thread is run next. 
- PLATORM INDEPENDENCE: User-mode threads can be used on any platform, as all the necessary tools are available at the user level.

**Disadvantages of user-mode threads:**
- BLOCKING PROBLEM: If one thread is blocked (waiting for something, like i/o), all threads in the same process will be blocked as well. This means that if you have multiple processors, user-mode threads wont be able to take advantage of them.
- SINGLE PROCESSOR LIMITATION: User-mode threads can only run on a single processor (CPU). This means that if you have multiple processors, user-mode threads won't be able to take advantage of them.
- LIMITED SCALABILITY: Since user-mode threads are tied to a single process, they can't scale as well as kernel level threads, which can run on multiple processes and processors

**Advantages of kernel-mode threads:**
- MULTI-PROCESSOR SCHEDULING: Kernel-mode threads can schedule threads across multiple processors, which means that threads can run concurrently on different processors. This can *significantly* improve performance.
- HANDLING BLOCKED THREADS: If one thread in a process is blocked, kernel-mode threads can still run other threads in the same process. This means that the process as a whole is not brought to a standstill.
- MULTI-THREADED KERNEL ROUTINES: The kernel itself can be multi-threaded, which allows for more efficient and scalable system operations.

**Disadvantages of kernel-mode threads:**
- SLOW THREAD SWITCHING: When switching b/t kernel mode threads, the OS needs to perform a kernel-mode switch, which is slower than a user-mode switch. This is because the OS needs to change its own state and context before switching to the new thread. 
- HIGH CONTEXT SWITCHING OVERHEAD: Context switching b/t kernel mode threads is more expensive than b/t user-mode threads. This is because the OS needs to save and restore a lot of state info, such as register values and memory maps.

**Advantages of THREADS over PROCESSES:**
- Takes less time to create a new thread than a process (no need to fork())
- Takes less time to terminate a thread than a process
- Takes less time to switch b/t two threads within the same process
- Less communication overheads - communicating b/t the threads of one process is simple b/c the threads share files, dynamic memory allocation, global variables, etc.

**Disadvantages of THREADS over PROCESSES:**
- Synchronization (can lead to the [[Dirty Read]] problem)
- Data integrity and possible inconsistency
