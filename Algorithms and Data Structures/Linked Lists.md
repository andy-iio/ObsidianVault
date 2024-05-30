For list processing, see [[List Processing]] (traversal, reversal)
A set of *nodes* each with a pointer to another node.
A node is a block of related items, containing the data and a link to the next node.
```cpp
struct node {
	struct node* pNext; // pNext points to a node  
	struct item Data;
};
```
![[Pasted image 20240528143345.png]]
### Linked lists vs Arrays:

| Linked List                                       | Array                                            |
| ------------------------------------------------- | ------------------------------------------------ |
| Able to rearrange items in the collection easily  | Can quickly access any element in the collection |
| Easily expand/shrink a collection                 | Inserts are a challenge                          |
| Difficult to select any element in the collection |                                                  |
| O(1) for insertion and deletion                   | O(n) for insertion and deletion                  |
| O(k) for finding the Kth item                     | O(1) for finding the Kth item                    |
Searching for an item in a linked list is just as complex as with an array

### Linked Lists Using Arrays
Pointers are a convenient way to implement linked lists, but they can also be implemented with two arrays, one for values and one for links.
![[Pasted image 20240528154357.png]]
Sample code for linked list implemented with two arrays:
```cpp
int item[N], next[N];  
	for (j=0; j < N; ++j)
{  
	item[j] = j; // 0 to N-1  
	next[j] = j+1; // 0 links to 1..  
}  
next[N-1] = 0; // make it circular
```
This method is NOT useful if the list needs to expand or shrink over time. For that, node based linked lists are better.
However, with a fixed size problem where the ordering is changeable(by changing values in the second array), then using two arrays is an option.
### Cyclic Linked Lists

One of the links in at least one node points backwards into the list
Follow the links from one node to the next node
List ends if:
	- There is a NULL link or dummy node at the end
	- There is a link back to the first node


### Linked List Sample Code:
```cpp
typedef struct item Item; // Define Item as data type struct item  
typedef struct node* link; // Define link as data type struct node*  
typedef struct node Node; // Define Node as data type struct node  
struct item {int height; int width;};  
struct node {link pNext; Item Data;};  
Item Chair = {42, 16}; //Creates an Item (with height and width)  
Node ChairNode; //Creates a Node  
ChairNode.Data.height = Chair.height; //Set height = 42  
Node DeskNode = {NULL, {36, 60}}; //Create a new Node & set its values  
DeskNode.pNext = &ChairNode; //Link new node from NULL to &ChairNode  
(DeskNode.pNext)->Data.height++; //Equivalent to ChairNode.Data.height++  
// '(DeskNode.pNext)->' means 'dereference what (DeskNode.pNext) is pointing to',  
// which is ChairNode
```

Lists are often used when we don't know in advance how many nodes we will need, so we use dynamic memory allocation to create them.
```cpp
// Using previous typedefs for link and Node  
link p;  
p = (link)malloc(sizeof(*p));  
// Another way to express the same thing  
Node* p;  
p = (Node*)malloc(sizeof(Node));  
```

Making a list of four nodes:
![[Pasted image 20240528145300.png]]
``` cpp title:fourNodes.cpp
Node *pNode, *pHead;  
pNode = (link)malloc(sizeof(Node)); // Make Node 1  
pHead = pNode; // Save location of head of list in  
pHead  
pNode->Data.height = 10; // Populate Node 1  
pNode->pNext = (link)malloc(sizeof(Node)); // Make Node 2  
pNode = pNode->pNext; // Move pNode so it points to Node 2  
pNode->Data.height = 20; // Populate Node 2  
pNode->pNext = (link)malloc(sizeof(Node)); // Make Node 3  
pNode = pNode->pNext; // Move pNode so it points to Node 3  
pNode->Data.height = 30; // Populate Node 3  
pNode->pNext = (link)malloc(sizeof(Node)); // Make Node 4  
pNode = pNode->pNext; // Move pNode so it points to Node 4  
pNode->Data.height = 40; // Populate Node 4  
pNode->pNext = NULL; // End of the list
```

