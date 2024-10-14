For when you want to look through a collection of items.
Each item has a defined key
GOAL: find items with keys matching a search key
![[Pasted image 20240717130413.png]]

##### Handling Duplicate Keys
Duplicate keys cause problems for most search algorithms
Options for handling duplicates:
- Forbid them
- Create new unique key
- Allow duplicates but write functions to deal with them
- Move duplicates into a secondary data structure

##### Linear Search
- Simplest search algorithm we will see
```cpp
for (j=0; j < nEntries; ++j) {
  if ( list[j] == iTarget )
  return(j);
}
return(-1);
```
![[Pasted image 20240717130626.png]]
##### Big O Analysis for Linear Search

| Worst                                                        | Best                             | Average                                                                                          |
| ------------------------------------------------------------ | -------------------------------- | ------------------------------------------------------------------------------------------------ |
| n items/comparisons none of which match (i.e., not in array) | Find item after first comparison | Depends on probability of key being in collection and if sorted/unsorted – difficult to estimate |
| O(n)                                                         | O(1)                             | n/a                                                                                              |

##### Improving a Linear Search
1. Sort the list so most probable searches appear first
	- Whenever you find an item, move it to top of list

2. Use multithreading
	- Get a second thread to help operate on data faster (e.g. search from two directions)

3. Push some search operations onto a server (or other computer)

4. Pre-load data to reduce wait time

6. Remove the need for the j comparison by placing the value being searched for to end of the list
	- This eliminates the j comparison (1 per loop eliminated)
```cpp
//Dummy value  placed at end of list is called the Sentinel
for (j=0; ~~j <~~ ~~nEntries~~; ++j)
	if ( list[j] == iTarget ) return(j);

//If the returned value of j is the last item, then it was never in the list to begin with
for (j=0; ; ++j)
  if ( list[j] == iTarget ) return(j);
```

##### Symbol Table
The Abstract Data Type for search is called the Symbol Table

**Required Operations:**
Insert() a new item
Return() an item with a given key
Delete() a specific item
Select() the kth smallest (largest) item
Sort() the table (to visit all the items in key order)
Join() two symbol tables
possibly also some housekeeping operations like: Initalize(), IsEmpty(), Destroy(), Copy(), etc.

##### Symbol Table - Performance
Performance depends on data structure used for the implementation
- E.g., sorted/unsorted linked-list, array, tree, etc.

Choose data structure for the implementation to give the most efficient performance for the application
- Mostly search?
	- Fast search is important: Use a binary tree
- Mostly add?
	- Fast insert is important: Use a linked list


##### ADT - Symbol Table
**Client**
- main.c file with the main() function
```cpp
//symbol table client
#include <stdio.h>
#include "Item.h"
#include "SymbolTable.h"

int main(int argc, char *argv[]) {
  int N, maxN = atoi(argv[1]);  // cmd line inputs
  Key key;
  Item item;
  STinit(maxN);

//GetItemInput() and PrintItem() are defined elsewhere
  for (N=0; N < maxN; ++N) {
    if (GetItemInput(&item,&key) == EOF) break;
    //Ensures that inserted items are unique (else next line skipped).
If STsearch(key) != NULLitem then search found the key in the list (NULLitem is at end of list)
    if (STsearch(key) != NULLitem) continue;
    STinsert(item);
  }

  STsort(PrintItem); printf("\n");
  printf("Total keys: %d\n", N);
  printf("Distinct keys: &d\n", STcount());

}
```

**Interface**
- symbolTable.h file
```cpp
//symbol table interface
//can be implemented differently but the input-output characteristics will be the same
void STinit(int);  // max size
void STinsert(item);  // must
Item STsearch(key);  // must
int  STcount(void);  // optional
void STdelete(item);  // optional
Item STselect(int);  // optional
void STsort(void (*visit)(Item));  // optional
```

**Implementation**
- symbolTable.c
- Data structure used (array, linked list, tree, etc) depends on whivh is most efficient for the specific application
- Several data structures we can use for the symbol table implementation
1. Key-Index Search (array based)
2. Binary Search
3. Binary Search Trees
4. Digital Search Trees


### Symbol Table Implementation 1: Key Index Search
- Suppose the keys are unique numbers between 0 and m 
- Algorithm
	- Create an array of size m Items
	- Initialize all entries to a special NULLitem value
	- Insert an item with that has key k at index k in the array
	- Search for key k?
		- Just go to index k
	- Delete key k?
		- Delete item at index k
	![[Pasted image 20240717141424.png]]
##### Key Index Search Performance
![[Pasted image 20240717141812.png]]

##### Sample Code
```cpp
//key index search implementation

#include <stdio.h> // and stdlib, Item.h, SymbolTable.h, etc.

static Item *st; 
static int m = maxKey;
void STinit(int maxN) {
  int i;
  st = malloc( (m+1)*sizeof(Item) );
  //Initialize entries to special NULLitem
  for (i=0; i<=m; ++i) st[i] = NULLitem;  // empty
}
//key() is a utility function that returns index of an item
void STinsert( Item item ) {st[key(item)] = item;}
Item STsearch(Key key) {return st[key(item)]; }
void STdelete(Item item) {st[key(item)] = NULLitem;}¡

int STcount(void) {  // increment count if not NULLitem
  int j, N=0;
  for (j=0; j < m; ++j) if ( st[j] != NULLitem ) N++;
  return(N); 
}

Item STselect(int k) {  // find the kth item in the list
  int j;
  for (j=0; j < m; j++) {
    if (st[j] != NULLitem )  // only count filled entries
    if (k-- == 0) return(st[j]);
  }
}
//visit() function pointer, as seen earlier
void STsort(void (*visit)(Item)) {
  int j;
  for (j=0; j < m; j++) {
    if ( st[j] != NULLitem )
    visit(st[i]); //Doesn't "sort" so much as visits (prints) items in the list in key order
  }
}
```

##### Eager vs Lazy Algorithms
Consider this algorithm to count the items in a Symbol Table:
```cpp
//this is a lazy algorithm
int STcount(void) {
  int j, N=0;
  for (j=0; j < M; ++j)
    if (st[j] != NULLitem) N++;
  return(N);
}
```
Lazy Algorithm: Work is only done (count items) when this function is called

- The alternative is to maintain a variable with the correct count at all times -> increment counter in insert() and decrement it in delete()
	- A lazy algorithm is only more efficient if STcount() is rarely called and the number of keys is small
	- Otherwise an eager algorithm is more efficient

### Symbol Table Implementation 2: Binary Search
- If key not in range first -> last, no match
	- Binary search assumes it has been sorted
- Compare key to item at mid, if:
	- key == mid return index
	- key > mid then search upper half
	- key < mid then search lower half
- Much better performance than a linear search
	- O(log n) vs. O(n)

- But: Requires data to be in a sorted array
	- Keeping the symbol table sorted: O(n2) for inserts / deletes

- This might be okay if:
	-  # of searches  >  # of insertions / deletions
```cpp
//binary search implementation
int BinarySearch(int *array, int num_of_elmts, int key) {  
  int low = 0, high = num_of_elmts-1, mid;  
  while(low <= high) {  
    mid = (low + high)/2;  // Mid of range  
    if(key == array[mid]) return mid;  // found, return index

    if(key > array[mid]) {

      low  = mid + 1;

    } else {  // key < array[mid]  
      high = mid - 1;  
    }

  }  
  return -1;  // not found

}
```
##### Binary Search - Big O Analysis
- What is worst case time?
	- N items none of which match the search key
	- N*(1/2)n=1
	- N=2n à log2(N)=log2(2n) à log2(N)=nlog2(2)
	- log2(2)=1
	- Therefore n=log2(N)
	- So O(n)=log2N comparisons of the search key

log2N comparisons of the search key
N=100         -> log2(100)=7 probes
N=1024       -> log2(1024)=10 probes
N=1 million -> log2(1,000,000)=20 probes

##### Binary Search Interpolated
An interpolation search calculates mid, based on a linear interpolation
![[Pasted image 20240717143137.png]]

Replace the line for computing mid in the code above with
```cpp
m = (array[high] – array[low])/(high – low);

mid = 1/m(key – array[low]) + low;
```

### Symbol Table Implementation 3: Binary Search Trees

##### Performance of BSTs
The performance of algorithms based on BSTs depends on the shape of the tree
- Best case for searching O(log2N) is a balanced tree
![[Pasted image 20240717143414.png]]

- Worst case O(N) is an unbalanced tree
 ![[Pasted image 20240717143430.png]]
- The general case is somewhere in between
![[Pasted image 20240717143454.png]]
Since the tree evolves as keys are inserted, we do not (automatically) control the balance, but we can fix this

Search and Insert cost:
- O(log2N) if tree is balanced
- O(N) if tree is unbalanced

Unfortunately, unbalanced trees are more likely so we need strategies for keeping trees balanced
- We saw self balancing 2-3 Trees in the BST class
