### Memory Management Objectives
**Optimal Utilization:** This involves allocating memory to processes as needed and reclaiming memory from processes that no longer require it. Efficient memory utilization helps maximize the overall performance of the system.

**Abstraction:** Memory management provides a layer of abstraction between the physical memory hardware and the processes running on the system. It abstracts the physical memory into a logical address space for each process, allowing processes to access memory without needing to know the specifics of the underlying hardware.

**Protection:** Memory management enforces memory protection mechanisms to prevent unauthorized access to memory regions. This includes protecting the memory of one process from being accessed or modified by another process without proper permission.

**Relocation:** Memory management handles the relocation of processes in memory to accommodate changes in memory availability and fragmentation. It relocates processes dynamically as needed, allowing processes to execute regardless of the physical memory addresses they were compiled for.

**Sharing:** Shared memory allows multiple processes to access the same memory region simultaneously, enabling communication and data sharing between processes without the need for costly data copying operations.

**Virtual Memory:** Many modern operating systems employ virtual memory techniques to extend the available memory beyond the physical RAM installed in the system.

Virtual memory uses a combination of RAM and secondary storage (such as disk) to provide a larger logical address space to processes than what is physically available. //addr.c

This allows the system to run more processes concurrently and handle larger data sets, improving overall system scalability.

**Logical Organization**
•While memory is organized like a very long byte array, when we write programs, we organize our programs into
•Modules and functions that are executed
•User data (both read and written)
•The stack – (transfer of data/params) between modules
**We should have:**
•Independently written/compiled modules, with runtime reference resolution
•An efficient scheme for defining access permissions
•An efficient way to share modules and functions (as in libraries)
•We will call this “**segmentation”**

**Physical Organization**
•We have primary memory – fast and volatile, and we have secondary memory – slow and persistent.
•We need to organize this memory (combination) in order to realize:
	•An efficient (and user transparent) transfer mechanism between the two
	•This should not be a user responsibility.
### Definitions
**Frame -** A fixed length block of main memory

**Page -** A fixed length block of data that resides in secondary memory. The O/S copies from pages to frames and vice versa.

**Memory Segments** - A variable length block of data that resides in secondary memory. A segment may be copied into a set of frames in main memory or may be divided into pages (each of which may be copied to/from a memory frame).

**Physical address -** The address of the actual storage cell, in the main memory, which contains the value of the data

**Virtual address -** The address presented to the running program (from the logical address/virtual address space)  //addr.c
### Memory partitioning
Memory partitioning involves how the available memory is split between user programs (We assume that the O/S occupies some fixed portion of memory).

We have 2 options:
•Fixed Partitioning – where each partition is fixed and static, the process must fit into the partition being considered
•Dynamic Partitioning – the partitions are created dynamically, so each process is allocated to a partition equal to its size
### Fixed partitioning
All partitions are statically defined early in the O/S initialization time.
New process must fit within an existing partition.
If no available partition, program cannot load.
Available as equal-sized partitions or unequal-sized partitions.
Fixed, equal-sized partitions:
	•Simple, fast (little O/S overhead)
	•If program is too big for available partition, developer must reorganize using overlays (a mechanism for loading only a portion of program at a time)
	•Inefficient- causes internal fragmentation (Process length largely varies)
	•Could lead to a lot of unused space
Fixed, unequal-sized partitions:
	•How to assign process to partition:
		•Process queue per partition:
		•Create process groups based on similar processing needs and assign each process group to a partition. Assign a process to the partition that provides the best fit (Minimizes unused space)
		•Single queue: when a new process is starting, examine the size requirement and place into a partition that provides the best fit (Minimizes unused space)
	•Provides improved flexibility with minimal additional complexity
	•Still has the problems of:
		•A fixed maximum number of active processes
		•Smaller jobs will have wasteful space utilization
### Dynamic Partitioning
Partitions are of variable length and number;
Partitions(equal to the size of processes) are dynamically created based on the process size
Leads to “holes” in memory or external fragmentation.
Memory compaction can undo external fragmentation (*requires relocation)

Placement Algorithms:
•Best Fit - Chooses the block of available memory that is nearest in size to what is required (smallest possible block that can fit the process)
•Worst performer – requires lot of work (examine all holes), and ends up creating several small fragments
•First Fit - Scans memory from beginning and chooses first, big-enough spot
•Simple implementation and good performance
•Next Fit - Starts operation where the previous allocation was made and increments up, stopping on the next, big-enough spot

 Modified version of First Fit (Does not start from the beginning and may end up being better in terms of time-complexity)
### Memory Relocation
The locations of instructions and data referenced by a process are not fixed.
They change each time a process:
•is swapped in or swapped out
•during memory compaction
•Paging
•Segmentation
Review of terms:
A **logical address** is a reference to a memory location independent of the current assignment of data to memory; a translation must be made to a physical address before the memory access can be achieved.
A **relative address** is a particular example of logical address, in which the address is expressed as a location relative to some known point (usually the starting instruction of the process)
A **physical address**, or absolute address, is an actual location in main memory.
### Paging
The OS views the secondary storage medium as a collection of equal-sized pages
Since the OS switches between processes rapidly, paging is based on the idea that the entire process need not be loaded into the memory and parts of it can be loaded and removed as required
All pages are of the same size
A page is assigned to a frame (in the main memory whose size is the same as that of a page)
Pages can be loaded into the main memory in non-contiguous frames.
The page table keeps track of which page is allocated to which frame and provides the final address resolution

### Segmentation
Segmentation divides the logical address space of a process into segments, where each segment represents a logical unit of the program, such as code (module), data, stack, etc.

•Each segment is identified by a segment number or name and has its own base address and length.
•When a program references a memory location, the CPU generates a logical address consisting of a segment number and an offset within that segment.
•The operating system also maintains a segment table, which maps each segment number to its corresponding base address and length  (Which is in turn mapped to the actual physical address using the page table)
![[Pasted image 20240620163014.png]]

### Linking and Loading
Static libraries are included directly in the executable, resulting in larger executable files

Dynamic libraries are loaded into memory only when needed, allowing for more efficient memory usage and easier library management.

The function of a **linker** is to take as input a collection of object modules and produce a load module, consisting of an integrated set of program and data modules, to be passed to the loader.

In each object module, there may be address references to locations in other modules.

The linker creates a single load module that is the contiguous amalgamation  of all the object modules.

Load Module: main() + other functions() + library functions()  //object modules and not source code

**Static Linking (Compile Time Linking)**
•Occurs when the source code is compiled.
•The linker combines object files (produced by the compiler) and libraries into a single executable file.
•Resolves references between different modules
•Results in a stand-alone executable that includes all necessary code.

**Load Time (Dynamic Linking):**
•Occurs when the program is loaded into memory for execution.
•Some parts of the program (e.g., dynamically linked libraries) are not included in the executable file but are loaded as needed.
•The dynamic linker/loader handles the resolution of references to these external libraries.
•Can result in smaller executables and allows for shared libraries to be updated independently of the application.

#### Loading
At the time of program execution: loading (from disk into memory). The loader places the requested module starting at a particular memory location.

**Types of loading:**
•Absolute loading - Program must be placed at a specific address (some O/S distributions in the past insisted on absolute loading ex- MS-DOS)
•Relocatable loading - The program can potentially be loaded at different addresses at run-time as opposed to absolute loading. This allows the code to be executed regardless of its absolute memory location, making it "relocatable."
•Dynamic run-time loading - Minimal amounts are loaded into memory, execution starts, and remaining components are loaded as/when required (Seamlessly supports relocation )
### Virtual Memory
Virtual memory is managed/maintained by both hardware and software (O/S), so the entire solution is quite complex.

The main aspects of virtual memory are
	•Paging
	•Segmentation

The break-through idea of virtual memory is that we know:
	•All references within a process are logical addresses that are dynamically   translated into physical addresses at run time. (includes swapping and relocation)
	•Processes may be broken into pieces (pages/segments) and those pieces need not   be contiguous or in and specific order

Therefore, we can say that not all pieces (page/segment) of the program need to be in main memory during execution
The piece(s)/pages in main memory “at any one time” during execution is/are called the resident set.

As long as the memory (instructions) required by the executing process is within the resident set, everything is smooth and just works. But if not:
	•The processor issues an interrupt indicating a memory access fault (page fault) and blocks the process (enters the waiting/blocked queue)
	•The interrupt handler is dispatched to load the required page from the image located on secondary storage. Once loaded, the process is returned to the ready queue.
While the idea that interrupting, then blocking the process when a page is missing in memory may seem inefficient, it enables:
•More processes to be active in memory A process can be larger than physical main memory!
Virtual memory allows for very effective multiprogramming
### Trashing

### Paging

### Translation Lookaside Buffer
Every virtual memory reference can cause 2 physical memory accesses (1 to fetch the appropriate page table entry, one to fetch the data), so we use this high-speed cache for page table entries called the TLB

Given a virtual address:
	•the processor will first examine the TLB.
	•  If the desired page table entry is present (TLB hit), then the frame number is retrieved and the real address is formed.
	•  If the desired page table entry is not found (TLB miss), then the processor uses the page number to index the process page table and examine the corresponding page table entry.
	•If the “present bit” is set:
	•  then the page is in main memory, and the processor can retrieve the frame number from the page table entry to form the real address.
	•  The processor also updates the TLB to include this new page table entry.
	•  Finally, if the present bit is not set, then the desired page is not in main memory and a memory access fault, (page fault) is issued
### Page Size
Page Size plays a big role in the efficiency of the memory management system.
•With a smaller the page size comes a reduction in the amount of internal fragmentation   (good).
•But, with a smaller page size there is a greater number of pages required per process, which results in larger page tables (not good).
•With larger page tables comes increased likelihood of a higher number of TLB misses, which might bring 2 memory accesses per memory request (not good).
### Virtual Memory Systems Policies
As we discuss the following policies, recognize that a key indicator of success is performance (reduced page faults, maximum (CPU) throughput))

There are policies (rules of operation) in virtual memory systems. These include:
•Fetch
•Replacement
•Resident set management
•Load Control
### Fetch
The Fetch Policy addresses concerns regarding when a page should be brought into main/primary memory.
This includes:
	•Demand paging - When the page is required, the page is loaded/fetched. When a process starts there are many page faults, then number tapers down as program executes
	•Prepaging - Pages beyond those that are required are loaded when the required page is being loaded (Prepaging tries to leverage the benefits or disk caching and locality of reference).
### Replacement
The Replacement Policy addresses concerns regarding when a page should be removed from main/primary memory in order to satisfy another memory load request (page fault).

The decision on which page to remove is complex due to:
•Max number of page frames can be allocated to each active process (resident set   management) //Upper limit
•Whether the set of pages to be considered for replacement should be limited to those of   the process that caused the page fault or encompass all the page frames in main memory   (resident set management)
•If multiple “candidate” pages exist, which particular page should be selected for replacement?
(replacement policy)
•Least Recently Used (LRU) - The page that has   been idle longest (how do we measure/track ? )
•First in First out (FIFO) - Uses a circular buffer:   when request comes back to start of circle, the   oldest is marked for removal
•Clock - (the best choice) This policy is similar to   FIFO, except that, in the clock policy, any frame   with a use bit of 1 is passed over by the algorithm.   The policy is referred to as a clock policy because   we can visualize the page frames as laid out in a   circle (see diagram on right).
•Also called the “Second Chance” Algorithm

### Resident set management
What is the optimal size of a resident set? How many frames/pages per process?
- **Fixed allocation:** A process gets a fixed number of frames in main memory.
	That number is decided at initial load time (process creation time)
	May be determined based on the type of process (interactive, batch, type of application)
- **Variable allocation:** The number of page frames allocated to a process to be varied over the lifetime of the process. A process that is suffering persistently high levels of page faults will be provided additional page frames to reduce the page fault rate.
	A process with an exceptionally low page fault rate will have its frame allocation reduced
### Load control
The Load Control Policy defines the number of processes that can be resident in main memory. It is also known as the multiprogramming level.

The load control policy is critical in effective memory management:
	•If too few processes are resident at any one time, then there will be many occasions when   all processes are blocked, and much time will be spent in swapping.
	•if too many processes are resident, then, on average, the size of the resident set of each   process will be inadequate and could lead to frequent page faults

In order to reduce the multiprogramming level, one or more currently running processes must be suspended (or swapped out to secondary storage).
### Virtual Memory in Linux
Linux uses a three-level page table structure for memory management
**1.Page Directory**
•At the highest level of the page table structure is the page directory.
•The page directory is an array of pointers, each pointing to a page table
•There are always a pool of processes and each process has its own page table
**2.Page Table**
•The page table sits between the page directory and the actual page frames in physical memory.
•Each entry in the page directory points to a page table.
•The page table is another array of pointers, each pointing to a page frame in physical memory.
**3.Page Frame**
•The page frame is the actual physical memory frame where data is stored.
•Each entry in the page table points to a specific page frame in physical memory.
•When a process accesses memory, the virtual address is translated to a physical address by traversing the page table hierarchy.
•When a process accesses a memory location, the CPU's memory management unit (MMU) uses the page directory and page table to translate the virtual address to a physical address.

•If a page table entry is not present in memory (i.e., the page is not currently resident in physical memory), a page fault occurs, and the operating system's page fault handler loads the necessary page from disk into physical memory.
### Virtual Memory in Windows

Default Page Size: The default page size in Windows is 4 KB. This is the size of memory that the operating system manages and allocates for virtual memory.

Large Pages: Windows supports larger page sizes, commonly referred to as "large pages" or "large memory pages." These pages are typically 2 MB or more in size. Large pages can offer performance benefits in some cases (depending on the workload type(High-Performance Applications), similar to Linux HugePages.

Enabling Large Pages: Enabling large pages in Windows involves configuring the system to allocate memory in larger page sizes. This configuration is typically done through system settings or registry settings.

**User Mode Address Space**:

Typically, the user mode address space ranges from 0x0000000000000000 to 0x000007FFFFFFFFFF (128 TB).

This space is used by user applications and DLLs. It is separated from kernel mode to protect the system from user-level errors and security vulnerabilities.

**Kernel Mode Address Space:  (128 TB)**
The kernel mode address space starts at 0xFFFF0800 00000000 and extends upwards. This space is used by the Windows kernel, device drivers, and system services.
This separation ensures that user applications cannot directly access kernel memory, providing stability and security

![[Pasted image 20240620163429.png]]