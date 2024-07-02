An Abstract Data Type ([[ADT]]) in which node ordering (priority) depends on the value of a key. A key could be a number, letter, timestamp or any other hierarchical data structure. E.g., In a FIFO queue, the key that determines priority (ordering) is the insertion time (timestamp).

### Where to Use Priority Queues?

Anywhere that priorities exist!  
- When you want to make some events more important than others  
- Packets in a network router  
- Tasks in an operating system  
- Message queue 

### Implementing a Priority Queue ADT

A priority queue can be implemented through a singly linked list, doubly linked list, or an array. In an ADT, implementation details can change but the interface that the client sees (usage) remains the same
How its implemented affects the Big O order of the overall algorithm depending on if we require the queue to be sorted vs. unsorted.
Consider effect of the implementation choice for:  
 Inserting a new element  
 Changing the value of a specific element  
 Deleting / finding the largest / smallest element  
 Joining queues   

![[Pasted image 20240606132044.png]]
O(N) (above) is because need to re-sort (if ordered) after modification or need traverse list (if unordered)
### Priority Queue Code:
``` cpp
typedef struct pq* PQ;  
typedef struct PQnode* PQlink;  
PQ PQInit(); // Create empty PQ  
int PQEmpty(PQ); // Is PQ empty?  
PQlink PQInsert(PQ, Item); // Add a node with priority  
Item PQdelmax(PQ); // Delete front of PQ  
void PQchange(PQ, PQLink, Item); // Change a key in the PQ  
void PQdelete(PQ, PQlink); // Delete any node in PQ  
void PQjoin(PQ, PQ); // Merge two PQs  
Item PQpeek(PQ); // View max item
```

### Duplicate Keys

Priority queues have keys to identify elements, eg the index i in an array identifies the a[i] element. 
So, what do we do with duplicate keys?  
Options: 
- Reject an insertion of a duplicate key?  
- Allow an insertion of duplicate key? 
	- And have some other way to differentiate them 
- Delete original and insert the new one?  

The option selected is a policy decision of the ADT implementation.