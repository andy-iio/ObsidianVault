# Helpful Videos/Resources:
https://www.youtube.com/watch?v=6Iu45VZGQDk&list=PLBlnK6fEyqRi_CUQ-FXxgzKQ1dwr_ZJWZ
# Definitions:
• Data: stored representations of meaningful objects and events  
• Structured: numbers, text, dates  (RDBMS)
• Unstructured: images, video  (Big data technology needed)
• semi structure - documents  (Big data technology needed)
• Datum -> a single piece of information (5%)  
• Data -> an unsorted collection of datum  (2, 3, 5, 200, 10)  
• Information: data processed to increase knowledge in the person 
• Knowledge: how to use information  
• Wisdom: when and why to use it

### Metadata  
• To be able to share data/ information we must have an  
agreement as to what the data looks like, how it is stored,  
etc.  
• This description is called METADATA, also called schema in  
some places  
• A description of a particular piece of data, how it relates to other  
data, etc.
![[Pasted image 20240905081503.png]]

### Databases:  
• An organized collection of logically related data  
• Generally designed to allow ‘easy’ access of data

#### File Processing Databases  
• File Processing – Application manages the data  
• 1960-1980-present  
• Started with sequential files (SAM) and later indexes (ISAMs) were created  
• Still used, can work for small or simple data, but there are some things to consider

##### Want to avoid duplicate data:

![[Pasted image 20240905094131.png]]

### Relational Databases  
• Types of Databases  
	• Relational  
		• 1980- present  
		• Data is stored in a series of interrelated tables  
		• Based on mathematical set theory  
		• Originally defined by Edgar Frank Codd in 1970  
		• The primary form of databases today  
		• Can be highly efficient for any amount of data  
		• User/program do not know the details of the file/record layout  
		• Uses industry standard Structured Query Language to access the data  
		• Examples are: MS Access, Oracle, MySQL, MariaDB, Postgres, MS SQL Server,  
		DB2

##### When database is managed by a Database Management System  
-  Single copy of the data  
	• Integrity  
	• All programs access the same copy of the data  
		• No duplication of data  
		• Space savings  
	• Actual file/data layouts hidden  
		• Each user/program gets only the data they require  
		• No need for interpretation/translation  
		• Security  
	• Shared access  
		• Can cause concurrency issues if not done correctly  
		• Central repository of shared data  
		• Data is managed by a controlling agent  
		• Stored in a standardized, convenient form  

### Database Management System  
- A software system that is used to create, maintain, and provide controlled access to user databases
- DBMS manages data resources like an operating system manages hardware resources
![[Pasted image 20240905100750.png]]

### The Database Approach  
• Data models  
	• Graphical diagram capturing nature and relationship of data  
	• Enterprise Data Model–high-level entities and relationships for the organization  
	• Project Data Model–more detailed view, matching data structure in database or data warehouse  
• Entities  
	• Noun form describing a person, place, object, event, or concept  
	• Composed of attributes  
• Relationships  
	• Between entities  
	• Usually one-to-many (1:M) or many-to-many (M:N), but could also be one-to one (1:1)  
• Relational Databases  
	• Database technology involving tables (relations) representing entities and primary/foreign keys representing relationships

### Relationships (between entities)
• Diagramming  
	• Many different ways but generally follow  
		• Tables are boxes  
		• Relationships are lines joining the tables  
			• One-to-one relationship – line with no ends  
			• One-to-many relationship – line with a > or ∞ symbol at one end  
			• Many-to-many relationship – line with a > or ∞ symbol at both ends
- One to Many (1-M) relationship: 
	- One customer may place many orders, but each order is placed by a single customer. 
	- One order has many order lines; each order line is associated with a single order. 
	- One product can be in many order lines, each order line refers to a single product
- Many to Many (M-M) relationship:
	- One order involves many products and one product is involved in many orders
- One to One (1-1) relationship:
	- One librarian has one library, and one library has only one librarian
### Enterprise and Project Level Data Models

| = One
/|\\ = Many
##### Enterprise Data Model
![[Pasted image 20240905102033.png]]

##### Project-Level Data Model
![[Pasted image 20240905102100.png]]

