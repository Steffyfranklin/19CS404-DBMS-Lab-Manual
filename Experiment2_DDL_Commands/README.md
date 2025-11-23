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
In the Cusomers table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

```sql
INSERT INTO Customers(CustomerID,Name,Address,City,ZipCode) VALUES (306,'Diana Prince','Themyscira',null,null);
INSERT INTO Customers(CustomerID,Name,Address,City,ZipCode) VALUES (307,'Bruce Wayne','Wayne Mano','Gotham',10007); 
INSERT INTO Customers(CustomerID,Name,Address,City,ZipCode) VALUES (308,'Peter Parker','Queens',null,11375);
```

**Output:**

<img width="1177" height="210" alt="image" src="https://github.com/user-attachments/assets/904c27f2-709b-481b-aea4-b26f991d808e" />

**Question 2**
---
Create a table named Orders with the following constraints:
OrderID as INTEGER should be the primary key.
OrderDate as DATE should be not NULL.
CustomerID as INTEGER should be a foreign key referencing Customers(CustomerID).

```sql
CREATE TABLE Orders(
OrderID INTEGER PRIMARY KEY,
OrderDate DATE NOT NULL,
CustomerID INTEGER,
FOREIGN KEY(CustomerID) REFERENCES Customers(CustomerID)
);
```

**Output:**

<img width="1294" height="178" alt="image" src="https://github.com/user-attachments/assets/7d7082f7-24cb-4b3d-886d-7543dadfa10a" />

**Question 3**
---
Write a SQL query to Add a new column State as text in the Student_details table.

```sql
alter TABLE Student_details
add column State TEXT;
```

**Output:**

<img width="1176" height="224" alt="image" src="https://github.com/user-attachments/assets/aaed5058-8e14-49eb-869a-ec26b7a4383a" />

**Question 4**
---
Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.

```sql
CREATE TABLE ProjectAssignments(
    AssignmentID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    ProjectID INTEGER,
    AssignmentDate DATE NOT NULL ,
    FOREIGN KEY(EmployeeID) references Employees(EmployeeID),
    FOREIGN KEY(ProjectID) references Projects(ProjectID)
);
```

**Output:**

<img width="1085" height="129" alt="image" src="https://github.com/user-attachments/assets/877ea090-2168-4355-ac8a-a28374bf6506" />

**Question 5**
---
Create a table named Tasks with the following columns:

TaskID as INTEGER
TaskName as TEXT
DueDate as DATE

```sql
CREATE TABLE Tasks(
TaskID  INTEGER,
TaskName TEXT,
DueDate DATE
);
```

**Output:**

<img width="1227" height="224" alt="image" src="https://github.com/user-attachments/assets/0e57fccc-f122-41e2-86f6-cb8e70660977" />

**Question 6**
---
Create a table named Bonuses with the following constraints:
BonusID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
BonusAmount as REAL should be greater than 0.
BonusDate as DATE.
Reason as TEXT should not be NULL.

```sql
CREATE TABLE Bonuses (
    BonusID INTEGER PRIMARY KEY,
    EmployeeID INTEGER ,
    BonusAmount REAL NOT NULL CHECK(BonusAmount>0),
    BonusDate DATE,
    Reason TEXT NOT NULL,
    FOREIGN KEY(EmployeeID) REFERENCES Employees(EmployeeID) 
);
```

**Output:**

<img width="1301" height="185" alt="image" src="https://github.com/user-attachments/assets/ab698663-978b-4a06-b800-fc7da0616476" />

**Question 7**
---
Insert all customers from Old_customers into Customers

Table attributes are CustomerID, Name, Address, Email

```sql
INSERT into Customers (CustomerID, Name, Address, Email)
SELECT CustomerID, Name, Address, Email from Old_customers
```

**Output:**

<img width="1181" height="189" alt="image" src="https://github.com/user-attachments/assets/8747deaa-5a6e-4cc7-893e-2a9f5a5a513f" />

**Question 8**
---
Create a new table named orders with the following specifications:
ord_id as TEXT with a length of 4.
item_id as TEXT.
ord_date as DATE.
ord_qty as INTEGER.
cost as INTEGER.
The primary key is a composite key consisting of item_id and ord_date.
ord_id and item_id should not accept NULL

```sql
CREATE TABLE orders(
    ord_id TEXT NOT NULL CHECK(LENGTH(ord_id)=4),
    item_id TEXT NOT NULL,
    ord_date DATE,
    ord_qty INTEGER,
    cost INTEGER,
    PRIMARY KEY (item_id, ord_date)
);
```

**Output:**

<img width="1275" height="248" alt="Screenshot 2025-11-23 160742" src="https://github.com/user-attachments/assets/6c66dd08-b504-44c4-9c5a-b5f22823c415" />

**Question 9**
---
Insert a record with EmployeeID 001, Name Sarah Parker, Position Manager, Department HR, and Salary 60000 into the Employee table.

```sql
INSERT into Employee(EmployeeID,Name,Position,Department,Salary) VALUES ("001","Sarah Parker","Manager","HR","60000");
```

**Output:**

<img width="1253" height="150" alt="image" src="https://github.com/user-attachments/assets/d398259a-12c5-418e-9c2d-1a3f867d58a6" />

**Question 10**
---
Write a SQL query to Add a new column mobilenumber as number in the Student_details table.

```sql
ALTER TABLE Student_details
ADD COLUMN mobilenumber number;
```

**Output:**

<img width="1274" height="281" alt="image" src="https://github.com/user-attachments/assets/2075bf8e-97e6-4846-95b5-c93847b09890" />

<img width="1919" height="1198" alt="Screenshot 2025-11-22 152942" src="https://github.com/user-attachments/assets/9df7e928-4762-49f4-828d-8e7f2bfc76ce" />

## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
