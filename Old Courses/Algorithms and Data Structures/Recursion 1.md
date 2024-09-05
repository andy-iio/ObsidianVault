  
A recursive algorithm is one that solves a problem by solving one or more smaller instances of the same problem. 
Recursive functions often mirror recursive definitions in mathematics.

In C we implement recursive algorithms by using recursive functions. 
A recursive function is one that calls itself.
```cpp
int RecursiveAdd(int iNumber) {  
	int nextNumber;  
	if (iNumber <= 1) {  
		return(1);  
	} else {  
		nextNumber = iNumber - 1;  
		return( iNumber + RecursiveAdd(nextNumber));  
	}  
}
```

### Recurrence Relation
A recurrence relation defines a function (of non-negative integers) in terms of it's own value on smaller integers. eg. factorials: N! = N * (N-1)!, for N >= 1, 0! = 1
We can write this in c using recursion: 
```cpp
int factorial(int N){  
	if (N == 0){  
		return(1); 
	}  
	return(N*factorial(N-1));  
}  
```
You could also write it as a simple loop instead of a recursive function:
```cpp
for (t=1, i=1; i<=N; i++){  
	t *= i;  
}
```
We can ALWAYS express a recursive algorithm in a non-recursive way.
So if we don't need recursion - why use it? 
- allows complex algorithms to be written compactly
- allows the implementation to mirror the problem being solved
	- less chance for errors
	- clear, easy to understand implementation (debatable)
	
Keep in mind: 
- its easy to write inefficient recursive functions
- each recursive call uses up resources so need to watch the 'depth' of recursion
- do not use it often, its rarely used in practice

RULES for writing recursive functions:
1. Termination condition that directly computes result
2. Calls itself with a SMALLER argument

Here is an example of a recursive function that violates a rule:
```cpp
int puzzle( int N ) {  
	if (N == 1) {  
		return(1);  
	}  
	if (N%2 == 0){  
		return(puzzle(N/2));  
	}  
	else return(puzzle(3N+1));  //calls itself with a LARGER amount
}
```

### Recursion & Linked Lists
for linked lists, we could write this recursive function to count the number of nodes in the list:
```cpp 
//count the number of nodes in the list:
int count(link x) {  
	if (x == NULL){  //reached the end of the list
		return(0);  
	}  
	return(1 + count(x->pNext));  
}
```

A recursive function that deletes the node with item V:
```cpp
link deleteR(link parent, link child, Item v) {  
	if (child == NULL){  
		return(NULL);  
	}  
	if (child->Data.sid == v.sid) {  //once the correct node is found, delete
		parent->pNext = child->pNext;  
		free(child);  
		deleteR(parent, parent->pNext, v);  
	}  
	else {  
		deleteR(child, child->pNext, v);  //if not found, call function again with the next node but same v value
	}
}
```

A recursive function that traverses the list:
```cpp
// Execute a function on each node in order  
void traverse(link h, void* visit(link)) {  
	if (h == NULL) {  
		return;  
	}  
	(*visit)(h); // calls 'visit( )' before recursive call  
	traverse(h->pNext, visit);  //visit() is called before the recursive traverse() call so nodes are visited in-order
}
```