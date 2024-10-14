##### Unit Testing: 
Unit testing is testing individual program units, such as procedures, functions, or methods in *isolation.*

Unit tests test small program units or modules of a software system  
- Often individual classes or small components such as methods  

Unit tests are:  
- Fully automated  
- Easy to develop using a framework such as MSTest  
- Execute quickly  
- Provide good test coverage

However, unit testing is never enough on its own. Just because the units work well individually does not mean they will work together correctly. We need to test modules working in combination. See [[Week 2 - Unit & Integration Tests#Integration Testing|Integration Testing]].

Example: Is the add function providing the correct results?
![[Pasted image 20240910171450.png]]
Two options for unit testing: 
- Use the function within the application and then test it with the application (but this option defeats the purpose of test driven development, because you have to wait until the application is finished to test)
- Write code to test the function before it goes to production (this code is called the unit test)

##### Why Unit Test?? 
- Identify defects early on
- Reduce costs -> the further bugs get the most it will cost to fix them, so finding them early is important
- Facilitates refactoring (restructuring) of code -> identify mistakes, make changes to improve
- Improves overall quality
*Unit testing is important, but just unit testing does not guarantee the final product will be perfect though*

##### Types of Unit Testing
1. Static Unit Testing (manually testing)
	- Code is examined over all possible behaviors that might arise during run time
	- Code of each unit is validated against requirements of the unit by reviewing the code
2. Dynamic Unit Testing
	- A program unit is executed, and its outcomes observed
	- One observes some representative program behavior, and can form some conclusions about the quality of the system
	- Units can invoke other units (methods can invoke other methods)
	- The emulation of the units in turn called by the UUT are called stubs (stubs are dummy programs)
	- The test driver and the stubs together are called scaffolding
	- The low-level design document provides guidance for selection of input test data
	![[Pasted image 20240910180250.png]]

### Unit Testing Tools

Many frameworks available, (JUnit is for Java applications, NUnit is for C#)
MSTest, JUnit, and NUnit are dynamic testing tools
- Requires the execution of the program
- Can be used for integration testing, regression testing, and system testing as well by acting as the test driver

##### MSTest Assertion Methods:
IsTrue()
IsFalse()
AreEqual()
AreNotEqual()
IsNull()
and more.. 

##### Test Project Structure
- Project containing the test should be named: ProjectBeingTested.Tests
	- This is a common standard naming in this course, but companies can have their own standard naming. Should just be consistent and clear.
- Give TestClass a name that groups the tests within it. eg. ArithmeticTests
- Use explanatory names for the test methods, to make it easier to identify which tests are failing. For example: ```public void Add_3_4_Return7() ```

##### AAA (Arrange, Act, Assert)\
- A pattern for arranging and formatting code in unit test methods
- Each method should group these sections, separated by blank lines
- **Arrange** all necessary preconditions and inputs
- **Act** on the object or methods under the test
- **Assert** that the expected results have occurred
``` cpp
[TestMethod]  
public void Add_3_4_Return7()  
{  
//Arrange  
int num1 = 3;  
int num2 = 4;  
int result;  
//Act  
result = Methods.AreEqual(num1, num2);  
//Assert  
Assert.AreEqual(7, result);  
}
```

### Integration Testing
Unit testing tests individual program units, whereas in integration testing, modules/units are assembled to construct a larger subsystem and tested

##### Coupling
Coupling refers to the degree of inter-relationship or dependency between modules
Highly coupled program units usually have **more** errors. Looser coupling minimizes unit interdependence and therefore minimizes software risk

Coupling can be minimized by:
- Minimize the number of parameters between units
- Avoid passing complex data structures
- Avoid the use of global variables
- Make sure each module performs a specific task
	- If it performs more than one specific task, create another mo1dule

##### Advantages of Integration Testing
- Defects are detected early (it is easier to fix defect when detected early)
- Get earlier feedback on the health and acceptability of the individual modules and on the overall system
- The scheduling of defect fixes can be flexible, it can overlap with development

##### Granularity of Integration Testing
Integration testing is performed at different levels of granularity.

**Intra-System Testing:** A form of testing that constitutes low-level integration testing with the objective of combining modules together to build a cohesive system

**Inter-System Testing:** A high level testing phase which requires interfacing independently tested systems

**Pairwise Testing:** In pairwise integration, only two interconnected (directly) systems in an overall system are tested at a time. The purpose of pairwise testing is to ensure that two systems under consideration can function together, assuming that the other systems within the overall environment behave as expected

##### Approaches to Integration Testing:
- [[Week 2 - Unit & Integration Tests#Top-Down|Top-down]]
- [[Week 2 - Unit & Integration Tests#Top-Down|Bottom-up]]
- [[Week 2 - Unit & Integration Tests#Top-Down|Sandwich]]
- [[Week 2 - Unit & Integration Tests#Top-Down|Big-Bang]]

##### Top-Down
- Follows the structural flow of applications 
- Unavailable or undeveloped modules are substituted by stubs
- Testing is done starting with the topmost module in the hierarchy
- Two types: Breadth-First and Depth-First
##### Bottom-Up
##### Sandwich
##### Big-Bang