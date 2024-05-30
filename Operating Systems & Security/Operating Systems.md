#OperatingSystems
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
