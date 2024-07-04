
### Terminology

A double-ended queue is known as a deque, and is pronounced "deck"  
Deque is sometimes written as dequeue in older material but is generally not used anymore due to the confusion with the dequeue verb (to pop from a queue) A deque is an ADT.
It is a queue in which nodes can be added or removed from either end.  
### Operations
Operations are:  
- addFront(), addBack()  
- removeFront(), removeBack()  
- isEmpty(), size(), init()

![[Pasted image 20240606134437.png]]
One side is the "front", and the other is the "back". It doesn't matter which side you choose for each.

### DLL Implementation

Assuming the Deque is implemented as DLL, draw the resulting deque after the following operations:  
addFront('g');  -> g
addBack('w');  -> gw
addBack('t');   -> gwt
addFront('q');  ->qgwt
addFront('p');  ->pqgwt
addBack('m');  -> pqgwtm
removeFront(); -> qgwtm  -> p popped
removeBack();  -> qgwt -> m popped

![[Pasted image 20240606134805.png]]

What is the Big O order of the operations?  