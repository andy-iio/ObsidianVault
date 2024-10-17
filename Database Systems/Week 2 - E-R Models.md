# Helpful Videos/Resources:
https://www.youtube.com/watch?v=xsg9BDiwiJE&t=4s
https://www.lucidchart.com/pages/er-diagrams#:~:text=ER%20diagrams%20are%20used%20to,in%20a%20physical%20data%20model.)
# Definitions

- Entity: A person, place, object, event, or concept.
- Strong Entity: Exists independently and has a unique identifier.
- Weak Entity: Dependent on a strong entity and does not have a unique identifier.
- Required Attribute: Must have a value for every instance.
- Optional Attribute: May not have a value for every instance.
- Composite Attribute: An attribute that has meaningful component parts.
- Multivalued Attribute: May take on more than one value for a given instance.
- Derived Attribute: Values calculated from related attributes.
- Cardinality Types: One-to-One, One-to-Many, Many-to-Many.
- E-R Model: A conceptual representation of data.
- Business Rules: Statements that define or constrain aspects of the business.
- Naming Guidelines: Names should be meaningful, unique, and readable.
- Identifiers: Attributes that uniquely identify instances of an entity type.

# E-R Model Constructs
[[#**Entities**|Entities]] | [[#**Relationships**|Relationships]] | [[#**Attributes** | Attributes]]
## **Entities**

- **Entity:** A person, a place, an object, an event, or a concept in the user environment about which the organization wishes to maintain data.
- **Entity Type**: A collection of similar entities that share common properties, typically represented as a table in a database (strong, weak , associative). 
- **Entity Instance**: Represents a single occurrence of an entity type, such as a specific person, place, event, concept, or object. Often corresponds to a **==row==** in a database table.
- **Diagram**: Entities are usually represented as rectangles in E-R diagrams (E-R = Entity-Relationship)
- For example, In a library database, 'Book' is an entity type, and 'Harry Potter' is an entity instance.
- An entity ==SHOULD== be:
	- An object that will have many instances in the database  
	- An object that will be composed of multiple attributes  
	- An object that we are trying to model
- An entity ==SHOULD NOT== be:
	- A user of the database system
	- An output of the database system (e.g. report)
### Strong vs. Weak Entities

- **Strong Entity**: Exists independently and has a unique identifier, represented with a single underline in diagrams.
- **Weak Entity**: Dependent on a strong entity, lacks a unique identifier, and is represented with double lines.
- **Identifying Relationship**: Links strong entities to weak entities, ensuring the weak entity's existence is tied to the strong entity.
- **Example**: In a university database, 'Course' can be a strong entity, while 'Enrollment' can be a weak entity dependent on 'Student'.

![[Pasted image 20241016131130.png]]

### Guidelines for Naming and Defining Entities

- **Definitions**: Should describe unique characteristics and clarify what constitutes the entity, be explicit about what is and is not the entity, when an entity is created or destroyed, changes to other entities, and be a history that should be kept
- **Naming**: Use singular nouns, be specific to the organization, be concise, and maintain naming consistency across all diagrams.

## **Relationships**

- **Relationship Instance**: A specific link between two or more entities, often represented by primary key-foreign key relationships in tables.
- **Relationship Type**: Defines the category of relationship between entity types, such as one-to-one, one-to-many, or many-to-many.
- **Relationship Cardinality**: Specifies the number of instances of one entity that can or must be associated with each instance of another entity.
- **Relationship Degrees:** Specifies the number of entity types involved
- **Associative Entity:** A special entity that is also a relationship
- **Diagram**: Relationships are depicted as diamonds shown as lines in E-R diagrams.
- For example, A 'Borrow' relationship between 'Member' and 'Book' entities in a library system.

### Cardinality of Relationships

- Cardinality defines the number of instances of one entity that can be associated with instances of another entity.
- Types of cardinality include One-to-One, One-to-Many, and Many-to-Many relationships.
- Example: In a One-to-Many relationship, one department can have many employees, but each employee belongs to only one department.

### Degree of Relationships

- The degree of a relationship refers to the number of entity types involved. It can be Unary (one entity type), Binary (two entity types), or Ternary (three entity types).
- Example: A binary relationship might involve `Employees` and `Departments`, while a ternary relationship could involve `Students`, `Courses`, and `Professors`.

### Cardinality Constraints

- Cardinality constraints specify the minimum and maximum number of instances of one entity that can be associated with another.
- Minimum cardinality can be optional (zero) or mandatory (one or more).
- Example: A patient must have at least one medical history recorded (mandatory), while an employee may not be assigned to any projects (optional).

### Associative Entities

- An associative entity is a combination of a relationship and an entity that has its own attributes.
- Associative entities are used when a relationship has attributes that need to be stored, or when the relationship itself has meaning independent of the entities.
- Example: A `Certificate` entity that links `Employees` and `Courses` with an attribute for `Date Completed`.
### Examples of Relationships

|   |   |   |
|---|---|---|
|Relationship Type|Description|Example|
|Unary|One entity related to itself|An employee supervises another employee|
|Binary|Two different entities|An employee works in a department|
|Ternary|Three different entities|A student enrolls in a course taught by a professor|

## **Attributes**

- **Definition**: Attributes are properties or characteristics of an entity or relationship type, corresponding to a **==field==** in a table.
- **Types of Attributes**: Includes required vs. optional, simple vs. composite, single-valued vs. multi-valued, stored vs. derived.
- **Example**: For a 'Book' entity, attributes are 'Title', 'Author', and 'Publication Year'.

![[Pasted image 20241016125014.png]]

### Attributes Classifications

- ****Required vs. Optional Attributes****: Required attributes must have values for every instance, while optional attributes may not.
- ****Simple vs. Composite Attributes****: Simple attributes cannot be divided further, while composite attributes can be broken down into smaller parts.
- ****Single-Valued vs. Multi-Valued Attributes****: Single-valued attributes hold one value, whereas multi-valued attributes can hold multiple values.
- ****Stored vs. Derived Attributes****: Stored attributes are saved in the database, while derived attributes are calculated from other data.
### Composite Attributes

- A composite attribute is an attribute that consists of multiple meaningful component parts. For example, an address can be broken down into street, city, state, and zip code.
- Composite attributes help in organizing data more effectively by allowing for structured storage of related information.
- Example: An employee's address can be represented as a composite attribute with components like `Street`, `City`, `State`, and `Zip Code`.

### Multi-valued and Derived Attributes

- Multi-valued attributes can hold multiple values for a single entity instance. For instance, an employee may possess multiple skills.
- Derived attributes are not stored directly in the database but can be calculated from other attributes. For example, `Years Employed` can be derived from the `Date Employed` and the current date.
- Example: An employee entity may have a multi-valued attribute `Skills` and a derived attribute `Years Employed`.

### Identifiers (Keys)

- An identifier (or key) is an attribute or a combination of attributes that uniquely identifies an instance of an entity type.
- Simple identifiers consist of a single attribute, while composite identifiers are made up of multiple attributes.
- Candidate identifiers are potential identifiers that meet the criteria for uniqueness.

### Naming and Defining Attributes

- Attributes should be named using singular nouns or noun phrases and must be unique.
- A standard naming format should be followed, such as `[Entity Type Name { [Qualifier] }]`.
- When defining attributes, it is important to clarify what is included in the attribute's value, its source, and whether it can change.


# Business Rules

Business rules are statements that define or constrain aspects of the business, derived from policies, events, functions, and procedures. They assert business structure and control/influence business behavior.
They should be expressed in familiar terms to end users and written in short, concise phrases.
Business rules are eventually automated through software to ensure consistency and compliance.
For example: A rule stating that 'A library book cannot be checked out before today' 

### Characteristics of Good Business Rules

- **Declarative**: Clearly states what is required without detailing how to achieve it. (what, not how)
- **Precise**: Must have a clear, agreed-upon meaning to avoid ambiguity.
- **Atomic**: Each rule should express a single idea or requirement.
- **Consistent**: Rules should be consistent both internally and externally.
- **Business-oriented**: Must be understandable by business stakeholders, not just technical people.

### Examples of Business Rules

- **Library Example**: 'A Library Book Can Be Checked out By Only One Person' ensures that books are not double-checked out.
- **E-commerce Example**: 'A Customer Can Only Have One Active Account' prevents fraud.

# Naming and Defining Data

### Good names for data are:  

- Related to business, not technical, characteristics  
- Meaningful and self-documenting  
- Unique  
- Readable  
- Composed of words from an approved list  
- Repeatable  
- Written in standard syntax.

### Data Definitions

- **Term**: A term is a word or phrase with a specific meaning
- **Fact:** A fact is an association between two or more terms.
- **Guidelines for Good Data Definition**: Data definitions should be a concise description of essential data meaning, gathered with system requirements, achieved by consensus, iteratively refined, and accompanied by diagrams.

### Time-dependent Data Modeling

- Modeling time-dependent data is crucial for compliance with regulations like HIPAA and Sarbanes-Oxley.
- Example: An `Assignment` associative entity that tracks the date range of a product's assignment to a product line.
- This approach allows for better tracking of changes over time and enhances data integrity.