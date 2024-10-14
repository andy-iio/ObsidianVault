The file system permits users to create data collections, called files, with desirable properties, such as:
- Long-Term Existence
	- Files are stores on disk or other secondary storage 
	- Files do not disappear when a user logs off
- Shareable between processes:  
	- Files have names and can have associated access  
	- permissions that permit controlled sharing.  
- Structure:  
	- Depending on the file system, a file can have an internal structure  
	- That is convenient for particular applications. In addition, files can be organized into a hierarchical or more complex structure to reflect the relationships among files

### Primitive Operations
Typical operations include the following:  
• Create: A new file is defined and positioned within the structure of files.  
• Delete: A file is removed from the file structure and subsequently destroyed.  
• Open: An existing file is declared to be “opened” by a process, allowing the process to perform functions on the file.  
• Close: The file is closed with respect to a process, so the process no longer may perform functions on the file, until the process opens the file again.  
• Read: A process reads all or a portion of the data in a file.  
• Write: A process updates a file, either by adding new data that expands the size of the file, or by changing the values of existing data items in the file

All operations have their corresponding system call in linux

### File Management System
A file management system is a part of the operating system that provides services to users and applications in the use of files. Typically, the only way a user or application may access files is through the file management system.  

##### Objectives of an FMS
• To meet the data management needs and requirements of the user, which include storage of data and the ability to perform the aforementioned operations  
• To guarantee, to the extent possible, that the data in the file are valid  
• To optimize performance, both from the system point of view in terms of overall throughput, and from the user’s point of view in terms of response time  
• To provide I/O support for a variety of storage device types  
• To minimize or eliminate the potential for lost or destroyed data -> needs a mechanism to create backups 
• To provide a standardized set of I/O interface routines to user processes  
• To provide I/O support for multiple users, in the case of multiple-user systems -> multitasking environment

##### FMS Requirements
Those objectives translate into a set of requirements:  
• Each user should be able to create, delete, read, write, and modify files.  
• Each user may control what types of accesses are allowed to the user’s files.  
• Each user may have controlled access to other users’ files.  
• Each user should be able to move data between files.  
• Each user should be able to back up and recover the user’s files in case of damage.  
• Each user should be able to access files by name rather than by numeric identifier.

### Filesystems Architecture

![[Pasted image 20240704172329.png]]
##### Device drivers 
Device drivers are software programs that allow operating systems to communicate with and control hardware devices (from potentially several manufacturers)  

They act as intermediaries between the hardware and the operating system. (The OS cannot directly talk to any piece of hardware, so it needs to go through device drivers) 

Responsible for starting I/O operations on a device and processing the completion of an I/O request.

Considered to be a part of the operating system.

##### Basic file system  
The primary interface with the environment outside of the computer system.  

Deals with blocks of data that are exchanged between devices and is concerned with the placement of those blocks on the secondary storage device and buffering of those blocks in main memory. (basic file system keeps track of where files are physically stored, e.g. which blocks is a file saved on, how many blocks does it use, is it continuous set of blocks or chained set of blocks, etc.)

Does not understand the content of the data or the structure of the files involved.  

Considered to be part of the operating system.

##### Basic I/O supervisor  
Responsible for all file I/O initiation and termination.  

Control structures are maintained that deal with device I/O, scheduling, and file status.  
This level selects the device on which file I/O is to be performed, based on the file selected.  
Concerned with scheduling disk and tape accesses to optimize performance.  

I/O buffers are assigned, and secondary memory is allocated at this level.

Considered to be part of the operating system.

##### Logical I / O  
Enables users and applications to access records  

The logical I/O module deals with file records and provides a general-purpose record I/O capability and maintains basic data about files.  

Provides the ability to create, delete, read, write etc. through system calls

##### Directories
Tree structure helps to facilitate a quicker search for files, programs, etc.

The directory contains information about the files, including attributes, location, and ownership.  

Directory ’mechanism’ is managed by the operating system.  

*The directory is itself a file*, accessible by various file management routines. From the user’s point of view, the directory provides a mapping between file names, known to users and applications, and the files themselves.

**Directory Structure**:
Varies widely among various systems.

Some of the information may be stored in a header record associated with the  file types of operations that may be performed on the directory:

•**Search:** When a user or application references a file, the directory must be searched to find the entry corresponding to that file.
•**Create file:** When a new file is created, an entry must be added to the directory.
•**Delete file:** When a file is deleted, an entry must be removed from the directory.
•**List directory:** All or a portion of the directory may be requested. Generally, this request is made by a user and results in a listing of all files owned by that user, plus some of the attributes of each file (e.g., type, access control information, usage information).
•**Update directory:** Because some file attributes are stored in the directory, a change in  one of these attributes requires a change in the corresponding directory entry.

The simplest form of structure for a directory is  that of a list of entries, one for each file.

This structure could be represented by a simple  sequential file, with the name of the file serving as  the key. But it will be inadequate when multiple  users share a system and even for single users with  many files.

A more powerful and flexible approach, and one  that is almost universally adopted, is the hierarchical, or tree-structure

As before, there is a master directory (root directory), which has  under it several user directories.

![[Pasted image 20240704174428.png]]
**Directory Naming**
Users need to be able to refer to a file by a symbolic name. (thus each file in the system must have a unique name in order that file references be unambiguous. But it will be a burden on users to require they provide unique names, especially in a shared system.)  
The use of a tree-structured directory minimizes the difficulty in assigning unique names:  
• Any file in the system can be located by following a path from the root or master directory down various branches until the file is reached.  
• Typically, an interactive user or a process has associated with it a current directory, often referred to as the working directory.  
• Files are then referenced relative to the working directory.  
• During execution, the user can navigate up or down in the tree to change to a different working directory.
If two files have the same name, they MUST be in different subdirectories/have different paths
![[Pasted image 20240704174559.png]]

**File Sharing**
In a multiuser system, there is almost always a requirement for allowing files to be shared among several users.

Two issues:
1.Access rights
	•The rights for themselves: None, Knowledge, Execution, Reading, Appending,  Updating, change protection, delete
	•For or By: specific user, user groups, all.

2.Simultaneous access
	•The O/S could just lock the entire file when it is being updated or
	•Have a finer record-level lock on the individual records being updated.

**Secondary Storage Management**
On secondary storage, a file consists of a collection of blocks. The operating  system or file management system is responsible for allocating blocks to files.

This raises two management issues:
	1. Space on secondary storage must be allocated to files (files are not fixed size, can grow, expand)
	2. O/S must keep track of the space available for allocation.

**File Allocation:**
Several issues are involved in file allocation:

•When a new file is created, is the maximum space required for the file allocated at once?
•Are the blocks allocated in a contiguous manner? What happens when the file size increases, and additional blocks are required?
•What sort of data structure or table is used to keep track of the portions assigned to a file?

**Preallocation vs Dynamic Allocation**  
A preallocation policy requires the maximum size of a file be declared at the time of the file creation request. (How???)  
Dynamic allocation allocates space to a file in portions as needed. (more complex)

**Contiguous allocation**
With Contiguous allocation, a single contiguous set of blocks is allocated to a file at the time of file creation.  

This is a preallocation strategy. 

The file allocation table needs just a single entry for each file, showing the starting block and the length of the file. However, this introduces problems when file changes size (files have to be moved if additional blocks are not available)  
External fragmentation will occur, making it difficult to find contiguous blocks of space of sufficient length. It will be necessary to implement a compaction algorithm to free up  
contiguous space on the disk.
![[Pasted image 20240704181445.png]]

**Chained allocation**
With Chained allocation, the allocations are done on an individual block basis.  
Each block contains a pointer to the next block in the chain. the file allocation table needs just a single entry for each file, showing the starting block and the length of the file.  
Although preallocation is possible, it is more common simply to allocate blocks as needed.  
And now the selection of blocks is now a simple matter: Any free block can be added to a chain.  
There is no external fragmentation, but there is no accommodation of the principle of locality.
![[Pasted image 20240704181455.png]]

**Indexed allocation**
The final type, Indexed allocation has a file allocation  table that contains a separate one-level index for each  file; with the index having one entry for each portion allocated to the file.

Typically, the file indexes are not physically stored as  part of the file allocation table. Rather, the file index for a file is kept in a separate block, and the entry for the file in the file allocation table points to that block.
![[Pasted image 20240704181538.png]]
