# (Half-baked) SQL tutorial (or) SQL Cheatsheet
* The only SQL tutorial/cheatsheet you'll ever need.
* Syllabus designed based on tutorial from [w3schools.com](https://www.w3schools.com/sql/)


![img](images/sql.jpg)

## SQL (Structured Query Language)
### What is SQL?
* Language used to create, access and manage databases.
* Trivia: It became an ANSI/ISO (American National Standard Institute and International Organization for Standardization) .

### Requirements for SQL
* RDBMS (Relational Database Management System) like MS Access, MySQL, SQL Serer, Oracle, IBM DB2.
* Server-side scripting language such as PHP, ASP
* SQL
* HTML/CSS for front-end visualization

### Basic Terminologies 101
* Table (Collection of rows and columns)
* Field/Fields
* Rows/Record

## SQL Commands

* #### SQL Select

Semicolon is required to seperate different SQL commands. SQL is case in-sensitive.
```
SELECT * FROM Customers;
SELECT column1, column2 FROM table_name;
```
* #### SQL SELECT DISTINCT

Displays only the unique results, without duplicates.
```
SELECT DISTINCT * FROM CUSTOMERS;
SELECT DISTINCT CustomerName, ContactName FROM CUSTOMERS;
SELECT COUNT (DISTINCT CustomerName) FROM CUSTOMERS;
```
* #### SQL WHERE CLAUSE
```
SELECT * FROM CUSTOMERS WHERE CUSTOMERID IS 1;
SELECT * FROM CUSTOMERS WHERE CITY IS "London";
```
* #### SQL AND, OR, NOT CLAUSE
```
SELECT * FROM CUSTOMERS WHERE CITY IS "London" AND CUSTOMERID IS 4;
SELECT * FROM CUSTOMERS WHERE CITY IS "London" OR CUSTOMERID IS 3;
SELECT * FROM CUSTOMERS WHERE NOT CUSTOMERID IS 3;
```
* #### Combining AND, OR, NOT
```
SELECT * FROM CUSTOMERS WHERE CustomerID IS 1 AND (CITY IS "London" OR CITY IS "Berlin");
SELECT * FROM CUSTOMERS WHERE NOT COUNTRY IS "Germany" OR (CustomerName IS "Maria Anders" AND CITY IS "Berlin");

```
* #### SQL ORDER BY CLAUSE

Used to order the result either in ascending or descending order
```
SELECT * FROM Customers ORDER BY CONTACTNAME DESC;
SELECT * FROM Customers ORDER BY CUSTOMERID ASC;
```
* #### INSERT INTO 

Used to insert values into columns/fields of the table
```
INSERT INTO CUSTOMERS (CustomerID, CustomerName, ContactName, Address, City, PostalCode, Country) VALUES ('100', 'Sai Adarsh', 'Adarsh', 'Velachery', 'Chennai', '600088', 'India');
INSERT INTO CUSTOMERS (CustomerID, CustomerName, ContactName) VALUES ('100', 'Sai Adarsh', 'Adarsh');

```
* #### NULL CLAUSE

Used to display null or empty
```
SELECT * FROM CUSTOMERS WHERE CUSTOMERID IS NULL;
SELECT CUSTOMERNAME FROM CUSTOMERS WHERE CITY IS NOT NULL;
```
* #### UPDATE CLAUSE
Used to update the DataBase or table
```
UPDATE table_name SET column1, column2 WHERE CustomerID is 10;
```

* #### DELETE CLAUSE
Used to delete the Database or table
```
DELETE FROM CUSTOMERS WHERE CUSTOMERID IS "1009";
DELETE FROM CUSTOMERS
```

* #### LIMIT CLAUSE
Used to display top N records from the database or table
```
SELECT * FROM CUSTOMERS LIMIT 5;
SELECT CUSTOMERID FROM CUSTOMERS WHERE CITY IS "London" LIMIT 5;
```

* #### SQL Functions
COUNT(): ```SELECT COUNT(*) FROM CUSTOMERS;``` \
SUM(): ```SELECT COUNT(*) FROM CUSTOMERS;```  \
AVG(): ```SELECT AVG(*) FROM CUSTOMERS;```  \
MIN(): ```SELECT MIN(CustomerID) FROM CUSTOMERS;```  \
MAX(): ```SELECT MAX(CustomerID) FROM CUSTOMERS;```

* #### LIKE, NOT LIKE CLAUSE
Used to filter based on initial, end and in-between occurences of strings
```
SELECT * FROM CUSTOMERS WHERE CustomerName LIKE "a%";
SELECT * FROM CUSTOMERS WHERE CustomerName LIKE "%a";
SELECT * FROM CUSTOMERS WHERE CustomerName LIKE "%a%";
SELECT * FROM CUSTOMERS WHERE CustomerName LIKE "a%b";
SELECT * FROM CUSTOMERS WHERE CustomerName NOT LIKE "a%";
SELECT * FROM CUSTOMERS WHERE CustomerName LIKE "_a";
```

* #### WILDCARDS CLAUSE
Used for string and substring based conditional-filtering
```
SELECT * FROM CUSTOMERS WHERE CustomerName LIKE "[acs]%";
SELECT * FROM CUSTOMERS WHERE CustomerName LIKE "[a-f]%";
SELECT * FROM CUSTOMERS WHERE CustomerName LIKE "[!acf]%";
```

* #### IN, NOT IN CLAUSE
Checks if present in
```
SELECT * FROM CUSTOMERS WHERE COUNTRY IN ('Germany', 'Norway');
SELECT * FROM CUSTOMERS WHERE COUNTRY NOT IN ('Germany', 'Norway');
SELECT * FROM CUSTOMERS WHERE COUNTRY IN (SELECT COUNTRY FROM SUPPLIERS);
```

* #### COMMENTS IN SQL
Single line comments
```
-- SELECT * FROM CUSTOMERS;
SELECT COLUMN1 FROM CUSTOMERS
```
Multi-line comments
```
/* Something in line 1
Something in line 2 */
```
* #### SQL UNION
Used to combine the result-set of two tables
``` SELECT COLUMN1, COLUMN2 FROM TABLE1
UNION
SELECT COUMN1, COLUMN2 FROM TABLE2
```
Includes Duplicates
```
SELECT COLUMN1, COLUMN2 FROM TABLE1
UNION ALL
SELECT COUMN1, COLUMN2 FROM TABLE2;

SELECT COLUMN1, COLUMN2 FROM TABLE1
UNION
SELECT COUMN1, COLUMN2 FROM TABLE2
ORDER BY COLUMN1;

SELECT COLUMN1, COLUMN2 FROM TABLE1 WHERE COLUMN1 IS ""
UNION
SELECT COUMN1, COLUMN2 FROM TABLE2 WHERE COLUMN1 IS ""
ORDER BY COLUMN1;

SELECT COLUMN1, COLUMN2 FROM TABLE1 WHERE COLUMN1 IS ""
UNION ALL
SELECT COUMN1, COLUMN2 FROM TABLE2 WHERE COLUMN1 IS ""
ORDER BY COLUMN1;
```
* #### SQL HAVING CLAUSE
Used to add conditional queries to aggregate functions
``` SELECT DEPT_NAME, AVG(SALARY) FROM INSTRUCTOR GROUP BY ""
DEPT_NAME HAVING AVG(SALARY)>40000;
```
