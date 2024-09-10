A constructor is a special type of member function that is called automatically when an object is created. The constructor is used to initialize objects.

- constructors **must** have the same name as the class name
- constructors don't have a return type, as they don't return anything. Don't need to write void though
- a constructor is automatically called when an object is created
- a default constructor is provided if you don't write one

```cpp
 class circle {
	//data 
	float radius;
	float area;
	float perimeter;

 public:

	 circle() { //constructor
		 radius = 7;
	 }
}
```

Three types of constructors:

**Default Constructor:**
A constructor with no parameters.

**Parameterized Constructor:**
A constructor with parameters.

**Copy Constructor:**
A constructor that is used to copy data of one object to another object.