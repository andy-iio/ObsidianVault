### New Operator
Obtains memory from the operating system and returns a pointer to its starting point

### Delete Operator
To ensure safe and efficient use of memory, the new operator is matched by a corresponding delete operator that returns memory to the operating system

### Class Destructor
Destructor is a special function that is called automatically when an object is destroyed. A destructor has the same name as the class name preceded by a tilde(~)

```cpp
class ClassName {
	public:
		~ClassName( ) {
		}
	};
```

### Function Overriding
If a derived class defines the same function (e.g print()) as defined in its base class, this is known as function overriding

```cpp
#include <iostream>
using namespace std;

class Shape {
public:
	void print(){
		cout << "Shape:Base class";
	}
};

class Rectangle :public Shape {
public:
	void print(){
		cout << "Rectangle:Derived class";
	}
};

class Circle :public Shape {
public:
	void print(){
		cout << "Circle:Derived class";
	}
};

int main(){
	Shape shape;
	Rectangle rec;
	Circle circ;

	shape.print();
	rec.print();
	circ.print();
}

// OUTPUT:
// Shape: Base class
// Rectangle: Derived class
// Circle: Derived class
```

### Virtual Function

**ONLY necessary when using a base class pointer to call the override functions.** Functions that are declared with a virtual keyword in base class will ensure that the correct function is called for an object of a derived class, regardless of the type of reference (or pointer) used for function call

#### Example:
```cpp
#include <iostream>
using namespace std;

class Shape {
public:
	virtual void print() { //need virtual to override, without it it just uses the base class function every time
		cout << "Shape:Base class\n";
	}
};

class Rectangle :public Shape {
public:
	void print() {
		cout << "Rectangle:Derived class\n";
	}
};

class Circle :public Shape {
public:
	void print() {
		cout << "Circle:Derived class\n";
	}
};

int main() {
	//useful for when you want to declare only one pointer, and then can assign the value of it at runtime
	//eg. ask the user if they want to print circle or rectangle
	Shape s, *p;
	Rectangle r;
	Circle c;
	p = &s;
	p->print();
	p = &r;
	p->print();
	p = &c;
	p->print();
}
```

### Polymorphism 
Polymorphism means "many forms", and it happens when you have many classes that are related to each other by inheritance. This can be used to allow an object to behave differently in different conditions. 
![[Pasted image 20240703133312.png]]

### Abstract Class
An abstract class in C++ is a class that has at least one pure virtual function (A function that does not have a definition). Any class inherits for the abstract class must provide a definition for the pure virtual function; otherwise, the derived class would become an abstract class itself. Notice that you cannot create an instance of an abstract class.

Pure virtual function -> a function that does not have a body
```cpp
//this is a pure virtual class, meaning its an abstract class
class Shape{
public:
	virtual void draw() = 0;
};
```

Concrete class -> a class that does not have any pure virtual functions
```cpp
//this is a concrete class
class Rectangle: public Shape {
public:
	void draw() override {
		cout << "draw a rectangle" << endl
	}
};
```

You can create a pointer of an abstract class
```cpp
Shape* shape;
```

BUT you cannot create an instance of an abstract class
```cpp
// you can't do this
Shape shape;
```

### Copy Constructor
A copy constructor is a special member function that initializes an object using another object of the same class. A copy constructor has the following general function prototype:
```cpp
ClassName(ClassName & object){

}
```
For each class, a default copy constructor is provided. This default copy constructor copies all the member field values. This works well if the fields are values BUT may not be what you want for fields that point to dynamically allocated memory

**Shallow Copy:**
Shallow copies all of the member field values.
![[Pasted image 20240703134657.png]]

**Deep Copy**
A deep copy copies all fields and makes sure your field has their own memory address and copies of dynamically allocated memory pointed to by the fields.
![[Pasted image 20240703134726.png]]

### Assignment Operator
The assignment operator is used to replace the data of an existing object with some other object's data.
```cpp
Person p1(100);
Person p2(55); //p2 is already created
p2 = p1; //= is the assignment operator
```

The copy constructor can be used if a new object has to be created before the copying can happen.
```cpp
Person p1(100);
Person p2 = p1; //p2 is not yet created, so copy constructor is used
```