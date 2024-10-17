## Key Terms/Concepts

- **Software Quality**: The degree to which a software product meets specified requirements and customer expectations.
- **Quality Assurance (QA)**: Systematic activities providing evidence that software is fit for use, ensuring processes are established and improved.
- **Quality Control (QC)**: The process of comparing product quality against standards and taking action when non-conformance is detected.
- **Verification**: The process of evaluating software to determine if it meets the requirements established before development.
- **Validation**: The process of evaluating software to ensure it meets its intended use.
## Software Quality
Different Views:
- **Consumer's View**: Focuses on quality characteristics related to usage and reliability, emphasizing that the software should be 'fit for use'.
- **Producer's View**: Concentrates on whether the software meets its specified requirements, ensuring that development goals are achieved.
- **Product View**: Pertains to characteristics that influence sales and branding, highlighting the importance of market perception.
## Quality Factors & Criteria
- **Quality Factors**: Behavioral characteristics of a system, such as correctness, reliability, efficiency, and testability.
- **Quality Criteria** Attributes related to software development, for example, modularity as an attribute of software architecture.
- **Quality Models**: Frameworks like ISO 9126 (now ISO 25010) and CMM that provide standards for assessing software quality.

## Quality Assurance
How do you prove the software is fit for use? Through QA!
*"The systematic activities providing evidence of the fitness for use of the total software package"*

**Quality Assurance:** the set of support activities needed to provide adequate confidence that processes are established and continuously improved to ensure products meet specifications and are fit for use. Quality assurance is achieved through establishing guidelines for quality control to ensure the integrity and long life of software.

**Quality Control:** the process where product quality is compared with applicable standards and action is taken when non-conformance is detected

**Auditing:** the inspection/assessment activity that verifies compliance with plans, policies, and procedures

## Software Testing
**Software Testing:** an activity or strategy to identify and manage risk within software. Used to verify that the business requirements were met. **The limitation of testing alone is that by the time testing can be done it's too late to build quality into the product!!!!**
Tests are only as good as the test cases:
- Test cases can be inspected to ensure that all requirements are tested across all possible combinations of inputs and system states
- Still does not guarantee all defects will be discovered
- Includes verification and validation activities

**Verification:** evaluation of software system that helps in determining whether the product of a given development phase satisfies the requirements established before the start of that phase (did we build the product correctly?)

**Validation:** evaluation of software system that helps in determining whether the product meets its intended use (did we build the correct product?)

Software testing has historically been more validation.
- Creating a test product
- Once programming is complete, the system is tested to determine it's functional and operational performance

Its good practice though to combine verification with validation in modern testing processes. Validation is not enough. This can be done through utilizing systematic procedures throughout the SDLC (procedures of review, analysis, testing, etc.)
- TDD (test driven development)

## Failure, Error, Fault, Defect

**Failure:** A failure occurs whenever the external behavior of a system does not conform to the system specification 

**Error:** (manifestation of a fault/defect) An error is the state of a system. An error state could lead to a failure in the absence of any corrective action by the system

**Fault:** A fault is something that possibly could cause an error
- Faulty requirements
- Faulty design
- Faulty coding 

**Defect:** A defect is synonymous with a fault (also known as a bug)
- Can be introduced at any point in the SDLC, no matter the model
- The severity of the defect depends on the impact it has on a user

**Fault/Defect/Bug -> could lead to error -> could lead to failure**
## Software Quality Methodologies:
Any strategy taken to ensure software operates as expected (could be simple or well established practice) (SCRUM and waterfall are methodologies that have their own models and procedures) 
methodologies vs models: methodologies consist of model procedures, e.g. scrum may use relational model. What you use in a methodology is a model. There can be a bunch of models you use in 1 methodology.
### Overview
| Functional Testing      | Description                                               |
| ----------------------- | --------------------------------------------------------- |
| Unit Testing        | Testing individual program units in isolation.            |
| Integration Testing | Testing assembled modules as a larger subsystem.          |
| System Testing      | Testing the complete system for functionality and load.   |
| Acceptance Testing  | Testing to ensure the system meets customer expectations. |
##### Functional Testing:
- Test the system (or parts of the system) against the business requirements
- Usually done in these steps:
	- Unit Testing -> individual program units (procedures, functions, methods in isolation)
	- Integration Testing -> modules are assembled to construct a larger subsystem and tested
	- System Testing -> wide spectrum of testing and functionality, and load
	- Acceptance Testing -> customers expectations for the system
	
The V model represents the development and testing phases in software development. 
![[Pasted image 20241015093037.png]]

##### Non-Functional Testing:
- Tests the operation of the system (speed, capacity, volume, reliability, etc.)
	**TYPES:**
	- Performance Testing
	- Usability Testing
	- Reliability Testing
	- Vulnerability/Security Testing

## Problem-Solving Steps

To effectively conduct software testing, follow these steps:

1. **Define Requirements**: Clearly outline what the software is supposed to do.
2. **Develop Test Cases**: Create test cases that cover all requirements and possible input combinations.
3. **Execute Tests**: Run the test cases in a controlled environment.
4. **Record Results**: Document the outcomes of each test case, noting any failures.
5. **Analyze Failures**: Investigate any failures to determine their cause (fault, error, defect).
6. **Report Findings**: Communicate results to stakeholders and suggest improvements.
7. **Iterate**: Refine the software based on feedback and retest as necessary.

**Tips**: Ensure that test cases are comprehensive and consider edge cases to avoid missing potential defects.