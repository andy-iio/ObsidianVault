## Key Terms/Concepts

- **Unit Testing**: A software testing method where individual units or components of a software are tested in isolation to ensure they function correctly.
- **Integration Testing**: A phase in software testing where individual units are combined and tested as a group to ensure they work together properly.
- **Coupling**: The degree of interdependence between software modules; lower coupling is preferred to reduce complexity and errors.
- **Dynamic Testing**: A testing method where the software is executed and its behavior is observed to validate its functionality.
- **Static Testing**: A testing method that involves reviewing the code without executing it to find defects.
## Unit Testing: 
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

### Why Unit Test?? 
- **Reduce costs:** The further bugs get the most it will cost to fix them, so finding them early is important
- **Early Defect Detection**: Identifies defects early in the development process, reducing costs associated with fixing them later.
- **Facilitates Refactoring**: Makes it easier to restructure code without introducing new bugs.
- **Improves Code Quality**: Ensures that individual components function correctly, leading to a more reliable overall system.
*Unit testing is important, but just unit testing does not guarantee the final product will be perfect*

### Types of Unit Testing
##### Static Unit Testing (manually testing)
- Code is examined over all possible behaviors that might arise during run time
- Code of each unit is validated against requirements of the unit by reviewing the code
##### Dynamic Unit Testing
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
- **MSTest**: A testing framework for C# that supports unit testing and integration testing, allowing developers to write and execute tests easily.
- **JUnit**: A widely used testing framework for Java applications, similar to MSTest.
- **NUnit**: A testing framework for .NET applications, providing similar functionalities as MSTest.

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

## Integration Testing
Unit testing tests individual program units, whereas in integration testing, modules/units are assembled to construct a larger subsystem and tested
### Coupling
Coupling refers to the degree of inter-relationship or dependency between modules
Highly coupled program units usually have **more** errors. Looser coupling minimizes unit interdependence and therefore minimizes software risk

Coupling can be minimized by:
- Minimize the number of parameters between units
- Avoid passing complex data structures
- Avoid the use of global variables
- Make sure each module performs a specific task
	- If it performs more than one specific task, create another module

### Advantages of Integration Testing
- Defects are detected early (it is easier to fix defect when detected early)
- Get earlier feedback on the health and acceptability of the individual modules and on the overall system
- The scheduling of defect fixes can be flexible, it can overlap with development

## Granularity of Integration Testing
Integration testing is performed at different levels of granularity.

**Intra-System Testing:** A form of testing that constitutes low-level integration testing with the objective of combining modules together to build a cohesive system

**Inter-System Testing:** A high level testing phase which requires interfacing independently tested systems

**Pairwise Testing:** In pairwise integration, only two interconnected (directly) systems in an overall system are tested at a time. The purpose of pairwise testing is to ensure that two systems under consideration can function together, assuming that the other systems within the overall environment behave as expected

## Approaches to Integration Testing:
| Approach                                                  | Description                                                                                                     |
| --------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| [[Week 2 - Unit & Integration Tests#Top-Down\|Top-down]]  | Testing starts from the topmost module, using stubs for lower-level modules that are not yet developed.         |
| [[Week 2 - Unit & Integration Tests#Top-Down\|Bottom-up]] | Testing begins with the lower-level modules, using drivers for higher-level modules that are not yet developed. |
| [[Week 2 - Unit & Integration Tests#Top-Down\|Sandwich]]  | A hybrid approach that combines both top-down and bottom-up testing methodologies.                              |
| [[Week 2 - Unit & Integration Tests#Top-Down\|Big-Bang]]  | All components are integrated and tested as a single unit after unit and integration testing.                   |
### Top-Down
- Follows the structural flow of applications 
- Unavailable or undeveloped modules are substituted by stubs
- Testing is done starting with the topmost module in the hierarchy
- Two types: Breadth-First and Depth-First

**Merits of Top-down Methodology**  
• Early exposure to architecture defects  
• It outlines the working of an application as a whole in early stages and helps in early disclosure of design defects  
• The main control points are tested early  

**Demerits of Top-down Methodology**  
• Significant modules are tested late in the cycle  
• It can be quite challenging to write test conditions  
• The stub is not a perfect implementation of the related Module. It just simulates the data flow between the two modules
##### Breadth-First
Test Case 1: Module L and Module O will be integrated and tested  
Test Case 2: Module L, O and P will be integrated and tested  
Test Case 3: Module L, O, P and R will be integrated and tested  
Test Case 4: Module L, O, P, R and OS will be integrated and tested ...and so on (including all modules level by level)
![[Pasted image 20241015095151.png]]

##### Depth First
Test Case1: Module L and Module O will be integrated and tested  
Test Case2: Module L, O and OS will be integrated and tested  
Test Case3: Module L, O, OS,P will be integrated and tested  
Test Case4: Module L, O, OS, P, CP will be integrated and tested ....and so on
![[Pasted image 20241015095254.png]]

### Bottom-Up
Modules at bottom layer are integrated and tested first and then sequentially other modules are integrated as we move up.  
Unavailable or undeveloped modules are replaced by drivers.

**The Merits of Bottom-up Methodology**  
• It’s easier to create test conditions in the bottom-up approach  
• Leads to testing of critical modules or functionality at an early stage. This helps in early discovery of errors  
• Interface defects are detected at an early stage  

**Demerits of Bottom-Up Methodology**  
• Drivers are more difficult to write than stubs  
• Design defects are caught in the later stage

Test Case1: Integration and testing of modules M1 and D4  
Test Case2: Integration and testing of Modules M1, D4 and M2  
Test Case3: Integration and testing of Modules D2,D4,M1 and M2  
Test Case4: Integration and testing of Modules D2,D4,M1,M2 and D3  
Test Case5: Integration and testing of Modules D1, D2,D4,M1,M2 and D3
![[Pasted image 20241015095509.png]]

### Sandwich
Combination of top- down and bottom-up methodology. Also known as Hybrid Testing  
Stubs and drivers are used for incomplete or undeveloped modules.
**Advantages**  
- Combines the best practices of both top-down and bottom-up  
- Beneficial for larger projects  
**Disadvantages**  
- Higher Testing Costs (Time)  
- Not always efficient when modules have high levels of coupling

Test Case1: Test A,G,H,I  
Test Case2: Test G, X, and Y  
Test Case3: Test H, Z  
Test Case 4: Test I,A  
Test Case5: Test A, G, H, I, X, Y, and Z  
![[Pasted image 20241015095720.png]]

### Big-Bang
Big bang integration testing is a testing approach where all components or modules are integrated and tested as a single unit.  
- Typical performed after multiple levels of unit and integration testing  
- Before system testing and acceptance testing