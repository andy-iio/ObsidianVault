A class in C++ is a user-defined type declared with keyword class that has data and functions as its members whose access is governed by the three [[Access Specifiers|access specifiers]] private, protected or public. By default, its members are private. (this differs from struct members which are public by default)

A class is like a datatype, no memory is allocated until an instance of the class is declared.

Classes in C++ are preferred over structures.

To initialize objects -->[[Classes Constructor]]

```cpp
#include <iostream>
using namespace std;

 class circle {

	//data 
	float radius;
	float area;
	float perimeter;

public:
	//functions
	void getRadius() {
		cout << "Enter the value of the radius: ";
		cin >> radius;
	}

	void calculateArea() {
		area = 3.14 * radius * radius;
	}

	void calculatePerimeter() {
		perimeter = 3.14 * 2 * radius;
	}

	void print() {
		cout << "The area is " << area << "\n";
		cout << "The perimeter is " << perimeter << "\n";
	}
};

int main() {
	//creating two objects, c1 and c2
	class circle c1, c2; //here is when memory is allocated

	//first object
	c1.getRadius();
	c1.calculateArea();
	c1.calculatePerimeter();
	c1.print();

	//second object
	c2.getRadius();
	c2.calculateArea();
	c2.calculatePerimeter();
	c2.print();
}
```