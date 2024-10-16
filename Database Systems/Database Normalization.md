# Helpful Videos/Resources:

https://www.youtube.com/watch?v=GFQaEYEc8_8&t=2s
https://www.freecodecamp.org/news/database-normalization-1nf-2nf-3nf-table-examples/

### What is Database Normalization?

- Database normalization is a design principle aimed at organizing data efficiently within a relational database.
- It reduces redundancy and maintains data integrity by structuring data into multiple related tables.
- Normalization helps eliminate undesirable characteristics associated with data manipulation, such as insertion, deletion, and update anomalies.
- The process involves defining relationships between tables using keys, which are essential for maintaining data consistency.
- Key types include primary keys (unique identifiers for records), foreign keys (linking records across tables), and composite keys (combinations of multiple columns as identifiers).
- Normalization is crucial for large databases where clarity and maintainability are paramount.

### Purpose of Normalization

- The primary goal of normalization is to simplify database design and avoid complexities that arise from data redundancy.
- It organizes data into multiple tables that are linked through relationships, enhancing data integrity and consistency.
- By eliminating duplicate data, normalization reduces storage costs and improves query performance.
- It facilitates easier data management and maintenance, allowing database administrators to make changes without affecting other data.
- Normalization also helps in enforcing data integrity constraints, ensuring that the data remains accurate and reliable.
- Overall, normalization leads to a more efficient and effective database structure.

# Types of Database Normalization

### Overview of Normal Forms

- Normalization is categorized into several forms, with the first three being the most commonly used: 1NF, 2NF, and 3NF.
- Each normal form builds upon the previous one, meaning that a table must satisfy the criteria of 1NF to be considered for 2NF, and so forth.
- Higher normal forms (4NF, 5NF, and 6NF) exist but are less frequently implemented in practice.
- The focus of this guide will be on the first three normal forms, as they are foundational to understanding database normalization.
- Each normal form addresses specific types of redundancy and dependency issues within the database structure.
- Understanding these forms is essential for designing efficient and effective relational databases.

| Normal Form | Criteria                                  | Purpose                                                                                              |
| ----------- | ----------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| 1NF         | Atomic values, primary key, no duplicates | Eliminates repeating groups and ensures data is stored in a structured manner.                       |
| 2NF         | Must be in 1NF, no partial dependency     | Eliminates redundancy by ensuring all non-key attributes depend on the entire primary key.           |
| 3NF         | Must be in 2NF, no transitive dependency  | Further reduces redundancy by ensuring non-key attributes do not depend on other non-key attributes. |

### First Normal Form (1NF)

- A table is in 1NF if it meets the following criteria:
- - Each cell contains atomic values (no multiple values in a single cell).
    - There is a primary key that uniquely identifies each row.
    - No duplicated rows or columns exist.
    - Each column contains only one value for each row.
- Example of a table in 1NF:

|   |   |   |   |   |   |   |
|---|---|---|---|---|---|---|
||employee_id|name|job_code|job|state_code|home_state|
||E001|Alice|J01|Chef|26|Michigan|
||E001|Alice|J02|Waiter|26|Michigan|

- The above table meets all 1NF criteria, but it has redundancy in the name and home_state fields.

### Second Normal Form (2NF)

- A table is in 2NF if it is already in 1NF and meets the following criteria:
- - There are no partial dependencies; all non-key attributes must be fully dependent on the primary key.
- Example of a transition to 2NF:
- - Original table (not in 2NF):

|   |   |   |   |   |   |   |
|---|---|---|---|---|---|---|
||employee_id|name|job_code|job|state_code|home_state|
||E001|Alice|J01|Chef|26|Michigan|
||E001|Alice|J02|Waiter|26|Michigan|

- - Split into two tables:

1. 1. employee_roles Table:

|   |   |   |
|---|---|---|
||employee_id|job_code|
||E001|J01|
||E001|J02|

2. 1. employees Table:

|   |   |   |   |   |
|---|---|---|---|---|
||employee_id|name|state_code|home_state|
||E001|Alice|26|Michigan|

### Third Normal Form (3NF)

- A table is in 3NF if it is already in 2NF and meets the following criteria:
- - There are no transitive dependencies; non-prime attributes must not depend on other non-prime attributes.
- Example of a transition to 3NF:
- - Continuing from the 2NF tables, we can further separate the state information:

1. 1. employee_roles Table:

|   |   |   |
|---|---|---|
||employee_id|job_code|
||E001|J01|
||E001|J02|

2. 1. employees Table:

|   |   |   |   |
|---|---|---|---|
||employee_id|name|state_code|
||E001|Alice|26|

3. 1. jobs Table:

|   |   |   |
|---|---|---|
||job_code|job|
||J01|Chef|
||J02|Waiter|

4. 1. states Table:

|   |   |   |
|---|---|---|
||state_code|home_state|
||26|Michigan|
||56|Wyoming|

# Examples of Normalization

### Illustrative Examples of 1NF, 2NF, and 3NF

- ****1NF Example****: The initial employee table with atomic values and a composite primary key.
- ****2NF Example****: The separation of employee roles and employee details into distinct tables to eliminate partial dependencies.
- ****3NF Example****: Further separation of state information into a dedicated states table to eliminate transitive dependencies.
- These examples illustrate the step-by-step process of normalization, highlighting the importance of each normal form.
- The transition from 1NF to 3NF demonstrates how redundancy is systematically reduced while maintaining data integrity.
- Understanding these examples is crucial for applying normalization principles in real-world database design.

# Summary

- Database normalization is essential for organizing data in relational databases, particularly large ones.
- The main purpose is to reduce redundancy and maintain data integrity through structured relationships.
- The first three normal forms (1NF, 2NF, 3NF) provide a framework for achieving an efficient database design.
- Most databases operate effectively within 3NF, but higher normal forms can be applied based on specific requirements.
- Understanding normalization is vital for database administrators and developers to create maintainable and efficient systems.
- This guide serves as a foundational resource for anyone looking to deepen their understanding of database normalization.