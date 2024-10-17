# Helpful Videos/Resources 
CRUD: https://www.youtube.com/watch?v=ByuhQncSuAQ
Use Case Diagrams: https://www.youtube.com/watch?v=4emxjxonNRI

### Definition of Use Cases

- A use case is an activity that a system performs in response to a request from a user or another system.
- Use cases are essential for defining functional requirements, allowing for a clear understanding of what the system must do.
- The process of functional decomposition involves breaking down the system into a set of use cases, each representing a specific function.
- Use cases are typically named using a Verb-Noun format, which helps in clearly identifying the action and the object involved.
- Example use cases from the RMO Tradeshow System include: Look up supplier, Enter/update product information, and Enter/Update contact information.

### Importance of Identifying Use Cases

- Identifying use cases is crucial for defining functional requirements, as they form the basis for the list of functions the system needs to perform.
- Use cases help in understanding user interactions with the system, ensuring that all user needs are addressed in the design.
- They serve as a foundation for further analysis, including system design and testing phases.
- Use cases facilitate communication among stakeholders by providing a clear and concise description of system functionality.

# Use Case Techniques
| Technique                     | Description                                                                                          |
| ----------------------------- | ---------------------------------------------------------------------------------------------------- |
| User Goal Technique           | Identifies potential users, classifies them, and gathers their specific goals to create use cases.   |
| Event Decomposition Technique | Focuses on identifying events that require system responses, naming use cases based on these events. |
### User Goal Technique

- The User Goal Technique is a widely used method in the industry for identifying use cases.
- This technique is simple and effective, focusing on the goals of different user types interacting with the system.
- Steps to apply the User Goal Technique include identifying potential users, classifying them by functional role and organizational level, and interviewing them to gather specific goals.
- Example user goals include: Search for item (customer), Add/update product information (marketing manager), and Ship items (shipping personnel).

### Event Decomposition Technique

- The Event Decomposition Technique is a more comprehensive method for identifying use cases by focusing on events that trigger system responses.
- This technique involves identifying events that occur at specific times and places, which the system must respond to.
- Events can be classified into three types: External Events, Temporal Events, and State Events, each driving different system functionalities.
- Examples of external events include customer transactions, while temporal events might involve scheduled reports or notifications.

# Practical Application of Use Cases

### Use Cases in the Ridgeline Mountain Outfitters Case

- The Ridgeline Mountain Outfitters (RMO) case study illustrates the application of use cases in a real-world scenario.
- Use cases help in understanding customer interactions and operational processes within the RMO system.
- Identifying use cases in this context aids in developing a user-friendly system that meets the needs of various stakeholders.

### Developing a Use Case Diagram

- A use case diagram visually represents the interactions between users (actors) and the system, highlighting the use cases involved.
- Diagrams help in simplifying complex systems by providing a clear overview of functionalities and user interactions.
- Key components of a use case diagram include actors, use cases, and the relationships between them.

# Summary and Group Assignments

### Summary of Key Concepts

- Use cases are vital for defining functional requirements and ensuring that user needs are met in system design.
- Two primary techniques for identifying use cases are the User Goal Technique and the Event Decomposition Technique, each with its own strengths.
- Understanding the context of use cases through case studies like RMO enhances the practical application of theoretical concepts.

### Group Formation and Assignment-1

- Group assignments encourage collaboration and deeper understanding of use case identification and modeling.
- Students are expected to apply the techniques learned in class to real-world scenarios, enhancing their analytical skills.

# Event Analysis Techniques

### Tracing a Sequence of Transactions

- Tracing sequences helps identify events related to specific external agents or actors, providing clarity on system interactions.
- This method emphasizes understanding the flow of events, which can reveal hidden requirements or interactions.
- Example: In an e-commerce system, tracing the sequence from a customer browsing to completing a purchase can highlight necessary events like item selection, cart management, and payment processing.
- Historical context: This technique is rooted in systems analysis, where understanding user interactions is crucial for effective design.
- The approach can be visualized through flowcharts that map out each step in the transaction process.

### Perfect Technology Assumption

- The perfect technology assumption posits that analysts should consider events only under ideal conditions, ignoring potential technological failures.
- This assumption allows analysts to focus on essential system responses without being bogged down by system controls that are not user-facing.
- Example: Events like database backups are excluded from initial analysis since they assume a flawless operational environment.
- This principle helps streamline the requirements gathering process, ensuring that only critical user interactions are prioritized.
- It is important to revisit these assumptions during the design phase to incorporate necessary system controls.

# Event Decomposition Technique

### Steps in Event Decomposition

1. Identify external events that require system responses, such as user actions or environmental changes.
2. For each external event, define the corresponding use case that the system must fulfill.
3. Recognize temporal events that necessitate system responses, establishing triggers for use cases.
4. Identify state events, particularly in real-time systems, and define the use cases associated with state changes.
5. Validate that identified events align with the perfect technology assumption, excluding non-essential system controls.

### Benefits of Event Decomposition

- Captures a broader range of events beyond user goals, including temporal and state events.
- Ensures that the focus remains on user-centric functionalities, avoiding unnecessary complexity from system controls.
- Facilitates a clearer understanding of system requirements, leading to more effective design and implementation.
- Helps in identifying potential gaps in the requirements by ensuring all relevant events are considered.
- Provides a structured approach to analyzing system interactions, which can be documented for future reference.

# Use Case Development

### RMO CSMS Project Use Cases

- The RMO CSMS project includes various subsystems, each with specific use cases and actors involved in the processes.
- Example use cases include searching for items, managing customer accounts, and generating reports, each with designated user roles such as customers and representatives.
- Use cases are essential for understanding user interactions and ensuring that system functionalities align with user needs.
- Each subsystem's use cases should be documented clearly to facilitate communication among stakeholders and developers.
- The use case documentation serves as a foundation for further system design and development.

### Validating Use Cases with CRUD Technique

- The CRUD technique is a method for validating use cases by ensuring all necessary operations (Create, Read, Update, Delete) are covered for each domain class.
- Steps include identifying domain classes, verifying use cases for each operation, and ensuring no critical use cases are overlooked.
- Example: For a customer domain class, use cases might include creating a customer account, looking up customer data, and processing account adjustments.
- This technique helps maintain data integrity and ensures that the system can handle all necessary data operations effectively.
- It is crucial for integrated applications to clarify data ownership and responsibilities among different systems.

# Use Case Diagrams

### Understanding Use Case Diagrams

- Use case diagrams are UML models that visually represent use cases and their relationships with actors, aiding in system design and communication.
- Actors represent end users or external systems that interact with the application, while use cases depict the functionalities provided by the system.
- The automation boundary distinguishes between the computerized system and the users, highlighting the scope of the application.
- Example: A use case diagram for an e-commerce system might include actors like customers and administrators, with use cases for browsing products and managing orders.
- Use case diagrams facilitate discussions with stakeholders, ensuring that all user needs are captured and understood.

### Steps to Create Use Case Diagrams

1. Identify stakeholders and users who will benefit from the diagram, ensuring their needs are represented.
2. Determine the specific use cases and actors relevant to each stakeholder's interests.
3. Select and draw the use cases and actors, using appropriate software tools for clarity and professionalism.
4. Name each diagram clearly and provide context on how and when it should be used for stakeholder reviews.