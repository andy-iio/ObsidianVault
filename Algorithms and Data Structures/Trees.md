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
![[Pasted image 20240702152926.png]]
#### Binary Search Tree Traversal
- keys in the left subtree are smaller, and keys in the right subtree are larger
- so, if we do an inorder traversal of a BST, we will process the keys in sorted order (because inorder traversal is left-parent-right recursivly)

LAST SLIDE = #40