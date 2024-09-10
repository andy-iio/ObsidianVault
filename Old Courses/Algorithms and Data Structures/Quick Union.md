Quick union speeds up the union operation at the expense of find.

UNION: To form a union: Value at the index of the second object is set to the index of the first object such that the second object 'points' to the first  
Exception: The root object in the set points to itself

### Example
The skunk set:
![[Pasted image 20240529173457.png]] 
All members of the skunk set point to another member of the set, except the root (skunk) which points to itself.
Following the pointers eventually leads to the root (skunk)

So, for FIND:
Follows penguins pointers to the root
Follows lions pointers to the root
Both roots are skunk, so they are in the same set. 
Having to follow pointer to the root means that FIND is SLOW. (time is proportional to the depth of the tree)

For UNION:
To join two sets, eg. if tiger and lobster need to be connected, make one of the ROOT nodes (elephant or skunk) point to the ROOT node of the other set. Since only one pointer needs to change for a UNION, it is very FAST. (constant time for each union once roots are found)
![[Pasted image 20240529174112.png]]

### Worst Case for Quick Union:
Straight line tree:
![[Pasted image 20240529174455.png]]
To mitigate this problem, we can use **Weighted Quick Union**.
This algorithm addresses the problem of tall (straight line) trees that make quick union slow for finds. It works like quick union, except we join to the root that makes the tree as short as possible.
Short trees reduce the time find takes.