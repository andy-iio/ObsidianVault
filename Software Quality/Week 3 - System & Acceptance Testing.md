## Key Concepts

| Theory/Model                | Description                                                                                                           |
| --------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| Cyclomatic Complexity Model | Defines the cyclomatic complexity (M) as M = E - N + 2P, where E is edges, N is nodes, and P is connected components. |
| Control Flow Graph Theory   | Utilizes graphs to represent the flow of control in a program, aiding in understanding and testing software behavior. |
## Software Complexity

### Introduction to Software Complexity

- Software complexity refers to the intricacy of software systems, which can affect maintainability, reliability, and testability.
- Complexity can arise from various factors, including the number of components, interactions, and the algorithms used.
- Understanding complexity is crucial for effective testing and quality assurance.
- High complexity often leads to increased risk of defects and challenges in testing.
- Tools and methodologies exist to measure and manage software complexity.

## Graphs in Computer Science

- Graphs are mathematical structures used to model pairwise relations between objects.
- A graph consists of nodes (vertices) and edges (connections), which can represent various entities and their relationships.
- Weighted graphs have edges with associated values, representing costs or distances.
- A graph is said to be connected if there is a path to get to every node from any other node (You can hop through neighboring nodes)
- A graph is said to be disconnected if there are islands of nodes that are inaccessible from other nodes  
- Graph theory is applied in numerous computer science problems, such as network routing and optimization.
![[Pasted image 20241015100954.png]]

### Control Flow Graphs (CFG) in Quality Assurance

#### Definition and Purpose of Control Flow Graphs

- Control Flow Graphs are used to represent the flow of control in a program.
- Nodes in a CFG represent implementation statements, while edges represent the flow of control between these statements.
- CFGs help in visualizing the execution paths and identifying potential areas for testing.
- They are essential for path testing, which aims to ensure that all possible execution paths are tested.

### Path Testing

- Path testing involves creating test cases to ensure that every path in the CFG is executed at least once.
- Each conditional statement in the program should be tested in both true and false states.
- For example, with two IF statements, there are four possible paths to consider.
- The challenge arises with larger CFGs, where the number of paths can become overwhelming, especially with loops.
- It is not necessary to test every path; instead, focus on linearly independent paths.
![[Pasted image 20241015101211.png]]

## Cyclomatic Complexity

### Definition and Calculation

- Cyclomatic complexity (CC) is a software metric used to measure the complexity of a program based on its control flow graph.
- It is calculated using the formula: M = E - N + 2P, where E is the number of edges, N is the number of nodes, and P is the number of connected components.
- For a single program, P is typically 1, simplifying the calculation.
- A higher cyclomatic complexity indicates a more complex program, which may require more extensive testing.
![[Pasted image 20241015101320.png]]

### Importance of Cyclomatic Complexity

- Cyclomatic complexity helps determine the minimum number of test cases needed for basis path testing.
- It provides an upper limit on the number of linearly independent paths that need to be tested.
- By focusing on these paths, testers can ensure that all conditions in the CFG are evaluated for both true and false outcomes. (known as [[#Basis Path Testing]])
- This approach significantly reduces the number of test cases required while maintaining effective coverage.

### Practical Application of Cyclomatic Complexity

- Cyclomatic complexity can be used to estimate the number of test cases required for effective testing.
- It aids in identifying complex areas of code that may require more rigorous testing.
- By analyzing cyclomatic complexity, teams can prioritize testing efforts and allocate resources efficiently.
- Tools are available to automatically calculate cyclomatic complexity, aiding in continuous integration and testing processes.
## Linearly Independent Paths

A set of linearly independent paths of a CFG is:  
- A subset of the set of all paths of the CFG with a condition:  
	- Condition: Each path in the set (of linearly independent paths) must differ from all other paths in the set (of linearly independent paths) by at least one edge
- Cyclomatic Complexity (M) gives us the upper limit on the number of paths in the set (of linearly independent path) to perform basis path testing  
	- i.e. to obtain complete statement coverage of the CFG, or in other words to exercise every edge in the CFG  
- We only need to create a test case for each path in the set of the linearly independent paths (thereby drastically reducing the number of test cases required to satisfactorily test a method)
### Creating Linearly Independent Paths

- To create a set of linearly independent paths, start with any path in the CFG.
- Continue adding paths that introduce new edges until the number of paths equals the cyclomatic complexity (M).
- Each path must differ from others by at least one edge to be considered linearly independent.
- This method ensures comprehensive testing while minimizing redundancy.

## Basis Path Testing

### Overview of Basis Path Testing

- A given CFG can have different paths in its basis path set (i.e, it can possibly have multiple basis path sets)
- Basis path testing is a white-box testing technique that focuses on executing linearly independent paths.
- The number of paths in the basis path set will always be less than or equal to the cyclomatic complexity.
- This method ensures that all edges in the CFG are exercised, providing complete statement coverage.
- Different basis path sets can exist for the same CFG, but they will not exceed the cyclomatic complexity.


## Software Testing Levels

### Types of Software Testing

- ***Unit Testing***: Focuses on testing individual components or modules of a software system, ensuring that each part functions correctly in isolation. Unit tests are fully automated, easy to develop using a framework (MSTest), execute quicky, and provide good test coverage. 
- ***Integration Testing***: Tests the interaction between integrated modules to ensure they work together as expected.
- ***System Testing***: Evaluates the complete and integrated software system to verify that it meets specified requirements and functions correctly in various scenarios.
- ***Acceptance Testing***: Conducted to determine if the system meets the acceptance criteria set by the customer, ensuring it fulfills user and business requirements.
- Each testing level serves a distinct purpose and is crucial for delivering high-quality software.

### Importance of System Testing

- System testing is essential because individual components may work correctly in isolation but fail when integrated due to external dependencies and interactions.
- It assesses the system's functionality and performance under various conditions, including database connectivity and file I/O operations.
- System testing encompasses a wide range of testing types, including functional and load testing, to ensure comprehensive coverage.
- The V-model of software development emphasizes the importance of system testing as part of the development and testing phases.
- Effective system testing can identify issues that may not be apparent during unit or integration testing, leading to a more robust final product.
- It ensures that the entire application functions as intended, providing confidence in the software's reliability and performance.

### System Tests VS Unit tests

| System Tests                                                                                                                                                                                                                                                                                                                                                                                 | Unit Tests                                                                                                                                                                                                                                                                                                                         |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| *Does our entire system work as  <br>expected?*<br><br>Take a long time to run  <br>Require deployment of SUT and:  <br>• Configuration  <br>• Databases  <br>• Remote services  <br>• Permissions<br>Hard to cover paths in the logic from  <br>many application layers away  <br>Difficult to simulate infrequent errors  <br>Cannot run if dependencies are broken  <br>or in development | *Did we build our classes right?  <br>Did we implement their methods  <br>correctly?*<br><br>Very fast  <br>Have **none** of those concerns:  <br>• Tests run in memory  <br>• Instantiate the class under test  <br>• Mock/stub its dependencies, if any<br>Can cover every path in the application's  <br>business logic<br><br> |

## Acceptance Testing

### Types of Acceptance Testing

- ****User Acceptance Testing (UAT)****: Conducted by end-users to ensure the system meets their requirements and expectations.
- ****Business Acceptance Testing (BAT)****: Focuses on verifying that the software meets business requirements and can handle business scenarios effectively.
- Acceptance testing is formal and aims to validate that the system satisfies its acceptance criteria before deployment.
- Test cases for acceptance testing are designed to mimic real-world business processes, ensuring practical applicability.
- Both UAT and BAT are critical for confirming that the software is ready for release and meets the needs of stakeholders.

### Objectives and Execution of Acceptance Testing

- The primary objectives of acceptance testing include confirming that the system meets agreed-upon criteria, identifying discrepancies, and determining readiness for deployment.
- Acceptance criteria encompass various attributes such as functional correctness, data integrity, usability, and performance.
- Acceptance tests are executed in phases, starting with basic test cases followed by more complex scenarios, ensuring a thorough evaluation.
- Developers collaborate with customers during acceptance testing to address any issues and ensure the system aligns with expectations.
- The acceptance test report summarizes the outcomes, leading to decisions on whether to accept the system as delivered, after modifications, or not at all.

## Summary and Conclusion

### Key Takeaways

- Understanding cyclomatic complexity is crucial for identifying complex modules that require additional testing.
- System testing is vital for ensuring that integrated components function correctly in real-world scenarios.
- Acceptance testing validates that the software meets user and business requirements, ensuring readiness for deployment.
- A structured approach to testing at various levels enhances software quality and reduces the likelihood of defects.
- Regular assessment and execution of testing strategies contribute to the overall success of software development projects.