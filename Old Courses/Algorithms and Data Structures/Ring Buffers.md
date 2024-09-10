**BUFFERS:** In computer science, a **data buffer** is a region of memory used to store data temporarily while it is being moved from one place to another.

### **Basic Explanation of a Ring Buffer**:
![[Pasted image 20240604144007.png]]

A circular buffer first starts out empty and has a set length.
![[Pasted image 20240604143825.png]]
Assume a 1 is added to the buffer (the starting location is not important b/c it is circular)
![[Pasted image 20240604144023.png]]
Then assume that two more elements are added to the circular buffer — 2 & 3 — which get put after 1
![[Pasted image 20240604144229.png]]
If two elements are removed, the two oldest values inside of the circular buffer would be removed. Circular buffers use FIFO (_first in, first out_) logic. In the example, 1 & 2 were the first to enter the circular buffer, they are the first to be removed, leaving 3 inside of the buffer.
![[Pasted image 20240604144342.png]]
Now assume the buffer is full:
![[Pasted image 20240604144446.png]]
A property of the circular buffer is that when it is full and a subsequent write is performed, then it starts overwriting the oldest data. In the current example, two more elements — A & B — are added and they _overwrite_ the 3 & 4
![[Pasted image 20240604144531.png]]
Alternatively, the routines that manage the buffer could prevent overwriting the data and return an error or raise an exception. Whether or not data is overwritten is up to the semantics of the buffer routines or the application using the circular buffer.
### Uses
The useful property of a circular buffer is that it does not need to have its elements shuffled around when one is consumed. (If a non-circular buffer were used then it would be necessary to shift all elements when one is consumed.) In other words, the circular buffer is well-suited as a FIFO (_first in, first out_) buffer while a standard, non-circular buffer is well suited as a LIFO (_last in, first out_) buffer.

Examples of where a ring buffer would be useful:
 A port on a computer is continuously receiving data  
	 It has limited memory to store this data so it stores only the latest data.  
 A "black box" recorder can only hold n minutes of data  
	 So it only holds the last n minutes  
 Commands are sent to the Mars Rover  
	 At times, commands come faster than they can be carried out  
	 Memory is limited  

 A ring buffer is a data structure often used in communication systems  
 Used to hold the "most recent" n events until they are needed


![[Pasted image 20240604141048.png]]

### Sample Code
```cpp
#define SIZE 10  
static int head; // oldest  
static int tail; // most recent  
static int iRing[SIZE];  
void InitRing(void) {  
head = tail = -1;  
}  
int IsRingEmpty(void) {  
return(head == tail);  
}  
int IsRingFull(void) {  
return(head ==((tail+1) % SIZE));  
} 
head ==((tail+1) % SIZE)  
head == ((5+1) % 10)  
head == 6  
//True  So the ring is full

int WriteToRing(int iNew) {  
if (!IsRingFull()) {  
tail++;  
if (tail >= SIZE) {  
tail = 0;  
}  
iRing[tail] = iNew;  
return(0);  
}  
return(1); // ring full  
}  
int ReadFromRing(int* pOut) {  
if (!IsRingEmpty()) {  
*pOut = iRing[head++];  
if (head >= SIZE){  
head = 0;  
}  
return(0);  
}  
return(1); // ring empty  
}
```