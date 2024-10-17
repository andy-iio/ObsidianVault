## Week 1 - SW Quality Methodologies
[[Week 1 - SW Quality Methodologies#Key Terms/Concepts|Key Terms/Concepts]]

[[Week 1 - SW Quality Methodologies#Software Quality|Software Quality]]
- Consumer's View ~quality characteristics related to usage and reliability
- Producer's View ~whether the software meets its specified requirements
- Product View ~sales and branding, market perception.

[[Week 1 - SW Quality Methodologies#Quality Factors & Criteria|Quality Factors & Criteria]]
- Quality Models ~ ISO 9126 (now ISO 25010) and CMM 

[[Week 1 - SW Quality Methodologies#Quality Assurance|Quality Assurance]] ~provide confidence that processes are established and continuously improved
- Quality Control ~compare with standards
- Auditing ~ inspect to verify compliance with policies and procedures

[[Week 1 - SW Quality Methodologies#Software Testing|Software Testing]] ~Testing alone -> by the time testing is done it's too late to build in quality
- Verification ~did we build the product correctly? (satisfies requirements)
- Validation ~did we build the correct product? (meets its intended use)
    
[[Week 1 - SW Quality Methodologies#Failure, Error, Fault, Defect|Failure, Error, Fault, Defect]] ~Fault/Defect/Bug -> could lead to error -> could lead to failure

[[Week 1 - SW Quality Methodologies#Software Quality Methodologies|Software Quality Methodologies]]
	[[Week 1 - SW Quality Methodologies#Overview|Overview]]
		- Functional Testing (unit, integration, system, acceptance)
		- Non-Functional Testing (performance, usability, reliability, vulnerability/security)

[[Week 1 - SW Quality Methodologies#Problem-Solving Steps|Problem-Solving Steps]]
## Week 2 - Unit and Integration Tests
[[Week 2 - Unit & Integration Tests#Key Terms/Concepts|Key Terms/Concepts]]

[[Week 2 - Unit & Integration Tests#Unit Testing|Unit Testing]] ~testing individual program units in *isolation.*
	[[Week 2 - Unit & Integration Tests#Why Unit Test??|Why unit test?]] ~ reduce costs, early defect detect, refactoring, code quality
	[[Week 2 - Unit & Integration Tests#Types of Unit Testing|Types of Unit Testing]]
		[[Week 2 - Unit & Integration Tests#Static Unit Testing (manually testing)|Static Unit Testing]]
		[[Week 2 - Unit & Integration Tests#Dynamic Unit Testing|Dynamic Unit Testing]] ~ Test driver and the stubs together are called scaffolding (stubs are dummy programs)
	[[Week 2 - Unit & Integration Tests#Unit Testing Tools|Unit Testing Tools]] ~MSTest, JUnit, and NUnit
		-MSTest assertion methods
	[[Week 2 - Unit & Integration Tests#Test Project Structure|Test Project Structure]]
	[[Week 2 - Unit & Integration Tests#AAA (Arrange, Act, Assert)|AAA (Arrange, Act, Assert)]]

[[Week 2 - Unit & Integration Tests#Integration Testing|Integration Testing]]
	[[Week 2 - Unit & Integration Tests#Coupling|Coupling]] ~Highly coupled program units usually have **more** errors
	[[Week 2 - Unit & Integration Tests#Advantages of Integration Testing|Advantages of Integration Testing]]
	[[Week 2 - Unit & Integration Tests#Granularity of Integration Testing|Granularity of Integration Testing]]
		- Intra-system testing
		- Inter-system testing
		- Pairwise testing
	 [[Week 2 - Unit & Integration Tests#Approaches to Integration Testing|Approaches to Integration Testing]]
		[[Week 2 - Unit & Integration Tests#Top-Down|Top-Down]]
		[[Week 2 - Unit & Integration Tests#Breadth-First|Breadth-First]]
		[[Week 2 - Unit & Integration Tests#Depth First|Depth First]]
		[[Week 2 - Unit & Integration Tests#Bottom-Up|Bottom-Up]]
		[[Week 2 - Unit & Integration Tests#Sandwich|Sandwich]]
		[[Week 2 - Unit & Integration Tests#Big-Bang|Big Bang]]

## Week 3 - System & Acceptance Testing

[[Week 3 - System & Acceptance Testing#Key Concepts|Key Concepts]]

[[Week 3 - System & Acceptance Testing#Software Complexity|Software Complexity]]
	[[Week 3 - System & Acceptance Testing#Introduction to Software Complexity|Introduction to Software Complexity]]
	
[[Week 3 - System & Acceptance Testing#Graphs in Computer Science|Graphs in Computer Science]]
	[[Week 3 - System & Acceptance Testing#Control Flow Graphs (CFG) in Quality Assurance|Control Flow Graphs (CFG) in Quality Assurance]]
			[[Week 3 - System & Acceptance Testing#Definition and Purpose of Control Flow Graphs|Definition and Purpose of Control Flow Graphs]]
			 [[Week 3 - System & Acceptance Testing#Path Testing|Path Testing]]
			 
 [[Week 3 - System & Acceptance Testing#Cyclomatic Complexity|Cyclomatic Complexity]]
		  [[Week 3 - System & Acceptance Testing#Definition and Calculation|Definition and Calculation]]
		  [[Week 3 - System & Acceptance Testing#Importance of Cyclomatic Complexity|Importance of Cyclomatic Complexity]]
		  [[Week 3 - System & Acceptance Testing#Definition and Importance of Cyclomatic Complexity|Definition and Importance of Cyclomatic Complexity]]
		  [[Week 3 - System & Acceptance Testing#Practical Application of Cyclomatic Complexity|Practical Application of Cyclomatic Complexity]]
		  [[Week 3 - System & Acceptance Testing#Conclusions on Cyclomatic Complexity|Conclusions on Cyclomatic Complexity]]
		  
[[Week 3 - System & Acceptance Testing#Linearly Independent Paths|Linearly Independent Paths]]
		  [[Week 3 - System & Acceptance Testing#Creating Linearly Independent Paths|Creating Linearly Independent Paths]]
[[Week 3 - System & Acceptance Testing#Basis Path Testing|Basis Path Testing]]
	[[Week 3 - System & Acceptance Testing#Overview of Basis Path Testing|Overview of Basis Path Testing]]

[[Week 3 - System & Acceptance Testing#Software Testing Levels|Software Testing Levels]]
	[[Week 3 - System & Acceptance Testing#Types of Software Testing|Types of Software Testing]]
	[[Week 3 - System & Acceptance Testing#Importance of System Testing|Importance of System Testing]]
	[[Week 3 - System & Acceptance Testing#System Tests VS Unit tests|System Tests VS Unit tests]]

[[Week 3 - System & Acceptance Testing#Acceptance Testing|Acceptance Testing]]
	[[Week 3 - System & Acceptance Testing#Types of Acceptance Testing|Types of Acceptance Testing]]
	[[Week 3 - System & Acceptance Testing#Objectives and Execution of Acceptance Testing|Objectives and Execution of Acceptance Testing]]

[[Week 3 - System & Acceptance Testing#Summary and Conclusion|Summary and Conclusion]]
[[Week 3 - System & Acceptance Testing#Key Takeaways|Key Takeaways]]

## Week 4 - Project Risk Assessment
[[Week 4 - Project Risk Assessment#Risk Assessment|Risk Assessment]] ~Risk = Frequency x Cost

	[[Week 4 - Project Risk Assessment#Risk Terminology|Risk Terminology]]
	- Threat ~external force such as hacking, physical intrusion, or sabotage.
	- Vulnerability ~Internal weakness within a system, bugs, poor configuration, missing patches.
	- Risk ~Combination of threat and vulnerability    
	[[Week 4 - Project Risk Assessment#Importance of Risk Assessment|Importance of Risk Assessment]] 
	
	[[Week 4 - Project Risk Assessment#Risk Assessment Methodologies|Risk Assessment Methodologies]]
		[[Week 4 - Project Risk Assessment#Qualitative Risk Assessment|Qualitative Risk Assessment]] ~subjective judgment and past experiences to assess risks
		[[Week 4 - Project Risk Assessment#Quantitative Risk Assessment|Quantitative Risk Assessment]] ~objective numerical ratings to assess risks
		
	[[Week 4 - Project Risk Assessment#Identifying and Weighing Risk Attributes|Identifying and Weighing Risk Attributes]]
		[[Week 4 - Project Risk Assessment#Major Risk Attributes|Major Risk Attributes]] ~project size/ structure, exp with tech, technology complexity
		
    [[Week 4 - Project Risk Assessment#Risk Mitigation Strategies|Risk Mitigation Strategies]]
	    [[Week 4 - Project Risk Assessment#Overview of Risk Mitigation|Overview Of Risk Mitigation]]
	    [[Week 4 - Project Risk Assessment#Testing and Risk|Testing and Risk]]
	    [[Week 4 - Project Risk Assessment#Selecting a Risk Mitigation Strategy|Selecting a Risk Mitigation Strategy]]
	    
	[[Week 4 - Project Risk Assessment#Communicating Risk to Stakeholders|Communicating Risk to Stakeholders]]
		[[Week 4 - Project Risk Assessment#Effective Communication Strategies|Effective Communication Strategies]]
		[[Week 4 - Project Risk Assessment#Importance of Stakeholder Engagement|Importance of Stakeholder Engagement]]
			
	[[Week 4 - Project Risk Assessment#Understanding Risk Attributes|Understanding Risk Attributes]]
		[[Week 4 - Project Risk Assessment#Key Risk Attributes|Key Risk Attributes]]
		[[Week 4 - Project Risk Assessment#Attributes Increasing Likelihood of Risks|Attributes Increasing Likelihood of Risks]]
		[[Week 4 - Project Risk Assessment#Attributes Increasing Impact of Risks|Attributes Increasing Impact of Risks]]
		
	[[Week 4 - Project Risk Assessment#Communicating Risks to Stakeholders|Communicating Risks to Stakeholders]]
		[[Week 4 - Project Risk Assessment#Importance of Communication|Importance of Communication]]
		[[Week 4 - Project Risk Assessment#Effective Risk Communication Strategies|Effective Risk Communication Strategies]] ~ Categorize risks, clear language, visualization tools
		