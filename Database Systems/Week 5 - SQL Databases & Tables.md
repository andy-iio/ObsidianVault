# SQL Commands
|Command|Description|
|---|---|
|`CREATE DATABASE`|Creates a new database with the specified name.|
|`DROP DATABASE`|Deletes an existing database.|
|`CREATE TABLE`|Creates a new table with specified columns and data types.|
|`ALTER TABLE`|Modifies an existing table structure, such as adding or changing columns.|
|`INSERT INTO`|Adds new records to a table.|
|`SELECT`|Retrieves data from one or more tables.|
# Datatypes
|Data Type|Description|
|---|---|
|`TINYINT`|8-bit integer, can be signed or unsigned.|
|`SMALLINT`|16-bit integer, can be signed or unsigned.|
|`INT`|32-bit integer, can be signed or unsigned.|
|`BIGINT`|64-bit integer, can be signed or unsigned.|
|`FLOAT`|Floating-point number, similar to C's float.|
|`DOUBLE`|Double-precision floating-point number, similar to C's double.|
|`CHAR(m)`|Fixed-length string with a maximum length of 255 characters.|

### Introduction to SQL

- SQL stands for Structured Query Language, a standard interface for database interaction.
- SQL is essential for querying and managing databases.
- SQL allows users to define, manipulate, and query data in relational databases.
- It provides commands for inserting, deleting, and updating data, as well as altering database schemas.

### General SQL Concepts

- SQL statements are the primary means of communication with an SQL server, ending with semicolons.
- Keywords in SQL are typically written in uppercase for clarity, while strings are enclosed in single quotes.
- Variations exist between different SQL implementations and versions, affecting syntax and functionality.

# Database and Table Definitions

### Creating and Deleting Databases

- Use the command `CREATE DATABASE name;` to create a new database.
- To delete a database, the command `DROP DATABASE name;` is used, which removes all associated data.

### Defining Tables

- Tables are created using the `CREATE TABLE` statement, specifying columns and their data types.
- Example: `CREATE TABLE tblCustomer (id INT, name VARCHAR(40) DEFAULT 'Mr. Unknown', city VARCHAR(40) DEFAULT 'Unknown');`
- Columns can be defined with constraints such as NOT NULL, PRIMARY KEY, and DEFAULT values.

# Table Management and Data Manipulation

### Table Constraints and Relationships

- Table constraints are defined using clauses like PRIMARY KEY, UNIQUE, and FOREIGN KEY.
- Example of a foreign key: `FOREIGN KEY (id) REFERENCES tblCustomer (id)` establishes a relationship between tables.
- CHECK constraints can validate data entries, e.g., `CHECK (discount BETWEEN 0 and 0.25)` ensures discount values are within a specified range.

### Modifying Table Structures

- Use `ALTER TABLE` to modify existing tables, such as adding new columns or changing default values.
- Example: `ALTER TABLE tblOrderHeader ADD salespersonID INTEGER REFERENCES tblPerson;`
- Entire tables can be removed with `DROP TABLE tblTableName;`, but all relationships must be cleared first.

# Data Insertion and Querying

### Inserting Data into Tables

- The `INSERT INTO` command is used to add new records to a table.
- Example: `INSERT INTO tblCustomer VALUES (1, 'Fred', 'Flintstone', '1313 Mockingbird Lane', 'Bedrock', 'ON', 'N2M 4M1', '<phone>');`
- Specific fields can be targeted during insertion, allowing for flexibility in data entry.

### Querying Data

- Data retrieval is performed using the `SELECT` statement, which can specify particular columns or all columns with `*`.
- Example queries include: `SELECT name FROM tblCustomer;` and `SELECT * FROM tblCustomer WHERE city = 'Toronto';`
- Queries can be complex, involving multiple tables and conditions, which will be explored in future lessons.

# SQL Data Types

### Overview of SQL Data Types

- Each column in a table must have a defined data type, which dictates the kind of data it can hold.
- Common data types include INTEGER, FLOAT, and VARCHAR, each serving different purposes.

### Useful MySQL Data Types

> ****Integer Data Types:****

- TINYINT: 8-bit integer, signed or unsigned.
- SMALLINT: 16-bit integer, signed or unsigned.
- INT: 32-bit integer, signed or unsigned.
- BIGINT: 64-bit integer, signed or unsigned.
- BOOL: Represents TRUE or FALSE as an 8-bit integer.

****Floating-Point Data Types:****

- FLOAT: Similar to C's float, used for single-precision.
- DOUBLE: Similar to C's double, used for double-precision.

****Character/String Data Types:****

- CHAR: Fixed-length string, right-padded with spaces.
- VARCHAR(m): Variable-length string, where m is the maximum length (up to 255 characters).