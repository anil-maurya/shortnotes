# RDBMS
Relation Database Management System

## Content
1. RDBMS
2. SQL




## Terms to Understand

- Subquery
- Index
	- Unique Index
	- Cluster
	- Non-cluster
- SQL Statements
	- Types
		- DML
		- DDL
		- DCL
		- TCL
		-
	- Delete
	- Truncate
	- Current Date
- CLAUSE
- 


- ACID Property
- Store Procedure
- Functions
- Manipulation Functions
- Operator
- Relationship
- Dynamic SQL
- SQL vs PLSQL
- View
- Collections
- Datawarehouse
- OLTP vs OLAP
- OPERATORS
- Trigger
- Variables


## DBMS

DBMS is a software to creation, definition and manipulation of database, allowing users to store, process and analyse data easily. DBMS provides us an interface of a tool to perform various operations like creating database, storing data in it. Updaating data, creating table in the database etc.

Also provides security to the database.

Examples of Databases
- MySQL
- Oracle
- SQL Server
- IBM DB2
- PostgreSQL

Characteristics of DBMS

1. Data stored into Tables
2. Reduced Redundancy
3. Data Consistency
4. Support Multiple user and Concurrent Access
5. Query Language
6. Security
7. Supports transcations, which allows us to better handle and manage data integrity in real world application where multi-threading is extensively used.


|Student_Id	| Student_Name	| Student_Addr		|Student_Age|
|-----------|---------------|-------------------|-----------|
| 101	|	Chaitanya	|	Dayal Bagh, Agra	| 27        |
| 102	| Ajeet	| Delhi	| 26|   
|103	|Rahul	|Gurgaon|	24|
0|104	|Shubham|	Chennai|	25|


 
## Data Models

Data Model is a collection of conecpt to describe the structure of a database.


Types of data model
1. High level (Conceptual) data model
2. Low level (Physical) data model
3. Representationl(Implementation) data model 


## Database Schema & instances

A database schema is the skeleton structure that represents the logical view of the entire database. It defines how the data is organized and how the relations amongh them are associated.

The description of database is called 'database schema', which is specified during database design and is not expected to change frequently.

## Three Schema Architecture 
1. The Internal Level : Describe the physical storage structure of the database.
2. The conceptual Level :    
3. The external level or view level : 


## Database Model
A database model is the logical design and structure of a database and define how data will be stored, accessed and updated in DBMS.

1. Hierarchical Model 
	Tree-like structure with a single root, to which all the other data is linked.
	
2. Network Model
	In this model data is organised like a graph, and are allowed to have more than one parent note. In this database model data is more related as more relationship are established in this database model.  As the data is more related hence accessing the data is also easier and fast.
	
	![enter image description here](https://www.studytonight.com/dbms/images/network-dbms-model.png)
	
3. Entity-relationship model
	In this model, relationships are created by dividing object of interest into entity and its characteristics into attributes. 
	
	![enter image description here](https://www.studytonight.com/dbms/images/attribute-example.jpg)

5. Relational Model
In this Model, data is organised in  two-dimensional tables and the relationship is maintained by shorting a common field.

![enter image description here](https://www.studytonight.com/dbms/images/relational-dbms-model.png)


## ER Model (Entity Relationship Model)

Diagramatic representation of ER Model which uses entities, relationship and attributes.

Entity - Entities are the real world objects or a thing in a real world which have their independent existenace.

Attributes - Properties of entity

Relationship - Association between two or more entities.

Representation

Entity => Rectangular Box | example Artist & songs
Relation => Diamond | CREATE, Artist create songs
Attributes => Oval | Name, Genre


### Entity

Entity Set :

### Attributes

Attribbutes are the properties of the entities that describe the entity.

Employee is an entities 


Types of Attributes

1. Simmple Attributes or atomic attributes.

	An attribute which can not be further subdivided into components is a simple attribute.
	Example - Gender
 
2. Composite Attribute

	Attribute which can be splitted into componnets is a componsite attribute. For example - The address can be further splitted into house number, street number, city, state, country and pincode. The name can be splitted into first name middle name and last name.


3. Single-valued attribute
	
	The attribute which takes up only a single value for each entity instance is a single-valued attribute.
	Example - The age of a person

4. Multi-Valued Attributes

	The attributes which takes up more than a single value of each entity instance is multi-values attribute.

- Stores vs Derived Attributes

- Complex vs Composite Attributes

- Key vs Non-Keys Attributes
- Required vs non-required

### Relationship

Relationship Set

Relationship Types

Relationship Components

1. Relationship type name
2. Degree
3. Cardinality 

### Cardinality Ratios

Types

1. One-to-One => Represented by Arrow on both sides
2. One-to-Many => Arrow at the One side
3. Many-to-One
4. May-to-Many => Straight line without arrow

## RDBMS Basic Concepts
In RDBMS, data is stored in relations(tables) and is represented in form or tuples.

**Table**
Table is a collection of data elements organized in form of row and columns. 


**Attribute** : Attributes are the properties that define a relation. e.g.; **ROLL_NO**, **NAME** etc

**Tuple** 
Each row in the relation is known as tuple. The above relation contains 4 tuples, one of which is shown as:

**Attribute Domain** 
When an attribute is defined in a relation(table), it is defined to hold only a certain type of values, which is known as 

**Relation Schema**
A relation schema describes the structure of the relation, with the name of the relation(name of table), its attributes and their names and type

**Relation Key**
A relation key is an attribute which can uniquely identify a particular tuple(row) in a relation(table).


**Degree:** The number of attributes in the relation is known as degree of the relation.

**Cardinality:** The number of tuples in a relation is known as cardinality. The **STUDENT** relation defined above has cardinality 4.

**Data Definition Language:** It is used to define the structure of the database. e.g; 
	CREATE TABLE, 
	ADD COLUMN, 
	DROP COLUMN and so on.

**Data Manipulation Language:** It is used to manipulate data in the relations. e.g.; INSERT, DELETE, UPDATE and so on.
**Data Query Language:** It is used to extract the data from the relations. e.g.; SELECT




## Schema 
Logical representation of a database, It can have single table or more than one table.

## Keys
**KEYS in DBMS** is an attribute or set of attributes which helps you to identify a row(tuple) in a relation(table). They allow you to find the relation between two tables. Keys help you uniquely identify a row in a table by a combination of one or more columns in that table.

**Why we need a Key?**

-   Keys help you to identify any row of data in a table. In a real-world application, a table could contain thousands of records. Moreover, the records could be duplicated. Keys ensure that you can uniquely identify a table record despite these challenges.
-   Allows you to establish a relationship between and identify the relation between tables
-   Help you to enforce identity and integrity in the relationship.


1. Candidate Key - A set of uniquely identifiable keys
2. Primary Key  - Unique + Not Null
3. Foreign Key - 
It is attributes or set of attributes that references to Primary Key of same table or another table. FK maintain Referential Integrity
- More than one FK can exists in a table.
- Attribute Name of FK can be different from Primary key.

Referencing Table - Table which is taking reference from other table and FK is found in this table.
Referenced Table - Table whose reference is used in some other table. Primary key is found in this table.

How FK maintain Referential Integrity ?
Action					Referenced Table					Referencing Table 
INSERT  					No violation							May cause violation
DELETE					May cause violation				No violation
UPDATE					May cause violation				May cause violation

Queries to avoid problems
ON DELETE CASCADE
ON DELETE SET NULL, There may be problem if foreign key is primary key in Referencing table.
ON DELETE NO ACTION - Default option

4. Super Key
A super key is a combination of all possible attributes which can uniquely identify two tuples in a table.



## Data Integrity 

Data Integrity refers to the accuracy and consistency of data.

When creating databases, attention needs to be given to data integrity and how to maintain it. A good database will enforce data integrity whenever possible. 

For example, a user could accidentally try to enter a phone number into a date field. If the system enforces data integrity, it will prevent the user from making these mistakes.

**Types of Data Integrity**
 
-   Entity integrity
-   Referential integrity
-   Domain integrity
 
**1.  Entity Integrity**

Entity integrity defines each row to be unique within its table. No two rows can be the same.

To achieve this, a primary key can be defined. The primary key field contains a unique identifier – no two rows can contain the same unique identifier.

**2. Referential Integrity**
Referential integrity is concerned with relationships. When two or more tables have a relationship, we have to ensure that the foreign key value matches the primary key value at all times. We don’t want to have a situation where a foreign key value has no matching primary key value in the primary table. This would result in an orphaned record.

**3. Domain Integrity**
Domain integrity concerns the validity of entries for a given column. Selecting the appropriate data type for a column is the first step in maintaining domain integrity. Other steps could include, setting up appropriate constraints and rules to define the data format and/or restricting the range of possible values.

**Relational Integrity Constraints**
-   Integrity constraints are a set of rules. It is used to maintain the quality of information.
-   Integrity constraints ensure that the data insertion, updating, and other processes have to be performed in such a way that data integrity is not affected.

Thus, integrity constraint is used to guard against accidental damage to the database.

Types
1. Domain Constraints
2. Entity Integrity constraints
3. Referential Integrity Constraints
4. Key Constraints

## Normalization

Remove anomalies and redundant data.
Three types of anomalies
1. Insertion anomalies
2. Updation anomalies
3. Deletion anomalies

Normalization Form
- 1NF - First Normal Form
- 2NF - Second Normal Form
- 3NF - Third Normal Form
- Boyce Code Normal Form

## Denormalization

Denormalization is a database optimization technique in which we add redundant data to one or more tables. This can help us avoid costly joins in a relational database. Note that denormalization does not mean not doing normalization. It is an optimization technique that is applied after doing normalization.

In a traditional normalized database, we store data in separate logical tables and attempt to minimize redundant data. We may strive to have only one copy of each piece of data in database.

**Pros of Denormalization:-**

1.  Retrieving data is faster since we do fewer joins
2.  Queries to retrieve can be simpler(and therefore less likely to have bugs),  
    since we need to look at fewer tables.

**Cons of Denormalization:-**

1.  Updates and inserts are more expensive.
2.  Denormalization can make update and insert code harder to write.
3.  Data may be inconsistent . Which is the “correct” value for a piece of data?
4.  Data redundancy necessitates more storage.


## JOINS

Joins are mainly Cartesian product of two or more relations (or tables).
1. Inner Join
2. Outer Join 

Inner Join selects rows from the tables that fulfills the join condition. But using inner join the data specifically the rows from both the tables that do not satisfy the condition are lost. Outer Join can be used to prevent the loss of data from the tables.

Types of Outer Join
1. Left Outer Join
	Left Outer Join returns all the rows from the table on the left and columns of the table on the right is null 	padded. Left Outer Join retrieves all the rows from both the tables that satisfy the join condition along with the unmatched rows of the left table

3. Right Outer Join
Right Outer Join returns all the rows from the table on the right and columns of the table on the left is null padded. Right Outer Join retrieves all the rows from both the tables that satisfy the join condition along with the unmatched rows of the right table.

	- Cross Join
	- Natural Join

## Indexing
To access records faster and reduce I/O cost we do indexing,  

When searching a record data in 1 block is copied from HDD to RAM then search is performed and if record is not found next block is copied to RAM and searched and previous block is RAM is discorded. Thus every search required HDD I/O and it is known is I/O cost.

Indexing is a data structure technique to efficiently retrieve records from the database files based on some attributes on which the indexing has been done. Indexing in database systems is similar to what we see in books

- **Primary Index**  − If data has primary key, which is unique and not null and it is shorted then Primary Index is applied. Primary index is defined on an ordered data file. The data file is ordered on a  **key field**. The key field is generally the primary key of the relation.

- **Clustering Index**  − If data has shorted record but key is not unique then Clustering index is used. 
    
- **Secondary Index**  − If candidate key has duplicated records and it is not shorted, then Secondary index is used. In this case two index are created.

Two techniques are used to index records
- Dense Index - In index table, for each records pointers are created. It is done when data is not shorted.
- Sparse Index - Only pointers for anchor records are stored, this can be used only data is shorted.

- Multi level Index -
	sometime we use both indexing technique as secondary indexing..

## Hashing 
If data is huge and in that case Indexing can not give desired performance, so in that case hashing technique is used to boost search performance. 


## PL-SQL
Procedural-SQL, Extension of SQL where we can write functions, programming nature is included and block of code is known as code block.
 
- Function
- Procedure
- Trigger
- Cursor


## ACID Properties
A transaction is a single logical unit of work which accesses and possibly modifies the contents of a database. Transactions access data using read and write operations.  
In order to maintain consistency in a database, before and after the transaction, certain properties are followed. These are called **ACID** properties.

- Atomicity 
Either all or non - In database either all transaction will happen or none, like in bank transaction if any step in transaction fails all steps must be roll backed.
 
 Consistency
 This means that integrity constraints must be maintained so that the database is consistent before and after the transaction. It refers to the correctness of a database. Referring to the example above,  
The total amount before and after the transaction must be maintained.  
Total **before T** occurs = **500 + 200 = 700**.  
Total **after T occurs** = **400 + 300 = 700**.  
Therefore, database is **consistent**. Inconsistency occurs in case **T1** completes but **T2** fails. As a result T is incomplete.

 Isolation 
This property ensures that multiple transactions can occur concurrently without leading to the inconsistency of database state. Transactions occur independently without interference. Changes occurring in a particular transaction will not be visible to any other transaction until that particular change in that transaction is written to memory or has been committed. This property ensures that the execution of transactions concurrently will result in a state that is equivalent to a state achieved these were executed serially in some order.
 
 Durability 
This property ensures that once the transaction has completed execution, the updates and modifications to the database are stored in and written to disk and they persist even if a system failure occurs. These updates now become permanent and are stored in non-volatile memory. The effects of the transaction, thus, are never lost.
 