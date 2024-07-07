Q1. What is a database? Differentiate between SQL and NoSQL databases.
A database is an organized collection of structured information, or data, typically stored electronically in a computer system. Databases are managed using a database management system (DBMS).

Differences between SQL and NoSQL databases:
Data Model:

SQL: Relational databases (RDBMS) store data in tables with rows and columns. Each table has a fixed schema.
NoSQL: Non-relational databases can store data in various ways, such as key-value pairs, wide-column stores, document stores, or graph databases. They are schema-less or have a flexible schema.
Schema:

SQL: Requires a predefined schema before inserting data. Changes to the schema can be complex and involve downtime.
NoSQL: Typically schema-less, allowing for dynamic schema changes without downtime.
Query Language:

SQL: Uses Structured Query Language (SQL) for defining and manipulating data.
NoSQL: Uses various query languages depending on the database type, often providing a more flexible querying approach.
Scalability:

SQL: Typically vertically scalable, meaning you increase the capacity of a single server.
NoSQL: Typically horizontally scalable, meaning you add more servers to handle increased load.
ACID vs. BASE:

SQL: Follows the ACID (Atomicity, Consistency, Isolation, Durability) properties to ensure reliable transactions.
NoSQL: Follows the BASE (Basically Available, Soft state, Eventual consistency) properties, providing high availability and eventual consistency.
Q2. What is DDL? Explain why CREATE, DROP, ALTER, and TRUNCATE are used with an example.
DDL (Data Definition Language) is a subset of SQL used to define, alter, and manage database structures.

CREATE: Used to create a new database, table, index, or other database object.

sql
Copy code
CREATE TABLE Employees (
    EmployeeID int,
    FirstName varchar(255),
    LastName varchar(255),
    BirthDate date
);
DROP: Used to delete an existing database, table, index, or other database object.

sql
Copy code
DROP TABLE Employees;
ALTER: Used to modify an existing database object, such as a table.

sql
Copy code
ALTER TABLE Employees
ADD Email varchar(255);
TRUNCATE: Used to remove all records from a table, but the table structure remains.

sql
Copy code
TRUNCATE TABLE Employees;
Q3. What is DML? Explain INSERT, UPDATE, and DELETE with an example.
DML (Data Manipulation Language) is a subset of SQL used to insert, update, delete, and retrieve data within a database.

INSERT: Adds new records to a table.

sql
Copy code
INSERT INTO Employees (EmployeeID, FirstName, LastName, BirthDate)
VALUES (1, 'John', 'Doe', '1980-01-01');
UPDATE: Modifies existing records in a table.

sql
Copy code
UPDATE Employees
SET Email = 'john.doe@example.com'
WHERE EmployeeID = 1;
DELETE: Removes existing records from a table.

sql
Copy code
DELETE FROM Employees
WHERE EmployeeID = 1;
Q4. What is DQL? Explain SELECT with an example.
DQL (Data Query Language) is a subset of SQL used to retrieve data from a database.

SELECT: Retrieves data from one or more tables.
sql
Copy code
SELECT FirstName, LastName, BirthDate
FROM Employees
WHERE EmployeeID = 1;
Q5. Explain Primary Key and Foreign Key.
Primary Key: A field (or combination of fields) in a table that uniquely identifies each row/record in that table. Each table can have only one primary key, and the primary key cannot contain NULL values.

sql
Copy code
CREATE TABLE Employees (
    EmployeeID int PRIMARY KEY,
    FirstName varchar(255),
    LastName varchar(255),
    BirthDate date
);
Foreign Key: A field (or combination of fields) in a table that creates a link between the data in two tables. The foreign key in the child table references the primary key in the parent table.

sql
Copy code
CREATE TABLE Orders (
    OrderID int PRIMARY KEY,
    OrderDate date,
    EmployeeID int,
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)
);
Q6. Write a Python code to connect MySQL to Python. Explain the cursor() and execute() methods.
python
Copy code
import mysql.connector

# Establish the connection
conn = mysql.connector.connect(
    host='localhost',
    user='root',
    password='password',
    database='testdb'
)

# Create a cursor object
cursor = conn.cursor()

# Execute an SQL query
cursor.execute("SELECT * FROM Employees")

# Fetch all results
results = cursor.fetchall()

for row in results:
    print(row)

# Close the cursor and connection
cursor.close()
conn.close()
cursor(): This method creates a cursor object, which is used to execute SQL queries and fetch data from the database.
execute(): This method is used to execute a single SQL query, such as SELECT, INSERT, UPDATE, or DELETE.
Q7. Give the order of execution of SQL clauses in an SQL query.
The order of execution of SQL clauses in a query is as follows:

FROM: Specifies the tables to retrieve data from.
JOIN: Combines rows from two or more tables based on a related column.
WHERE: Filters the rows based on a specified condition.
GROUP BY: Groups rows sharing a property so aggregate functions can be applied to each group.
HAVING: Filters groups based on a specified condition.
SELECT: Specifies the columns to be returned.
DISTINCT: Removes duplicate rows from the result.
ORDER BY: Specifies the order of the returned rows.
LIMIT: Specifies the maximum number of rows to return.
