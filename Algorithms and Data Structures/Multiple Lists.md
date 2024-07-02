
### Multiple List Membership

Suppose we want items organized in a FIFO queue, but also want to classify these same items in other lists.
We could make copies of the node and place those copies into multiple lists, but this is a bad idea because it wastes memory with duplicates and leads to an administration nightmare as we try to delete or update all copies of the same node.
Instead of making copies, we can make nodes with multiple links.
Like with DLLs, you just need to add more links into the node structure and follow different links for different lists.
![[Pasted image 20240606133228.png]]

### Example

Image we receive messages in a FIFO queue and want to keep a set of sub-lists of the messages classified into different priority classes, so that you can traverse messages in order of priority P0 (Highest priority)  
P1 (High priority)  
P2 (Medium priority)  
P3 (Low priority)
The node structure might look like this:  
```cpp
typedef struct message MSG;  
struct message {  
char bufText[MSG_SIZE];  
unsigned char iPriority; // 0-7  
unsigned short iSender; //  
unsigned short iReceiver; // 0-128  
// etc.  
MSG *pNextFIFO; // Next by FIFO queue  
MSG *pNextSamePri; // Next by priority  
};
```

![[Pasted image 20240606133849.png]]


What needs to be done on queue insertion? -> Update tails on all lists  
What needs to be done on queue deletion? -> Update heads on all lists  
We need to modify all the pointers on the lists.
