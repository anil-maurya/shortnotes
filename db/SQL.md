# SQL

- Not Case sensitive
- Some database systems require a semicolon at the end of each SQL statement
- Semicolon is the standard way to separate each SQL statement in database systems that allow more than one SQL statement to be executed in the same call to the server. 
- Most Important SQL Commands
-   **SELECT**  - extracts data from a database
-   **UPDATE**  - updates data in a database
-   **DELETE**  - deletes data from a database
-   **INSERT INTO**  - inserts new data into a database
-   **CREATE DATABASE**  - creates a new database
-   **ALTER DATABASE**  - modifies a database
-   **CREATE TABLE**  - creates a new table
-   **ALTER TABLE**  - modifies a table
-   **DROP TABLE**  - deletes a table
-   **CREATE INDEX**  - creates an index (search key)
-   **DROP INDEX**  - deletes an index


## Database Management

```sql

SHOW DATABASES;

USE <database>;

SHOW TABLES;

DESCRIBE <table_name>;

DESC <table_name>


CREATE DATABASE testdb;

DROP DATABASE testdb;


-- Write output to local text file 

SELECT * from products INTO OUTFILE 'sql.txt';

-- or after login to database we can fire..

tee databaselog.txt;

-- It will start loggin and log every command and output.


-- Backup Database

BACKUP DATABASE databasename
TO DISK = 'filepath'
WITH DIFFERENTIAL;


BACKUP DATABASE testDB
TO DISK = 'D:\backups\testDB.bak';


-- Backup in mysql

mysqldump -u root -p sakila > C:\MySQLBackup\sakila_20200424.sql


-- Create Table

-- SQL-SERVER 
-- To use the auto increment field, in SQL Server, you have to use the IDENTITY keyword. 

CREATE TABLE PERSON (
    id INT IDENTITY (1, 1), 
    name VARCHAR(255),
    age INT,
    phone INT
);


CREATE TABLE Person(
  PersonID int,
  LastName varchar(255),
  FistName varchar(255),
  Address varchar(255),
  City varchar(255)
  );

-- MySQL Server

CREATE TABLE TableName (
	Column1 DataType  AUTO_INCREMENT,
	Column2 DataType, 
);

DESC Person;

/*
+----------+--------------+------+-----+---------+-------+
| Field    | Type         | Null | Key | Default | Extra |
+----------+--------------+------+-----+---------+-------+
| PersonID | int(11)      | YES  |     | NULL    |       |
| LastName | varchar(255) | YES  |     | NULL    |       |
| FistName | varchar(255) | YES  |     | NULL    |       |
| Address  | varchar(255) | YES  |     | NULL    |       |
| City     | varchar(255) | YES  |     | NULL    |       |
+----------+--------------+------+-----+---------+-------+
5 rows in set (0.010 sec)

*/

-- Creating Table from another Table

CREATE TABLE Prods AS
SELECT productCode, productName, productline, ProductScale from products;


SELECT * from Prods;

/*
+-------------+---------------------------------------------+------------------+--------------+
| productCode | ProductName                                 | ProductLine      | productScale |
+-------------+---------------------------------------------+------------------+--------------+
| S10_1678    | 1969 Harley Davidson Ultimate Chopper       | Motorcycles      | 1:10         |
| S10_1949    | 1952 Alpine Renault 1300                    | Classic Cars     | 1:10         |
| S10_2016    | 1996 Moto Guzzi 1100i                       | Motorcycles      | 1:10         |
| S10_4698    | 2003 Harley-Davidson Eagle Drag Bike        | Motorcycles      | 1:10         |
| S10_4757    | 1972 Alfa Romeo GTA                         | Classic Cars     | 1:10         |
| S10_4962    | 1962 LanciaA Delta 16V                      | Classic Cars     | 1:10         |
| S12_1099    | 1968 Ford Mustang                           | Classic Cars     | 1:12         |
| S12_1108    | 2001 Ferrari Enzo                           | Classic Cars     | 1:12         |
| S12_1666    | 1958 Setra Bus                              | Trucks and Buses | 1:12         |
| S12_2823    | 2002 Suzuki XREO                            | Motorcycles      | 1:12         |
| S72_1253    | Boeing X-32A JSF                            | Planes           | 1:72         |
| S72_3212    | Pont Yacht                                  | Ships            | 1:72         |
+-------------+---------------------------------------------+------------------+--------------+
110 rows in set (0.001 sec)

*/


-- Delete Table

DROP Table Prods;

```



## SQL Operators

- Arithmetic Operator
	- +
	- -
	- *
	- /
	- %

- Bitwise Operator
	- &
	- |
	- ^

- Comparision Operator
	- =
	- '>'
	- <
	- '>='
	- <=
	- <>

- Compound Operators
	- +=
	- -=
	- *=
	- /=
	- %=
	- &=
	- -=
	- '*='

- Logical Oeprators
	ALL
	AND
	ANY
	BETWEEN
	EXISTS
	IN
	LIKE
	NOT
	OR
	SOME



## SELECT

SELECT <column/s name> FROM <table_name>

Example

```sql

SELECT * from customers;
SELECT first_name, last_name, address from customers;
SELECT customer_id, first_name, address from customers;

```

Notes - 

- fields/attributes are not within ''/"", if done so it is treated as string by database it returns only 'passed' string against each tuples.
- comma ',' is required within fields


'DISTINCT' 

distinct keyword is used to return only unique values.

```sql

SELECT DISTINCT city as CITY from customers;

```

'COUNT'

```sql

SELECT COUNT(city) as city_count from customers;

```



### Distinct Count

In MariaDB

```sql


SELECT DISTINCT productLine from products;
/*
+------------------+
| productline      |
+------------------+
| Classic Cars     |
| Motorcycles      |
| Planes           |
| Ships            |
| Trains           |
| Trucks and Buses |
| Vintage Cars     |
+------------------+
*/

SELECT COUNT(DISTINCT productline) as count from products;

/*
+-------+
| count |
+-------+
|     7 |
+-------+

*/

-- But in SQL Server

SELECT Count(*) AS count
FROM (SELECT DISTINCT productline FROM products);

```


### 'WHERE'

Where clause is used to filter records. The 'WHERE' clause is used to extract only those records that fulfill a specified condition.


SELECT  _column1_, _column2, ..._  
FROM  _table_name_  
WHERE  _condition_;

Operators in The WHERE Clause

	= 	 		equal
	
	>   		greater than
	
	<  	 		less than

	>=	 		greater than or equal

	<> 			Not equal to

	BETWEEN     between certain range

	LIKE	    Search for a pattern

	IN			To specify multiple possible values for a column



### AND, OR and NOT Operators

The AND and OR operators are used to filter records based on more than one condition:

- The AND operator displays a record if all the conditions separated by AND are TRUE.
- The OR operator displays a record if any of the conditions separated by OR is TRUE.



SELECT  _column1_, _column2, ..._  
FROM  _table_name_  
WHERE  _condition1_  AND  _condition2_  AND  _condition3 ..._;

SELECT  _column1_, _column2, ..._  
FROM  _table_name_  
WHERE  _condition1_  OR  _condition2_  OR  _condition3 ..._;

SELECT  _column1_, _column2, ..._  
FROM  _table_name_  
WHERE  NOT  _condition_;


```sql

SELECT productCode, productName, productLine, ProductScale from Products 
WHERE productLine = 'Planes';

/*
+-------------+----------------------------------+-------------+--------------+
| productCode | productName                      | productLine | ProductScale |
+-------------+----------------------------------+-------------+--------------+
| S18_1662    | 1980s Black Hawk Helicopter      | Planes      | 1:18         |
| S18_2581    | P-51-D Mustang                   | Planes      | 1:72         |
| S24_1785    | 1928 British Royal Navy Airplane | Planes      | 1:24         |
| S24_2841    | 1900s Vintage Bi-Plane           | Planes      | 1:24         |
| S24_3949    | Corsair F4U ( Bird Cage)         | Planes      | 1:24         |
| S24_4278    | 1900s Vintage Tri-Plane          | Planes      | 1:24         |
| S700_1691   | American Airlines: B767-300      | Planes      | 1:700        |
| S700_2466   | America West Airlines B757-200   | Planes      | 1:700        |
| S700_2834   | ATA: B757-300                    | Planes      | 1:700        |
| S700_3167   | F/A 18 Hornet 1/72               | Planes      | 1:72         |
| S700_4002   | American Airlines: MD-11S        | Planes      | 1:700        |
| S72_1253    | Boeing X-32A JSF                 | Planes      | 1:72         |
+-------------+----------------------------------+-------------+--------------+

*/

SELECT productCode, productName, productLine, ProductScale from Products
WHERE productLine = 'planes' OR productLine = 'Ships';

/*
+-------------+----------------------------------+-------------+--------------+
| productCode | productName                      | productLine | ProductScale |
+-------------+----------------------------------+-------------+--------------+
| S18_1662    | 1980s Black Hawk Helicopter      | Planes      | 1:18         |
| S18_2581    | P-51-D Mustang                   | Planes      | 1:72         |
| S24_1785    | 1928 British Royal Navy Airplane | Planes      | 1:24         |
| S24_2841    | 1900s Vintage Bi-Plane           | Planes      | 1:24         |
| S24_3949    | Corsair F4U ( Bird Cage)         | Planes      | 1:24         |
| S24_4278    | 1900s Vintage Tri-Plane          | Planes      | 1:24         |
| S700_1691   | American Airlines: B767-300      | Planes      | 1:700        |
| S700_2466   | America West Airlines B757-200   | Planes      | 1:700        |
| S700_2834   | ATA: B757-300                    | Planes      | 1:700        |
| S700_3167   | F/A 18 Hornet 1/72               | Planes      | 1:72         |
| S700_4002   | American Airlines: MD-11S        | Planes      | 1:700        |
| S72_1253    | Boeing X-32A JSF                 | Planes      | 1:72         |
| S18_3029    | 1999 Yamaha Speed Boat           | Ships       | 1:18         |
| S24_2011    | 18th century schooner            | Ships       | 1:24         |
| S700_1138   | The Schooner Bluenose            | Ships       | 1:700        |
| S700_1938   | The Mayflower                    | Ships       | 1:700        |
| S700_2047   | HMS Bounty                       | Ships       | 1:700        |
| S700_2610   | The USS Constitution Ship        | Ships       | 1:700        |
| S700_3505   | The Titanic                      | Ships       | 1:700        |
| S700_3962   | The Queen Mary                   | Ships       | 1:700        |
| S72_3212    | Pont Yacht                       | Ships       | 1:72         |
+-------------+----------------------------------+-------------+--------------+

*/

 SELECT productcode, productName, productLine, ProductScale from products
 WHERE NOT productLine='Planes' AND NOT productLine='Ships'

 /*
+-------------+---------------------------------------------+------------------+--------------+
| productcode | productName                                 | productLine      | ProductScale |
+-------------+---------------------------------------------+------------------+--------------+
| S10_1678    | 1969 Harley Davidson Ultimate Chopper       | Motorcycles      | 1:10         |
| S10_1949    | 1952 Alpine Renault 1300                    | Classic Cars     | 1:10         |
| S10_2016    | 1996 Moto Guzzi 1100i                       | Motorcycles      | 1:10         |
| S10_4698    | 2003 Harley-Davidson Eagle Drag Bike        | Motorcycles      | 1:10         |
| S10_4757    | 1972 Alfa Romeo GTA                         | Classic Cars     | 1:10         |
| S10_4962    | 1962 LanciaA Delta 16V                      | Classic Cars     | 1:10         |
| S32_4485    | 1974 Ducati 350 Mk3 Desmo                   | Motorcycles      | 1:32         |
| S50_1341    | 1930 Buick Marquette Phaeton                | Vintage Cars     | 1:50         |
| S50_1392    | Diamond T620 Semi-Skirted Tanker            | Trucks and Buses | 1:50         |
| S50_1514    | 1962 City of Detroit Streetcar              | Trains           | 1:50         |
| S50_4713    | 2002 Yamaha YZR M1                          | Motorcycles      | 1:50         |
| S700_2824   | 1982 Camaro Z28                             | Classic Cars     | 1:18         |
+-------------+---------------------------------------------+------------------+--------------+
89 rows in set (0.001 sec)
*/

SELECT * FROM Customers  
WHERE  NOT Country='Germany';

SELECT * FROM Customers  
WHERE City='Berlin'  OR City='München';

SELECT * FROM Customers  
WHERE Country='Germany'  OR Country='Spain';

SELECT * FROM Customers  
WHERE Country='Germany' AND (City='Berlin'  OR City='München');

SELECT * FROM Customers  
WHERE  NOT Country='Germany'  AND  NOT Country='USA';

```

### ORDER BY

Use to sort result.

SELECT  _column1_, _column2, ..._  
FROM  _table_name_  
ORDER  BY  _column1, column2, ..._ ASC|DESC;

```sql

-- by default assending order

SELECT * FROM customers
ORDER BY Country;

SELECT * FROM Customers  
ORDER  BY Country DESC;

SELECT * FROM Customers
ORDER by Country, CustomerName;

SELECT * FROM Customers  
ORDER  BY Country ASC, CustomerName DESC;

SELECT * FROM Customers  
ORDER  BY Country ASC, CustomerName DESC;

SELECT productcode, productName, productLine, ProductScale from products
WHERE productLine='Trains' OR productLine='Motorcycles'
ORDER BY productName DESC;
/*
+-------------+----------------------------------------+-------------+--------------+
| productcode | productName                            | productLine | ProductScale |
+-------------+----------------------------------------+-------------+--------------+
| S18_3259    | Collectable Wooden Train               | Trains      | 1:18         |
| S10_4698    | 2003 Harley-Davidson Eagle Drag Bike   | Motorcycles | 1:10         |
| S50_4713    | 2002 Yamaha YZR M1                     | Motorcycles | 1:50         |
| S12_2823    | 2002 Suzuki XREO                       | Motorcycles | 1:12         |
| S24_1578    | 1997 BMW R 1100 S                      | Motorcycles | 1:24         |
| S32_1374    | 1997 BMW F650 ST                       | Motorcycles | 1:32         |
| S10_2016    | 1996 Moto Guzzi 1100i                  | Motorcycles | 1:10         |
| S32_2206    | 1982 Ducati 996 R                      | Motorcycles | 1:32         |
| S24_2360    | 1982 Ducati 900 Monster                | Motorcycles | 1:24         |
| S32_4485    | 1974 Ducati 350 Mk3 Desmo              | Motorcycles | 1:32         |
| S10_1678    | 1969 Harley Davidson Ultimate Chopper  | Motorcycles | 1:10         |
| S50_1514    | 1962 City of Detroit Streetcar         | Trains      | 1:50         |
| S24_2000    | 1960 BSA Gold Star DBD34               | Motorcycles | 1:24         |
| S18_3782    | 1957 Vespa GS150                       | Motorcycles | 1:18         |
| S32_3207    | 1950's Chicago Surface Lines Streetcar | Trains      | 1:32         |
| S18_2625    | 1936 Harley Davidson El Knucklehead    | Motorcycles | 1:18         |
+-------------+----------------------------------------+-------------+--------------+
16 rows in set (0.001 sec)
*/



```


### INSERT INTO

INSERT  INTO  _table_name_ (_column1_, _column2_, _column3_, ...)  
VALUES (_value1_, _value2_, _value3_, ...);

Note - To add values to all column we need not to specify the column names in the SQL query but order of data must be same as order of fields.

INSERT  INTO  _table_name_  
VALUES (_value1_, _value2_, _value3_, ...);

```sql

insert into customers (customer_id, customer_name, address, city)
values (92, 'Cardinal', 'Skagen 21', 'Stavanger');

INSERT  INTO Customers (CustomerName, City, Country)  
VALUES ('Cardinal', 'Stavanger', 'Norway');

```

### SQL NULL Values

If a field in a table is optional, it is possible to insert a new record or update a record without adding a value to this field. Then, the field will be saved with a NULL value.

Test if values is NULL

SELECT  _column_names  
FROM  _table_name_  
WHERE  _column_name_  IS  NULL;

SELECT  _column_names  
FROM  _table_name_  
WHERE  _column_name_  IS  NOT  NULL;


### SQL UPDATE Statement

UPDATE  _table_name_  
SET  _column1_ = _value1_, _column2_ = _value2_, ...  
WHERE  _condition_;

```sql

UPDATE Customers  
SET ContactName = 'Alfred Schmidt', City= 'Frankfurt'  
WHERE CustomerID = 1;

```

Note - 
* It is where clause which determines how many records will be updated. So write where clause carefully.
* By default safe update mode is enabled in MySQL and you can't update using any filed other than 'key'

* So to update data, without using key in where clause disable 'safe update mode'. 


### DELETE Statement

Delete existing records in table.

DELETE  FROM  _table_name_ WHERE  _condition_;

```sql

DELETE  FROM Customers WHERE CustomerName='Alfreds Futterkiste';
DELETE from table_name --Delete All records

```

Comments

	-- 	 		Single line

	/* */  		Multi-line


### SQL SELECT TOP

SQL Server/MS Access 

SELECT  TOP  _number_|_percent_  _column_name(s)_  
FROM  _table_name  
_WHERE  _condition_;

MySQL

SELECT  _column_name(s)_  
FROM  _table_name  
_WHERE  _condition_  
LIMIT  _number_;

```sql
SELECT  TOP  3 * FROM Customers;

-- MySQL
SELECT * FROM Customers  
LIMIT  3;

SELECT  TOP  50  PERCENT * FROM Customers;

SELECT * FROM Customers  
WHERE Country='Germany'  
LIMIT  3;

```
Note - Limit by percentage in MySQL not possible simply by entering value. Need to write
 
```sql
SELECT *
FROM    (
    SELECT list.*, @counter := @counter +1 AS counter
    FROM (select @counter:=0) AS initvar, list
    ORDER BY value DESC   
) AS X
where counter <= (10/100 * @counter);
ORDER BY value DESC

```


### SQL MIN() and MAX() functions

Select min and max value for selected column

SELECT MIN(_column_name_)  
FROM  _table_name_  
WHERE  _condition_;

SELECT MAX(_column_name_)  
FROM  _table_name_  
WHERE  _condition_;

```sql

SELECT MAX(Price) AS LargestPrice  
FROM Products;

SELECT MAX(buyPrice) as MaxCost, MAX(MSRP) as MaxMSRP from products;

/*
+---------+---------+
| MaxCost | MaxMSRP |
+---------+---------+
|  103.42 |  214.30 |
+---------+---------+
1 row in set (0.001 sec)
*/

```

Note - Max and min function can be applied on varchar also, it consider string length for calculation.


### COUNT(), AVG() and SUM() Functions

COUNT - returns no of rows that matches a specified criterion.
AVG - returns the average value of a numeric column.
SUM - returns the SUM of values of numeric column.

SELECT  COUNT(_column_name_)  
FROM  _table_name_  
WHERE  _condition_;

SELECT AVG(_column_name_)  
FROM  _table_name_  
WHERE  _condition_;

SELECT SUM(_column_name_)  
FROM  _table_name_  
WHERE  _condition_;


### LIKE Operator
Used in where clause to search for a specified pattern in a column

	% 		The percent sign represents zero, one, or multiple characters

	_        The underscore represents a single character

SELECT  _column1, column2, ..._  
FROM  _table_name_  
WHERE  _columnN_  LIKE  _pattern_;

```sql
SELECT * FROM Customers  
WHERE CustomerName LIKE  '%a';

SELECT * FROM Customers  
WHERE CustomerName LIKE  '%or%';

```

### Wildcard Characters

	% 		Represent zero or more characters
	
	_  		Represent a single character
	
	[] 		Represent any single character within the bracket - Not supported in MySQL

	^     	Represents any character not in the brackets

	`-`     Range of characters- [a-z]

```sql

SELECT * FROM Customers  
WHERE City LIKE  '[!bsp]%';

SELECT * FROM Customers  
WHERE City LIKE  '[bsp]%';

SELECT * FROM Customers  
WHERE City NOT  LIKE  '[bsp]%';
```

### SQL IN Operator

The IN operator allows you to specify multiple values in a WHERE clause.
The IN operator is a shorthand for multiple OR conditions.

SELECT  _column_name(s)_  
FROM  _table_name_  
WHERE  _column_name_  IN (_value1_, _value2_, ...);

or

SELECT  _column_name(s)_  
FROM  _table_name_  
WHERE  _column_name_  IN (_SELECT  STATEMENT_);

```sql
SELECT * FROM Customers  
WHERE Country IN ('Germany', 'France', 'UK');

SELECT * FROM Customers  
WHERE Country NOT  IN ('Germany', 'France', 'UK');

SELECT * FROM Customers  
WHERE Country IN (SELECT Country FROM Suppliers);
```

### BETWEEN

The BETWEEN operator selects values within a given range. The values can be numbers, text, or dates.

The BETWEEN operator is inclusive: begin and end values are included.

SELECT  _column_name(s)_  
FROM  _table_name_  
WHERE  _column_name_ BETWEEN  _value1_  AND  _value2;_


```sql

SELECT * FROM Products  
WHERE Price NOT  BETWEEN  10  AND  20;

SELECT * FROM Products  
WHERE Price NOT  BETWEEN  10  AND  20;

SELECT * FROM Products  
WHERE Price NOT  BETWEEN  10  AND  20;

```

### Aliases

SELECT  _column_name_  AS  _alias_name_  
FROM  _table_name;_

```sql

SELECT CustomerID AS ID, CustomerName AS Customer  
FROM Customers;

SELECT CustomerName AS Customer, ContactName AS [Contact Person]  
FROM Customers;

SELECT o.OrderID, o.OrderDate, c.CustomerName  
FROM Customers AS c, Orders AS o  
WHERE c.CustomerName='Around the Horn'  AND c.CustomerID=o.CustomerID;

```

JOINS in SQL

A JOIN clause is used to combine rows from two or more tables, based on a related column between them.




## Stored Procedure


MySQL Delimiter

A mysql client program like Workbench, heidiSQL or mysql uses ; as default delemiter but since store proceduce have multiptle statements which may have special charecter and delemiter (;) and in such case program will not treat it as a single statement but multiple statements, therefore we change delimiter temporarily.

DELEMITER /  -> change delemiter as '/'
DELEMITER ;  -> Reset delemiter to ;



Create Store Procedure in MySQL

```sql

DELIMITER //

CREATE PROCEDURE simpleproc (OUT param1 INT) BEGIN
    SELECT COUNT(*) INTO param1 FROM t;
END;
//
DELIMITER ;



DELIMITER //

CREATE PROCEDURE listProds() BEGIN
	SELECT * FROM products;
END
//

DELIMITER ;


-- calling procedures

CALL listProds();


-- Creating Procedure with param

DELIMITER $$

CREATE PROCEDURE showAll(tbl_name varchar(40) ) 

BEGIN
	SET @t1 = CONCAT('SELECT * from ', tbl_name);
	PREPARE stmt from @t1;
	EXECUTE stmt;
	DEALLOCATE stmt;
END $$


--- Manage Procedure

SHOW PROCEDURE status;

-- Delete stored procedure

DROP PROCEDURE simpleproc;

-- Print procedure definition

SELECT ROUTINE_DEFINITION FROM INFORMATION_SCHEMA.ROUTINES
WHERE ROUTINE_SCHEMA = 'classicmodels' AND ROUTINE_TYPE = 'PROCEDURE' AND ROUTINE_NAME = "fisrProc";


-- call procedure/execute

CALL simpleproc;

```

Stored Procedures in SQL-SERVER

```sql

CREATE PROCEDURE firstProc
AS
SELECT * FROM products;
GO;

-- execute procedure
exec firstProc


-- Stored procedure with parameters

CREATE PROCEDURE SelectAllCustomers @City nvarchar(30)
AS
SELECT * FROM Customers WHERE City = @City
GO;


EXEC SelectAllCustomers @City = 'London';


-- Stored procedure with multiple parameters

CREATE PROCEDURE SelectAllCustomers @City nvarchar(30), @PostalCode nvarchar(10)
AS
SELECT * FROM Customers WHERE City = @City AND PostalCode = @PostalCode
GO;

EXEC SelectAllCustomers @City = 'London', @PostalCode = 'WA1 1DP';

```
