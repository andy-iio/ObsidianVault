#OperatingSystems
### What is an operating system?
- Software
- Acts as an interface b/t the hardware and the users (applications/programs)
- Manages the hardware resources in a multi-user and multi-tasking environment
### Role of operating systems
All operating systems provide services for the programs they run. Typical services include:
- executing a new program
- opening / reading a file
- allocating a region of memory
- getting the current time
### Architecture of the UNIX operating system
The core of the UNIX OS is called the **kernel.**
The **kernel** directly interacts with the HW and provides services to applications.
The interface of the kernel is a layer of SW called the **system calls.** see: [[#System Calls]]
**Libraries** of common functions are built on top of the system call interface, but applications are free to use both.
The **shell** is a special application  that provides an interface for  running other applications.
![[Pasted image 20240619174339.png]]

## System calls
No application/program can access the hardware resources/kernel directly.
It has to be done through system calls.

A system call is a way for a program to ask the operating system (the software that manages the computer's hardware) for help with something it can't do on its own.)

In other words, when a program needs to perform an action that requires permission or access to something that's controlled by the operating system (like reading or writing to a file, connecting to the internet, or controlling hardware), it makes a request to the operating system by making a system call.

The operating system then responds to this request, either granting permission and performing the requested action, or denying the request if it's not allowed.

![[Pasted image 20240619174500.png]]

### Major components of the kernel
Process Management 
Memory Management (Primary Memory) 
File Management (Secondary Memory)
I/O Management 
Security Management

### OS design and implementation

**User Goals:**
Easy to Use
Availability
Response Time

**System Goals:**
Resource Utilization
Prevent Resource Starvation
Robustness 
Fault Tolerance  
Security

Policy == what to implement  
An OS implements a variety of policies. 
Mechanism == how to implement it

### Other
Operating systems were developed to provide a convenient secure, consistent interface for applications to use.

The operating system is a layer of software between the applications and the computer hardware that supports applications and utilities

We can think of the OS as providing a uniform, abstract representation of resources (main memory, network interfaces, file systems, etc.) that can be requested and accessed by applications.  

Once the OS has created these resource abstractions for applications to use, it must also manage their use.  

How the OS manages the execution of these applications such that:  
• Resources are made available to multiple applications?  
• The physical processor is switched among multiple applications so all will appear to be progressing?  
• The processor and I/O devices can be used efficiently?  

The approach taken by all modern operating systems is to rely on a model in which multiple processes are concurrently executed in an interleaved manner  

• The OS rapidly switches rapidly between multiple [[Processes|processes]] executing a few instructions each process at a time, thereby leading to an illusion that all process are being executed at the same time (concurrently)
eg word, teams, zoom, all seem like they are running at the same time but really the OS is just quickly switching between them.
