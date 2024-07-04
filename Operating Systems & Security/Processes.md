#OperatingSystems
## **What is a process?** 
==A process is a program/ application under execution.==
It is the set of CPU state, memory (including heap and stack), I/O, and program (instructions).
It is a dynamic entity working towards some goal.
A ”container” holding a number of resources (allocated to the process)
An entity that executes instructions according to the loaded program.

Information associated with each process:  
• [[#**Process States**||Process state]] 
• Program counter
• CPU registers  
• CPU scheduling information  
• Memory-management information  
• Accounting information  
• I/O status information

![[Pasted image 20240516173200.png]]


## **Difference between a process and an application**

An application is just a passive file located on some storage.
Its a set of instructions that direct the computer to 'do a thing'.
The application becomes a part of the process once it is started.

## **Process States**

![[Pasted image 20240516173626.png]]

new -> new processes are created by the user or system
ready-> queue of ready processes (at any point in time a process from here can be scheduled on the CPU by the process scheduler) (can be scheduled by round robin, priority based, etc.) (can have thousands of processes in the ready state)
running -> only one process in the running state at a time. very rarely is a process completed in one go. usually only run for a few ms then put back in the ready state. 
waiting -> waiting for some input output of event completion, when done goes back to the ready state, cannot go directly back to running state

context switching == multitasking

![[Pasted image 20240516174500.png]]
dispatcher is a part of the process management component of the OS (dispatcher is making the decisions for which process to run)

![[Pasted image 20240516180158.png]]
typically -> time slice expires and the process goes back to the ready queue a bunch of times until it is completed
fork a child ->
## **Context Switching**
When CPU switches to another process, the system ==*must save the state of the old process*== and load the saved state for the new process via a context switch.  
![[Pasted image 20240516181053.png]]

The context of a process is represented in the [[#**Process control block**|Process Control Block (PCB)]].  

Context-switch time is overhead; the system does no useful work while switching (however, it is essential to implement a multi-user, multi-tasking environment)

## **Process control block**

The PCB has 3 main regions:  
1. [[#**Process Identification**|Process Identification]]  
2. [[#Processor state information|Processor state information ]] 
3. [[#Process control information ]] 

![[Pasted image 20240516181340.png]]

###### Process Identification
Contains info such as the user who created the process, date and time started, etc.
• Process id (pid)  
• Parent Process (ppid)  -> process identification can only be created from a parent process
• User id (uid)

###### Processor state information:  
• User-visible registers  
• Control and status registers  
• Stack pointers (both User and Kernel)

###### Process control information:  
• State  
• Priority  
• Scheduling information  
• Inter process communication info and other shared data structures  
• Process privileges  
• Memory management data  
• Resource usage (open files, etc.), utilization and accounting data

## Processes in Unix

See [[Linux]] for more info.

```
//processids.c  
#include <stdio.h>  
#include <unistd.h>  
//process id, parent id, process group id  
main(void) {  
int id1=getpid(); //System call  
int id2=getppid(); //System call  
int id3=getgid(); //System call  
printf("\n The current process id is %d \n",id1);  
printf("\n The parent id of the current process is %d \n",id2);  
printf("\n The group id of the current process is %d \n",id3);  
}  
$ gcc –o processids processids.c  
$./processids
```

getpid().. etc. these ids are all created upon process creation
```
int id1=getpid(); //System call  
int id2=getppid(); //System call  
int id3=getgid(); //System call  
```

• Unix is a multiuser and multitasking operating system  
	• Multiple users can run their programs concurrently and share hardware resources  
	• An user can run multiple programs and tasks concurrently  
• It appears that the execution is done in parallel, however in reality the OS switches between multiple users and processes rapidly (back and forth) in an interleaved manner  
• Unix Processes:  
	• An executing program is a process.  
	• welcome.c (program)-> welcome (executable)->./welcome (process)  
• Every process in Unix has the following :  
	• A unique process ID (PID)  
	• Some code : instructions that are being executed  
	• Some data : variables (typically)  
	• A stack : a form of memory where it is possible to push and pop variables/data  
	• An environment : CPU registers' contents, tables of open files 

Unix starts as a single process, called init. The PID of init is 1.  
• The only way to create a new process in Unix, is to duplicate an existing one.  
• The process init is the ancestor of all subsequent processes.  
• Process init never dies!!!!  

The creation or spawning of new processes is done with two system calls :  
	• fork() : duplicates the caller process  
	• exec() : replaces the caller process by a new one.

## Creating a new process: the fork system call:

• Synopsis: pid_t fork(void)  
• when successful, the fork() system call :  
	• creates a copy of the caller (parent) process  
	• returns the PID of the newly created child process to the parent  
• returns 0 to the new process (the child).  
• If not successful, fork() returns -1.  
• fork() is a strange system call : called by a single process but returns twice, to two  
different processes (parent and child)  
• Very important: After the fork() system call is invoked in the parent and the child  
process is created, both the parent and the child process run concurrently in the  
system // i.e the child process becomes a concurrent process  
• Execution resumes at the line immediately after the fork() statement in both the  
parent and the child process.

![[Pasted image 20240516190413.png]]


two consecutive fork statements
![[Pasted image 20240516192929.png]]
