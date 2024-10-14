### Software Quality
Different Views:
Consumer's View -> Quality characteristics that deal with the usage and reliability of the product (fit for use)
Producers View -> Does the software meet its requirements?
Product View -> Characteristics that pertain to sales and branding

### Quality Factors & Criteria
Quality Factor -> behavioral characteristics of a system (e.g, correctness, reliability, efficiency, testability)
Quality Criterion -> an attribute of a quality factor that is related to software development
Quality Models -> (e.g ISO 25010, CMM, etc.)

### Quality Assurance
How do you prove the software is fit for use? Through QA!
*"The systematic activities providing evidence of the fitness for use of the total software package"*

Quality assurance is achieved through establishing guidelines for quality control to ensure the integrity and long life of software.

**Quality Assurance:** the set of support activities needed to provide adequate confidence that processes are established and continuously improved to ensure products meet specifications and are fit for use

**Quality Control:** the process where product quality is compared with applicable standards and action is taken when non-conformance is detected

**Auditing:** the inspection/assessment activity that verifies compliance with plans, policies, and procedures

### Software Testing
**Software Testing:** an activity or strategy to identify and manage risk within software. Used to verify that the business requirements were met. ***The limitation of testing alone is that by the time testing can be done it's too late to build quality into the product!!!!***
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

### Failure, Error, Fault, Defect

**Failure:** A failure occurs whenever the external behavior of a system does not conform to the system specification 

**Error:** (manifestation of a fault/defect) An error is the state of a system. An error state could lead to a failure in the absence of any corrective action by the system

**Fault:** A fault is something that possibly could cause an error
- Faulty requirements
- Faulty design
- Faulty coding 

**Defect:** A defect is synonymous with a fault (also known as a bug)
- Can be introduced at any point in the SDLC, no matter the model
- The severity of the defect depends on the impact it has on a user

***Fault/Defect/Bug -> could lead to error -> could lead to failure***


### Software Quality Methodologies:
Any strategy taken to ensure software operates as expected (could be simple or well established practice) (SCRUM and waterfall are methodologies that have their own models and procedures) 
methodologies vs models: methodologies consist of model procedures, e.g. scrum may use relational model. What you use in a methodology is a model. There can be a bunch of models you use in 1 methodology.

**Functional Testing:**
- Test the system (or parts of the system) against the business requirements
- Usually done in these steps:
	- Unit Testing -> individual program units (procedures, functions, methods in isolation)
	- Integration Testing -> modules are assembled to construct a larger subsystem and tested
	- System Testing -> wide spectrum of testing and functionality, and load
	- Acceptance Testing -> customers expectations for the system
	
The V Model: 

![[Pasted image 20240910112814.png]]

**Non-Functional Testing:**
- Tests the operation of the system (speed, capacity, volume, reliability, etc.)
TYPES:
- Performance Testing
- Usability Testing
- Reliability Testing
- Vulnerability/Security Testing