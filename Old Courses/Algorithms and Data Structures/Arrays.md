The name of the array is a pointer to the first element of the array.
```cpp
int array[10];
``` 

Since the name array is a pointer already, there is no need to make a separate pointer.

1D array example:
```cpp
for (i=0;i<9;i++){
	cout << array[i]
} *(array + i) //instead of a seperate pointer, use this format
```

If the name of the array is 'a', then ``` *(a+i) and a[i]``` are equivalent

**Two dimensional arrays:**
Stored in memory one row after another. This is called **row major order**.
Each row can be thought of (and can be used) as if it were a 1D array, the length of a row.
![[Pasted image 20240516131702.png]]

2D array example:
```cpp
for (i=0;i<3;i++){
	for (j=0;j<3;j++){
		cout << a[i][j]
	}
} *(*(array + i) +j) //instead of a seperate pointer, use this format
```

**Array Memory Allocation:**
An array of a fixed size --> ```int table[100]``` (room for 100 ints)
Dynamic memory allocation --> ```int* pTable; //pointer to be filled```
						```pTable = (int)malloc(iTableSize*sizeof(int));```
