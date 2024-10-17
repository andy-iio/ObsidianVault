# Helpful Videos/Resources 
Data Flow Diagrams: https://www.youtube.com/watch?v=6VGTvgaJllM
Context Diagrams: https://www.youtube.com/watch?v=LINsqN2NLLQ

# Overview

- Traditional analysis focuses on structured methodologies for gathering and defining system requirements.
- Understanding traditional models is important for systems analysts, especially when dealing with older systems.
- Traditional models are often easier for stakeholders to understand, facilitating communication.
### Traditional vs Object-Oriented Approaches

- Object-oriented approaches utilize [[Week 3 - Use cases|use cases]] and class diagrams, while traditional approaches rely on ERDs and [[#Data Flow Diagrams (DFD's)]].
- Use cases describe user interactions, whereas DFDs focus on data movement and processing within the system.

![[Pasted image 20241016151454.png]]
![[Pasted image 20241016151540.png]]

# Data Flow Diagrams (DFD's)

- DFDs visually represent the flow of data within a system, highlighting inputs, outputs, processes, and data storage.
- They are designed to be easily understood by end users and stakeholders with minimal training.
- DFDs can be decomposed into multiple levels, providing varying degrees of detail about system processes.
- The main components of a DFD include processes, data stores, data flows, and external entities.

![[Pasted image 20241016152121.png]]

### DFD Symbols and Components

- **Processes**: Represented by squares, indicating actions taken on data.
- **Data Stores**: Shown as open-ended rectangles, representing where data is stored.
- **Data Flows**: Arrows indicating the direction of data movement between processes, stores, and external entities.
- **External Entities**: Squares representing the source or destination of data outside the system

![[Pasted image 20241016151916.png]]

### Context Diagrams and Decomposition

- A context diagram is a DFD that provides the most abstract view of the system, showing all external interactions and data flows. The entire system is represented as one process.
- Decomposing DFDs involves breaking down complex processes into simpler, more detailed diagrams (e.g., Diagram 0, Diagram 1).
- Each DFD fragment corresponds to a specific use case. 

DFD Fragments:
![[Pasted image 20241016152331.png]]
# Ensuring Data Flow Consistency

### Common Data Flow Issues

- **Black Hole**: A process that receives input but produces no output, indicating a potential design flaw.
- **Miracle**: A situation where data appears from nowhere, suggesting missing data sources in the model.
- **Data Flow Rules**: Data must flow through processes and cannot directly return to the same source.

### Examples of Data Flow Issues

- A black hole example could be a process that logs user activity but does not generate any reports or outputs.
- A miracle example might involve a process that generates a report without any input data, indicating a lack of clarity in data sources.
- Ensuring data flow consistency is crucial for accurate system modeling and analysis.

# Stakeholders in System Implementation

### Types of Stakeholders

- **Internal Stakeholders**: Individuals within the organization who are directly involved in the system's implementation and use. Examples include employees, managers, and IT staff.
- **External Stakeholders**: Individuals or groups outside the organization who have an interest in the system's success, such as customers, suppliers, and regulatory bodies.
- **Operational Stakeholders**: Users who regularly interact with the system, providing feedback and insights based on their experiences.
- **Executive Stakeholders**: Individuals who do not directly interact with the system but rely on its outputs for decision-making or have a financial stake in its success.

### Importance of Stakeholder Engagement

- Engaging stakeholders ensures that the system meets the needs and expectations of all parties involved, leading to higher satisfaction and adoption rates.
- Stakeholder feedback can identify potential issues early in the development process, allowing for timely adjustments.
- Understanding the perspectives of different stakeholders can help prioritize features and functionalities based on their importance to the organization.
- Effective communication with stakeholders fosters collaboration and can lead to innovative solutions that might not have been considered otherwise.

# Information-Gathering Techniques

### Common Techniques for Information Gathering

- **Interviews**: Conducting structured or unstructured interviews with users and stakeholders to gather qualitative data about their needs and expectations.
- **Questionnaires**: Distributing surveys to collect quantitative data from a larger audience, allowing for statistical analysis of user needs.
- **Document Review**: Analyzing existing documentation, such as reports and manuals, to understand current processes and requirements.
- **Observation**: Watching users interact with the system in real-time to identify pain points and areas for improvement.
- **Vendor Research**: Investigating potential vendor solutions to understand market offerings and best practices.
- **User Feedback**: Collecting comments and suggestions from active users to inform system enhancements.

### Analyzing Collected Information

- Organizing and categorizing data collected from various sources to identify common themes and requirements.
- Using tools like affinity diagrams to visualize relationships between different pieces of information.
- Prioritizing requirements based on stakeholder feedback and business objectives to ensure alignment with organizational goals.

# Models and Modeling in Systems Analysis

### Types of Models

- **Textual Models**: Written descriptions that outline system requirements and functionalities, often used for documentation purposes.
- **Graphical Models**: Visual representations of system components and their relationships, such as UML diagrams, which enhance understanding and communication.
- **Mathematical Models**: Formulas and algorithms that represent system behaviors and processes, often used in performance analysis.

### Unified Modeling Language (UML)

- UML provides a standardized way to visualize system design, making it easier for teams to communicate and collaborate.
- Prior to UML, different organizations used varied notations, leading to confusion and misinterpretation of diagrams.
- UML includes various diagram types, such as use case diagrams, class diagrams, and activity diagrams, each serving a specific purpose in system design.

### Benefits of Modeling

- **Complexity Reduction**: Models help simplify complex systems by abstracting unnecessary details, making it easier to understand core functionalities.
- **Learning Tool**: The modeling process itself can reveal insights and foster a deeper understanding of system requirements.
- **Documentation**: Models serve as a reference for future maintenance and enhancements, ensuring continuity in system development.
- **Communication**: Models facilitate discussions among team members and stakeholders, ensuring everyone has a shared understanding of the system.

# Use Cases and Their Importance

### Understanding Use Cases

- A **use case** describes a specific interaction between a user (actor) and the system, detailing the system's response to user requests.
- Use cases help define functional requirements, breaking down the system into manageable components for analysis and design.
- Each use case should be named using a **Verb-Noun** format to clearly convey its purpose, such as 'Create Account' or 'Generate Report'.

### Techniques for Identifying Use Cases

- **User Goal Technique**: Focuses on identifying the goals of users to derive relevant use cases, ensuring that user needs are met.
- **Event Decomposition Technique**: Involves identifying events that trigger system responses, leading to a comprehensive list of use cases based on system interactions.

### Validating Use Cases with CRUD

- The **CRUD Technique** (Create, Read, Update, Delete) is used to ensure that all necessary use cases for data management are identified and validated.
- Each use case should correspond to a specific CRUD operation, ensuring that the system can effectively manage data throughout its lifecycle.