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
create a table named jobs including columns job_id, job_title, min_salary and max_salary, and make sure that, the default value for job_title is blank and min_salary is 8000 and max_salary is NULL will be entered automatically at the time of insertion if no value assigned for the specified columns.

```sql
CREATE TABLE jobs(
    job_id INT,
    job_title VARCHAR(100) DEFAULT '',
    min_salary INT DEFAULT 8000,
    max_salary INT DEFAULT NULL
);
```

**Output:**

<img width="1244" height="408" alt="Screenshot 2026-03-09 141654" src="https://github.com/user-attachments/assets/eba7619c-3e36-4f71-8304-6ee22a90f3b9" />


**Question 2**
---
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should cascade updates and deletes.
item_desc and rate should not accept NULL.

```sql
CREATE TABLE item (
    item_id TEXT PRIMARY KEY,
    item_desc TEXT NOT NULL,
    rate INTEGER NOT NULL,
    icom_id TEXT(4),
    FOREIGN KEY (icom_id)
        REFERENCES company(com_id)
        ON UPDATE CASCADE
        ON DELETE CASCADE
);
```

**Output:**

<img width="1242" height="440" alt="Screenshot 2026-03-09 141829" src="https://github.com/user-attachments/assets/41bdcc1e-707e-488d-a928-ebd0e8859ca0" />

**Question 3**
---
Create a table named Customers with the following columns:

CustomerID as INTEGER
Name as TEXT
Email as TEXT
JoinDate as DATETIME

```sql
CREATE TABLE Customers(
    CustomerID INTEGER,
    Name TEXT,
    Email TEXT,
    JoinDate DATETIME
);
```

**Output:**

<img width="1241" height="473" alt="Screenshot 2026-03-09 141921" src="https://github.com/user-attachments/assets/ca2a9bd9-ccd9-4392-b3fe-86e79c882a0e" />


**Question 4**
---
<img width="845" height="253" alt="Screenshot 2026-03-09 142022" src="https://github.com/user-attachments/assets/0ecd5f7d-6dc1-4af6-b581-5acba010736a" />


```sql
ALTER TABLE customer
ADD COLUMN birth_date timestamp;
```

**Output:**

<img width="1238" height="439" alt="Screenshot 2026-03-09 142036" src="https://github.com/user-attachments/assets/bf1b5a2f-24b3-4cd3-af46-9437d1c6c195" />


**Question 5**
---
Write a SQL query to Add a new ParentsNumber column  as number and Adhar_Number as Number in the Student_details table.

```sql
ALTER TABLE Student_details
ADD COLUMN ParentsNumber number;
ALTER TABLE Student_details
ADD COLUMN Adhar_Number number;
```

**Output:**

<img width="1243" height="461" alt="Screenshot 2026-03-09 142200" src="https://github.com/user-attachments/assets/e6ba95a4-7a92-452f-b0b7-4d7fefc6a261" />


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
    EmployeeID INTEGER,
    BonusAmount REAL CHECK (BonusAmount > 0),
    BonusDate DATE,
    Reason TEXT NOT NULL,
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)
);
```

**Output:**

<img width="1243" height="360" alt="Screenshot 2026-03-09 142244" src="https://github.com/user-attachments/assets/42c54f1a-b283-40fc-a18f-5a712407c052" />


**Question 7**
---
Create a table named Shipments with the following constraints:
ShipmentID as INTEGER should be the primary key.
ShipmentDate as DATE.
SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID).
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).
For example:

```sql
CREATE TABLE Shipments (
    ShipmentID INTEGER PRIMARY KEY,
    ShipmentDate DATE,
    SupplierID INTEGER,
    OrderID INTEGER,
    FOREIGN KEY (SupplierID) REFERENCES Suppliers(SupplierID),
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID)
);
```

**Output:**

<img width="1239" height="322" alt="Screenshot 2026-03-09 142334" src="https://github.com/user-attachments/assets/88837b5e-ed53-44c2-b280-d6a0f240d8dd" />


**Question 8**
---
Insert a book with ISBN 978-1234567890, Title Data Science Essentials, Author Jane Doe, Publisher TechBooks, and Year 2024 into the Books table.

```sql
INSERT INTO Books ( ISBN, Title, Author, Publisher, Year)
VALUES ('978-1234567890', 'Data Science Essentials','Jane Doe', 'TechBooks',2024);
```

**Output:**

<img width="1240" height="317" alt="Screenshot 2026-03-09 142416" src="https://github.com/user-attachments/assets/4707e4d4-13b7-412c-a92d-2f28346cf345" />


**Question 9**
---
In the Employee table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.
```
EmployeeID  Name          Position    Department  Salary
----------  ------------  ----------  ----------  ----------
5           George Clark  Consultant
7           Noah Davis    Manager     HR          60000
8           Ava Miller    Consultant  IT
```

```sql
INSERT INTO Employee (EmployeeID, Name, Position, Department, Salary)
VALUES (5, 'George Clark','Consultant',NULL,NULL);
INSERT INTO Employee (EmployeeID, Name, Position, Department, Salary)
VALUES (7,'Noah Davis','Manager','HR',60000);
INSERT INTO Employee (EmployeeID, Name, Position, Department, Salary)
VALUES (8,'Ava Miller','Consultant','IT',NULL);
```

**Output:**

<img width="1248" height="368" alt="Screenshot 2026-03-09 142546" src="https://github.com/user-attachments/assets/2587b1fc-a636-4b56-bd1e-1a5974dd6f90" />


**Question 10**
---
Insert all students from Archived_students table into the Student_details table.
```
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           RollNo      INT           0                       1
1           Name        VARCHAR(100)  0                       0
2           Gender      VARCHAR(10)   0                       0
3           Subject     VARCHAR(50)   0                       0
4           MARKS       INT           0                       0
```
```sql
INSERT INTO student_details (RollNo, Name, Gender, Subject, MARKS)
SELECT RollNo, Name, Gender, Subject, MARKS
FROM Archived_students;
```

**Output:**

<img width="1244" height="366" alt="Screenshot 2026-03-09 142709" src="https://github.com/user-attachments/assets/7c1e7300-c4ff-4a2d-978b-71ab7294ec30" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
