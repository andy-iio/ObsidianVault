### Traversal
Traversal is going through the list by following the links, one node to the next.
If x is a pointer to the first node in a list, t temporarily holds the pointer to the list element, and the last node points to NULL:
```cpp
for (t=x; t != NULL; t=t->pNext)  
Visit(t->item); // Prints the contents
```

### Reversal
