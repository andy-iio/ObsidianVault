Quick find is very fast for find, but slow for union operations (proportional to N items). eg, the worst case -> for a problem that requires M unions with N objects, the solution will require M * N instructions. lets edit
### Quick Find
- Each object starts off in its own set
- As connections are made, change the set of one object to that of the other (does not matter which)
- Then, to see if two objects are connected, check if they have the same set name / number

**Example:** 
Each object as its own set, so there are 18 sets to start:
![[Pasted image 20240527211502.png]]

We learn (in pairs) that:
 Elephant, panda, tiger and bunny are connected
 The lion, bear, and dragon make another set
 Lobster and bat make a third set
 All other critters remain individuals
![[Pasted image 20240527211635.png]]
Tiger is connected to bunny, because they are in the "Elephant" set  
Dragon is not connected to panda, because they are in different sets  
This demonstrates FIND is very quick

Now, tiger and bear are connected. To join the two sets, all objects in the lion set are now members of the elephant set:
![[Pasted image 20240527211847.png]]

