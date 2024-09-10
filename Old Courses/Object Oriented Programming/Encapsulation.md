Encapsulation - the process of combining related data member and functions into a single unit called a class. 
This is to prevent the access to the data directly, the access to them is provided through the functions of the class. 
So this data can not be used by functions outside of the class. 
terms to know: 
**Data hiding**

### Important properties of Encapsulation

1. **Data Protection:** Encapsulation protects the internal state of an object by keeping its data members private. Access to and modification of these data members is restricted to the class’s public methods, ensuring controlled and secure data manipulation.
2. **Information Hiding:** Encapsulation hides the internal implementation details of a class from external code. Only the public interface of the class is accessible, providing abstraction and simplifying the usage of the class while allowing the internal implementation to be modified without impacting external code.

### Features of Encapsulation:
1. Cannot access any function from the class directly. We need an object to access that function that is using the member variables of that class. 
2. The function which we are making inside the class must use only member variables, only then it is called _encapsulation_.
3. If we don’t make a function inside the class which is using the member variable of the class then we don’t call it encapsulation.
4. Encapsulation improves readability, maintainability, and security by grouping data and methods together.
5. It helps to control the modification of our data members.

Encapsulation leads to [[data abstraction]].
