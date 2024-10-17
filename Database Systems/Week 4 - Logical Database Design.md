# Components of the Relational Model

### Data Structure

- The relational model is based on the concept of tables (relations), which consist of rows (records) and columns (attributes).
- Each table must have a unique name, and every attribute value must be atomic, meaning it cannot be multivalued or composite.
- The uniqueness of rows is essential; no two rows can have identical values across all fields.
- Attributes within a table must have unique names, and the order of both columns and rows is irrelevant to the structure of the relation.

### Data Manipulation

- SQL (Structured Query Language) is the primary tool for data manipulation, allowing for powerful operations to retrieve and modify data.
- Common SQL operations include SELECT, INSERT, UPDATE, and DELETE, which facilitate interaction with the database.
- SQL's flexibility enables complex queries, including joins, subqueries, and aggregations, enhancing data retrieval capabilities.

### Data Integrity

- Data integrity is crucial for maintaining the accuracy and consistency of data within a database.
- Mechanisms such as primary keys, foreign keys, and integrity constraints are implemented to enforce business rules.
- Primary keys ensure that each record is unique, while foreign keys establish relationships between tables, maintaining referential integrity.

# Key Fields and Integrity Constraints

### Key Fields

- Keys are special fields in a database that serve as unique identifiers for records.
- Primary keys uniquely identify each record in a table, such as employee numbers or social security numbers.
- Foreign keys are used to link tables together, allowing for relationships between different entities in the database.
- Keys can be simple (single field) or composite (multiple fields), and they often serve as indexes to speed up query responses.

### Integrity Constraints

- Domain constraints define the allowable values for an attribute, ensuring data validity.
- Entity integrity requires that no primary key attribute can be null, enforcing that all primary key fields must contain data values.
- Referential integrity maintains consistency between related tables, ensuring that foreign key values correspond to primary key values in the parent table.

### Referential Integrity Rules

- Referential integrity rules dictate how foreign keys relate to primary keys, ensuring data consistency across tables.
- Common delete rules include:
- - Restrict: Prevents deletion of a parent record if related child records exist.
    - Cascade: Automatically deletes child records when the parent record is deleted.
    - Set-to-Null: Sets the foreign key in the child record to null if the parent record is deleted.

# Transforming EER Diagrams Into Relations

### Mapping Regular Entities

- Regular entities with simple attributes map directly to relations in the database.
- Composite attributes are broken down into their simple components when mapping to relations.
- Multivalued attributes require the creation of a separate relation, with a foreign key linking back to the original entity.

### Mapping Weak Entities

- Weak entities are represented as separate relations, with a foreign key referencing the strong entity that identifies them.
- The primary key of a weak entity is composed of its partial identifier and the primary key of the identifying strong entity.
- Domain constraints for foreign keys in weak entities must not allow null values, ensuring integrity.

### Mapping Binary Relationships

- One-to-Many (1:M): The primary key from the one side becomes a foreign key in the many side.
- Many-to-Many (M:N): A new relation is created that includes the primary keys of both entities as its own primary key.
- One-to-One (1:1): The primary key from the mandatory side becomes a foreign key in the optional side.

### Unary Relationships

- Unary relationships involve a single entity type and can be one-to-many or many-to-many.
- Example: An EMPLOYEE entity with a unary relationship where an employee can supervise other employees.
- In a one-to-many relationship, a recursive foreign key is used within the same relation to link employees to their supervisors.
- For many-to-many relationships, two relations are created: one for the entity type and one for the associative relation.
- This mapping allows for clear representation of hierarchical structures within the data.
- Case Study: Organizational charts often utilize unary relationships to depict reporting structures.

### Ternary Relationships

- Ternary relationships involve three entities and require careful mapping to maintain data integrity.
- Each entity in the relationship is represented by its own relation, along with an associative entity that links them.
- Example: A PATIENT TREATMENT relationship where a patient, a treatment, and a doctor are involved.
- The associative entity must include foreign keys from each of the three entities to maintain referential integrity.
- It is often beneficial to create a surrogate key for the associative entity to simplify queries.
- Historical Context: Ternary relationships are common in healthcare databases where multiple entities interact.

# Mapping Relationships in Database Systems

### M:N Relationships

- M:N relationships require a new intersection relation to manage the many-to-many connections between two entities.
- A composite primary key is formed from the primary keys of the two entities involved in the relationship.
- Example: In a relationship between Students and Courses, a new relation Enrollment can be created with StudentID and CourseID as composite keys.
- Foreign keys in the intersection relation reference the primary keys of the original entities, ensuring referential integrity.
- This mapping allows for efficient querying and management of relationships in a relational database.
- Case Study: University database systems often utilize M:N relationships to manage course enrollments.

### Binary 1:1 Relationships

- In a binary 1:1 relationship, one entity is associated with exactly one instance of another entity.
- Example: A relationship between a Person and a Passport, where each person can have only one passport.
- The foreign key is placed in the relation on the optional side, linking back to the mandatory side's primary key.
- This structure simplifies data retrieval and maintains data integrity.
- Often, one direction of the relationship may be optional, allowing for flexibility in data entry.
- Historical Context: 1:1 relationships are common in scenarios where entities are tightly coupled, such as user accounts and profiles.

### Associative Entities

- Associative entities are used to represent M:N relationships and can have their own attributes.
- When an identifier is assigned to an associative entity, it can enhance user experience by providing meaningful identifiers.
- Example: In a shipping database, a SHIPMENT associative entity may link Orders and Products, with attributes like ShipmentDate.
- The default primary key for the associative relation is typically a composite key formed from the primary keys of the two entities.
- Case Study: E-commerce platforms often utilize associative entities to manage complex relationships between products and orders.
- Mapping associative entities correctly is crucial for maintaining data integrity and avoiding redundancy.

# Data Normalization

### Importance of Normalization

- Data normalization is a process used to validate and improve the logical design of a database.
- The goal is to eliminate data redundancy and ensure data integrity by decomposing relations with anomalies.
- Well-structured relations allow users to insert, delete, and update rows without causing inconsistencies.
- Common anomalies include insertion, deletion, and modification anomalies, which arise from poor design.
- General Rule: A table should pertain to only one entity type to avoid unnecessary dependencies.
- Case Study: Normalization is crucial in financial databases to maintain accurate records.

### Steps in Normalization

- The normalization process typically involves three normal forms (1NF, 2NF, 3NF) to ensure data integrity.
- First Normal Form (1NF) requires that all attributes are atomic and there are no multivalued attributes.
- Second Normal Form (2NF) builds on 1NF by ensuring that every non-key attribute is fully functionally dependent on the entire primary key.
- Third Normal Form (3NF) requires that there are no transitive dependencies among non-key attributes.
- Each step in normalization helps to reduce redundancy and improve data integrity.
- Example: A product order table may need to be normalized to separate customer and product information.

### Functional Dependencies and Keys

- Functional dependencies define the relationship between attributes in a relation, where one attribute determines another.
- A candidate key is a unique identifier for a relation, and one of these will be chosen as the primary key.
- Example: In a customer table, both CustomerID and Email could serve as candidate keys.
- Understanding functional dependencies is crucial for effective normalization and ensuring that all non-key fields are dependent on the primary key.
- Case Study: In a library database, the relationship between BookID and BookTitle illustrates functional dependency.
- Properly identifying functional dependencies helps in designing efficient database schemas.