UNION: joins two sets 
FIND: if the two objects are in the same set

Two union find algorithms are [[Quick Find]] and [[Quick Union]].

Sample code, traversing the tree to find an items parent, then joining two sets with union:
```cpp
int x=7 //the thing to find the parent of
parent[i] = i //initilize
int find(x){
	if parent[x] != x{ //if the parent is not itself
		return find(parent[x]) //then recursivly call thefind function
	}else{
		return x; //when parent is found, return it
	}
}
int y = 5 //the item to connect x with
int union(x,y){
	parent[find(y)] = find(x) //finds the root of y and set the parent of one to be the parent of the other as well
}
```
Watch this video, its very helpful.
<iframe title="Union Find in 5 minutes — Data Structures &amp; Algorithms" src="https://www.youtube.com/embed/ayW5B2W9hfo?feature=oembed" height="113" width="200" allowfullscreen="" allow="fullscreen" style="aspect-ratio: 1.76991 / 1; width: 100%; height: 100%;"></iframe>

Union(x,y) - Unions the groups containing x and y
![[Pasted image 20240529170230.png]]


