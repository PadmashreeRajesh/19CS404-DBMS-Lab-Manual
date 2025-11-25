# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
-- 
```
Create a table named Bonuses with the following constraints:
BonusID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
BonusAmount as REAL should be greater than 0.
BonusDate as DATE.
Reason as TEXT should not be NULL.
Test	Result
INSERT INTO Bonuses (BonusID, EmployeeID, BonusAmount, BonusDate, Reason) VALUES (1, 6, 1000.0, '2024-08-01', 'Outstanding performance');
SELECT * FROM Bonuses;
BonusID     EmployeeID  BonusAmount  BonusDate   Reason
----------  ----------  -----------  ----------  -----------------------
1           6           1000.0       2024-08-01  Outstanding performance
```

```sql
CREATE TABLE Bonuses(
    BonusID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    BonusAmount REAL CHECK(BonusAmount>0),
    BonusDate DATE,
    Reason TEXT NOT NULL,
    FOREIGN KEY (EmployeeID) references employees(EmployeeID)
);
```

**Output:**

<img width="1301" height="296" alt="image" src="https://github.com/user-attachments/assets/204ca95d-8a61-4d73-aa23-0f29f3a0d7fd" />


**Question 2**
---
 ```
Insert the below data into the Customers table, allowing the City and ZipCode columns to take their default values.

CustomerID  Name          Address
----------  ------------  ----------
304         Peter Parker  Spider St      

Note: The City and ZipCode columns will use their default values.
 
For example:

Test	Result
SELECT CustomerID, Name, Address
FROM Customers;
CustomerID  Name          Address
----------  ------------  ----------
304         Peter Parker  Spider St

```

```sql
INSERT INTO Customers(CustomerID,Name,Address)
VALUES('304','Peter Parker','Spider St');
```

**Output:**

<img width="971" height="316" alt="image" src="https://github.com/user-attachments/assets/2b605fbb-33c6-4209-94d7-df22e1a968f7" />


**Question 3**
---
```
Create a table named Departments with the following columns:

DepartmentID as INTEGER
DepartmentName as TEXT
For example:

Test	Result
pragma table_info('Departments');
cid    name             type        notnull     dflt_value  pk
-----  ---------------  ----------  ----------  ----------  ----------
0      DepartmentID     INTEGER     0                       0
1      DepartmentName   TEXT        0                       0
```
```sql
CREATE TABLE Departments(
     DepartmentID INTEGER,
     DepartmentName TEXT
);
```

**Output:**

<img width="1282" height="351" alt="image" src="https://github.com/user-attachments/assets/b3cb5f3c-4d57-4c23-a6bd-9fb7462f78fa" />


**Question 4**
---
```
In the Employee table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

EmployeeID  Name          Position    Department  Salary
----------  ------------  ----------  ----------  ----------
5           George Clark  Consultant
7           Noah Davis    Manager     HR          60000
8           Ava Miller    Consultant  IT
 

For example:

Test	Result
SELECT * FROM Employee;
EmployeeID  Name          Position    Department  Salary
----------  ------------  ----------  ----------  ----------
5           George Clark  Consultant
7           Noah Davis    Manager     HR          60000
8           Ava Miller    Consultant  IT
```

```sql
INSERT INTO Employee(EmployeeID,Name,Position,Department,Salary)
    VALUES(5,'George Clark','Consultant',NULL,NULL),
          (7,'Noah Davis','Manager','HR','60000'),
          (8,'Ava Miller','Consultant','IT',NULL);
```

**Output:**

<img width="1290" height="281" alt="image" src="https://github.com/user-attachments/assets/343d9265-5f66-404b-8135-e1b47abd1217" />


**Question 5**
---
```
Insert all products from Discontinued_products into Products.

Table attributes are ProductID, ProductName, Price, Stock

For example:

Test	Result
select * from Products;
ProductID   ProductName     Price       Stock
----------  --------------  ----------  ----------
101         Old Smartphone  199.99      0
102         Vintage Laptop  399.99      10
103         Classic Tablet  149.99      5
```

```sql
INSERT INTO Products(ProductID,ProductName,Price,Stock)
SELECT ProductID,ProductName,Price,Stock FROM Discontinued_products
```

**Output:**

<img width="1071" height="269" alt="image" src="https://github.com/user-attachments/assets/3f2ee8e9-8c46-4a9e-8dfc-a36bc1fe152b" />


**Question 6**
---
```
Create a table named Employees with the following constraints:

EmployeeID should be the primary key.
FirstName and LastName should be NOT NULL.
Email should be unique.
Salary should be greater than 0.
DepartmentID should be a foreign key referencing the Departments table.
For example:

Test	Result
-- Attempt to insert a record with NULL FirstName
INSERT INTO Employees (EmployeeID, FirstName, LastName, Email, Salary, DepartmentID)
VALUES (1, NULL, 'Doe', 'john.doe@example.com', 50000, 1);
Error: NOT NULL constraint failed: Employees.FirstName

```

```sql
CREATE TABLE Employees(
    EmployeeID PRIMARY KEY,
    FirstName VARCHAR(20) NOT NULL,
    LastName VARCHAR(20) NOT NULL,
    Email VARCHAR(50) UNIQUE,
    Salary CHECK(Salary>0),
    DepartmentID Int,
    FOREIGN KEY(DepartmentID)REFERENCES Departments(DepartmentID)
);
```

**Output:**

<img width="1271" height="402" alt="image" src="https://github.com/user-attachments/assets/2162120b-e3b1-402a-a1f1-6d791744c453" />


**Question 7**
---
```
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should set NULL on updates and deletes.
item_desc and rate should not accept NULL.
For example:

Test	Result
INSERT INTO item VALUES("ITM5","Charlie Gold",700,"COM4");
UPDATE company SET com_id='COM5' WHERE com_id='COM4';
SELECT * FROM item;
item_id     item_desc     rate        icom_id
----------  ------------  ----------  ----------
ITM5        Charlie Gold  700

```

```sql
CREATE TABLE item(
    item_id TEXT PRIMARY KEY,
    item_desc TEXT,
    rate INTEGER,
    icom_id TEXT(4),
    FOREIGN KEY(icom_id)REFERENCES company(com_id)
    ON UPDATE SET NULL
    ON DELETE SET NULL
);
```

**Output:**

<img width="1281" height="331" alt="image" src="https://github.com/user-attachments/assets/a03a73af-ecd9-4729-91c7-90747e7d8c84" />


**Question 8**
---
```
Write an SQL command can to add a column named email of type TEXT to the customers table
For example:
Test	Result
pragma table_info('Customers');
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          integer     0                       0
1           name        text        0                       0
2           email       TEXT        0                       0
```

```sql
ALTER TABLE customers ADD COLUMN email TEXT;
```

**Output:**

<img width="1279" height="308" alt="image" src="https://github.com/user-attachments/assets/eae43c73-df78-4a4c-b419-3a5f1b224577" />


**Question 9**
---
```
Write an SQL query to add a new column salary of type INTEGER to the Employees table, with a CHECK constraint that ensures the value in this column is greater than 0.
For example:
Test	Result
pragma table_info('employees');
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          INTEGER     0                       1
1           name        TEXT        1                       0
2           salary      INTEGER     0                       0
```

```sql
ALTER TABLE employees
ADD COLUMN salary INTEGER CHECK (salary>0);
```

**Output:**

<img width="1291" height="300" alt="image" src="https://github.com/user-attachments/assets/31d8bb5a-7339-49ad-95a9-d978df3beac5" />


**Question 10**
---
```
Create a table named Products with the following constraints:

ProductID should be the primary key.
ProductName should be NOT NULL.
Price is of real datatype and should be greater than 0.
Stock is of integer datatype and should be greater than or equal to 0.
For example:

Test	Result
INSERT INTO Products
VALUES (1, NULL,0,5);
Error: NOT NULL constraint failed: Products.ProductName
```

```sql
CREATE TABLE Products(
   ProductID PRIMARY KEY,
   ProductName NOT NULL,
   Price REAL CHECK(Price>0),
   Stock INTEGER CHECK(Stock>=0)
);
```

**Output:**

<img width="1208" height="268" alt="image" src="https://github.com/user-attachments/assets/88293c7c-a849-480f-ad29-06b7ac03c2e2" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
