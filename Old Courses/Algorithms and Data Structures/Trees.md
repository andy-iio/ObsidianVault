like a linked list but with 2 pointers (left and right)
### Uses of Trees
- Filesystems (folders of sub folders)

### Tree ADT Terminology
NODE: also called a vertex, is a simple object (ex. Struct) that can have a name and other associated information
EDGE: a connection between nodes
PATH: a list of nodes (successive nodes form a path)
TREE: collection of *nodes* and *edges* that satisfies certain requirements
		- To be a tree, there must be **one** path connecting any **two** nodes
		- If more than one path (or no path) exists between some pair of nodes, then we have a graph 
		- A disjoint set of trees is called a **forest**

Tree, graph, forest: 
![[Pasted image 20240702142146.png]]


ROOTED TREE: a tree in which we designate one node as the root
			- any node is the root of a subtree consisting of it and the nodes below
			 ![[Pasted image 20240702144220.png]]

NON-ROOTED TREE: called a free tree - does not have an obvious root 
			![[Pasted image 20240702144249.png]]

PARENT NODES: Every node (except the root) has exactly one node above it, called its parent node
CHILDREN NODES: The nodes directly below a node are called it's children nodes
LEAVES / TERMINAL NODES: Nodes without children
![[Pasted image 20240702144508.png]]



ORDERED TREE: 
Sometimes the way the children of each node are ordered (to the left or right of the parent) is important. If this is the case, its called an ordered tree.
Example below: left side is always smaller than parent, right side is always larger
![[Pasted image 20240702144619.png]]


### Binary Trees

##### M-ary Trees
In some applications, each parent must have a specific number of children, Eg: M
In that case the tree is called an M-ary tree
Example: all the parents in the image below have 3 children (called a 3-ary of ternary tree)
![[Pasted image 20240702143356.png]]

EXTERNAL NODES: Sometimes we define a special external node (or just a NULL pointer) as a place holder for children not yet present. This is sometimes shown as a square box, or not shown
![[Pasted image 20240702144904.png]]

BINARY TREES: An ordered tree consisting of two types of nodes: 
- Internal nodes -> having 1 or 2 children (black dots in image)
- Leaves -> with no children (white dots on image)
 ![[Pasted image 20240702145059.png]]
Two options to draw a binary tree - show nulls(squares) or don't show the nulls

Left & Right Children: 
we refer to subtrees as the left child and right child of each parent in a binary tree. Subtrees include everything on the right and left side of the parent.

![[Pasted image 20240702143600.png]]


### Binary Tree Implementation in C
A binary tree node (struct) consists of data and two links to the left and right subtrees
	- this is similar to the linked list nodes we've seen
	![[Pasted image 20240702145425.png]]
The C code of a tree node and root could look like this: 
``` cpp
typedef struct TreeNode* link;

struct TreeNode {

  Item msg;  // the data
  link pLeft;  // left subtree
  link pRight;  // right subtree

};

link  root;    // create pointer to root
```

### Binary Trees - Doubly Linked
With only 2 links for each node we can go down to children but not up to parents, but like a doubly linked list you can add another link back to the parent if this is important.

### Full Binary Tree
A full binary tree is when all levels until the last have two children
How many **nodes** are there in a full binary tree? 
Full binary tree with 3 levels as an example:
- 1 root + 2 internal children = 3 internal nodes
- 4 leaves
In General A full n level tree has:
- 2n-1 leaves
- 2n-1-1 internal nodes
![[Pasted image 20240702145927.png]]
How many **levels** (n) in general are in a binary tree with N nodes? 
- Full tree: N=2n so at least n=log2N levels
- Unbalanced tree: at most N levels -> it can have between logN and N levels
 ![[Pasted image 20240702150227.png]]
 
  ### Traversing binary Trees
A binary tree is defined recursively, and so are all algorithms for operating on it
The most basic tree operation is traversal (Visiting every node and performing some operation, such as printing the node contents, or comparing to see if a search value is found)

When we used recursion with linked-lists there were only two options for the recursive process:
- Process the node, then follow the link (e.g., print in forward order)
- Follow the link, then process the node (e.g., print in reverse order)

With trees we have three options for the order in which we visit and process nodes
The three ways you can traverse the tree are:
**Preorder** - Process the node, visit the left subtree, then visit the right subtree (parent first) -> Print parent, then left, then right
In image below, would print -> E-D-B-A-C-H-F-G

**Inorder** - Visit the left subtree, then process the node, then visit the right subtree (left to right) -> print left, then parent, then right
In image below, would print-> A-B-C-D-E-F-G-H

**Postorder** - Visit the left subtree, visit the right subtree, then process the node (children first) -> print left, then right, then parent
In image below, would print -> A-C-B-D-G-F-H-E

For understanding, let's trace the call sequence for the traversal of a tree
Let's assume that *visit() prints the name of the node

![[Pasted image 20240702151324.png]]

### Code
PREORDER TRAVERSAL:

```cpp
// This recursive function takes a link to a tree as
// an argument and calls function visit() for each node.
// This version performs preorder traversal.

void traverse(link h, void (*visit)(link))
{

  if ( h == NULL ) return;  // fell off a leaf
  (*visit)(h);  // process parent first
  traverse(h->pLeft, visit);  // visit left subtree
  traverse(h->pRight,visit);  // visit right subtree
  return;  // that's it!
}
```

INORDER TRAVERSAL:
```cpp
// This recursive function takes a link to a tree as
// an argument and calls function visit() for each node.
// This version performs inorder traversal.

void traverse(link h, void (*visit)(link))
{
  if ( h == NULL ) return;  // fell off a leaf
  traverse(h->pLeft, visit);  // visit left subtree
  (*visit)(h);  // then process parent
  traverse(h->pRight,visit);  // visit right subtree
  return;  // that's it!
}
```

POSTORDER TRAVERSAL:
```cpp
// This recursive function takes a link to a tree as
// an argument and calls function visit() for each node.
// This version performs postorder traversal.

void traverse(link h, void (*visit)(link))
{
  if ( h == NULL ) return;  // fell off a leaf
  traverse(h->pLeft, visit);  // visit left subtree
  traverse(h->pRight,visit);  // visit right subtree
  (*visit)(h);  // then process parent
  return;  // that’s it!
}
```

Useful Utility Functions:

1. Count total nodes in a tree (recursively)
```cpp
// Recursively count the TOTAL number of nodes in a tree
int count(link h) {
  if (h == NULL) return(0);
  return(count(h->pLeft) + count(h->pRight) + 1);
}
```

2. determine height (excluding root) of the tree
```cpp
int height(link h) {
  int iLeftH, iRightH;

  if (h == NULL) return(-1);
  iLeftH = height(h->pLeft);
  iRightH = height(h->pRight); 

  if (iLeftH > iRightH) {
    return(iLeftH + 1);
  }

  else {
    return(iRightH + 1);
  }
}
```
![[Pasted image 20240702152459.png]]

pre-> 12-6-4-5-62-24-13-74-71
inorder-> 4-5-6-12-13-24-62-71-74
post-> 5-4-6-13-24-71-74-62-12


### Binary Search Trees
helpful video: 
https://youtube.com/watch?v=Gt2yBZAhsGM

![[Pasted image 20240702152926.png]]
#### Binary Search Tree Traversal
- keys in the left subtree are smaller, and keys in the right subtree are larger
- so, if we do an inorder traversal of a BST, we will process the keys in sorted order (because inorder traversal is left-parent-right recursivly)

##### Binary Search Tree Code - Inorder Traversal:
Here is code to print a BST in sorted order, using inorder traversal.  
Note – The existence of a char array szKey is assumed in the Item structure
```cpp
//Remember: Inorder traversal pattern is left (child) then center (parent) then right (child), recursively
void BSTPrint(link h){
  if (h == NULL) return;  // reached leaf
  BSTPrint(h->pLeft);  // left
  printf("Key: %s\n", h->Item.szKey);  // center
  BSTPrint(h->pRight);  // right
  return;
}
```

##### Binary Search Tree Code - Tree Node:
```cpp
#include <stdlib.h>
#include "Item.h"  // defines 'Item' structure

typedef struct BSTNode* link; //pointer to BSTNode
struct BSTNode { Item item; link pLeft, pRight; }; //defines the structure
static Item NullItem = {}; //children of leaf nodes, bc leaf nodes have no children
static link head;  // 'head' points to root (private var)

// NEW() function creates a new tree node using malloc()
link NEW(Item item, link left, link right) {
  link pNew = (link)malloc(sizeof(*pNew));
  pNew->item = item;
  pNew->pLeft= left;
  pNew->pRight = right;
  return(pNew);
}
```

##### Binary Search Tree Code - Search:
```cpp
// Create an empty Binary Search Tree
void BSTInit(void) {
  head = NEW(NullItem, NULL, NULL); // start with empty
}

// Search for a key in the BST (using szKey in struct Item)
Item BSTSearch(link h, char *szSearchKey) {
  int rc;
  if (h == NULL) return(NullItem); // Got to end & not found
  rc = strcmp(szSearchKey,h->msg.buff);
  if (rc == 0) return(h->msg);// Found it
  if (rc < 0) return(BSTSearch(h->pLeft,szSearchKey);
  else return(BSTSearch(h->pRight,szSearchKey);
}

Item Search(char *szKey) { return(BSTSearch(head,szKey); }
```
Search() simply calls BSTSearch() without  need for 'head' (a private variable) so that it can be called from main().

strcmp()
-If rc = 0 then the two strings are equal, found the Node with the matching key
-If rc < 0 then the first string szSearchKey is less than h->msg.buff (so search LEFT subtree)
-If rc > 0 then the first string szSearchKey is greater than h->msg.buff (so search RIGHT subtree)

Note: The Nodes 'Item' structure may contain more information than is in the key itself. For example we could be searching medical records (i.e. all info in the 'Item' member of a Node) by the search key 'Name' (a member of Item). So searching for a key, and finding it, gives us more/other useful information.
##### Binary Search Tree Code - Insert:
```cpp
// Insert a key in the BST. Uses szKey as before

link BSTInsert(link h, Item item) {
  int rc;
  if (h == NULL) return(NEW(item,NULL,NULL));  // insert pt
  rc = strcmp(item.buff, h->msg.buff);   // Go left or right?
  if (rc < 0) {
    h->pLeft = BSTInsert(h->pLeft, item);
  } else {
    h->pRight = BSTInsert(h->pRight, item);
  }

  return(h);    // pointer to (new/existing) child
}    // passed up to parent, assigned in the if block

void Insert(Item item)
{  
  head = BSTInsert(head, item);
}
```
Insert() calls BSTInsert() without need for head so it can be called from main() –> returns a pointer to the inserted node (so that parent nodes pLeft or pRight pointers can point to it)  

BSTInsert goes left or right depending on the result of the strcmp()

Once it reaches the end of the tree (i.e. leaf node where h\==pNull) then it inserts the new Item

##### BST Search Example
Here is a successful search for the key 'H':
We go right at the root (since H is larger than A), left at S, and so on
![[Pasted image 20240709143419.png]]

Here is an unsuccessful search for M:
![[Pasted image 20240709143511.png]]
If it were present it would be to the left of N, but instead we find a null link.

Here we insert M in its proper spot by allocating a new node for it, and replacing the left link of N with a pointer to the M node:
![[Pasted image 20240709143549.png]]
