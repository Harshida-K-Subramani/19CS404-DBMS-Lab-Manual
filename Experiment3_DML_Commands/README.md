# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
Write a SQL statement to Change the category to 'Household' where product name contains 'Detergent' in the products table.
```
Products Table 

name          type       
----------    ---------- 
product_id     INT PRIMARY KEY        
product_name   VARCHAR(10) 
category       VARCHAR(50) 
cost_price     DECIMAL(10) 
sell_price     DECIMAL(10) 
reorder_lvl    INT        
quantity       INT        
supplier_id    INT
```
```sql
UPDATE Products
SET category='Household'
WHERE product_name LIKE '%Deter%';
```

**Output:**

<img width="1244" height="576" alt="Screenshot 2026-03-09 143636" src="https://github.com/user-attachments/assets/0b4598c8-ca3f-4a60-bbab-53e272fe4a20" />


**Question 2**
---
Write a SQL statement to Update the product_name to 'Premium Bread' whose product ID is 5 in the products table.
```
Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id
```
```sql
UPDATE Products
SET product_name ='Premium Bread'
WHERE product_id=5;
```

**Output:**

<img width="1238" height="486" alt="Screenshot 2026-03-09 143736" src="https://github.com/user-attachments/assets/b2c73d51-a4d4-4dce-8807-ed6999920328" />


**Question 3**
---
Write a SQL statement to Increase the selling price by 10% for all products in the 'Bakery' category in the products table.
```
Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id
```
```sql
UPDATE Products
SET sell_price = sell_price*1.10
WHERE category='Bakery';
```

**Output:**

<img width="1250" height="601" alt="Screenshot 2026-03-09 143818" src="https://github.com/user-attachments/assets/0e9410db-eeff-4ea4-aa49-6bc110faf061" />


**Question 4**
---
Write a SQL statement to change the first_name column of employees table with 'John' for those employees whose department_id is 80 and gets a commission_pct below 0.35.
```
Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id
```
```sql
UPDATE Employees
SET first_name='John'
WHERE department_id=80
    AND commission_pct<0.35;
```

**Output:**

<img width="1239" height="619" alt="Screenshot 2026-03-09 143916" src="https://github.com/user-attachments/assets/84560a21-4df3-4ab7-9f6a-7e635c3fe449" />


**Question 5**
---
Update the 'Selling_Price' to add 10% extra margin for all products supplied by the supplier with id 6.
```
PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT
```
```sql
UPDATE Products
SET sell_price=ROUND(sell_price*1.10)
WHERE supplier_id=6;
```

**Output:**

<img width="1239" height="613" alt="Screenshot 2026-03-09 144021" src="https://github.com/user-attachments/assets/06fc6a88-0829-40f6-8a5b-c456144dd43d" />


**Question 6**
---
Write a SQL query to Delete All Doctors with a NULL Specialization
```
Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization
```
```sql
DELETE FROM doctors
WHERE specialization IS NULL;
```

**Output:**

<img width="1238" height="827" alt="Screenshot 2026-03-09 144110" src="https://github.com/user-attachments/assets/2f73c4c1-29a4-4365-9d39-2e6f57d1979a" />


**Question 7**
Write a SQL query to Delete customers with 'CUST_COUNTRY' 'UK' and 'WORKING_AREA' 'London' whose 'GRADE' is less than 3

```sql
DELETE FROM Customer
WHERE CUST_COUNTRY='UK'
    AND WORKING_AREA='London'
    AND GRADE<3
```

**Output:**

<img width="1276" height="566" alt="Screenshot 2026-03-09 144226" src="https://github.com/user-attachments/assets/7ceac759-a9ed-442f-ba85-1b303f99184c" />


**Question 8**
---
Write a SQL query to Delete customers with 'GRADE' 3 or 'AGENT_CODE' 'A008' whose 'OUTSTANDING_AMT' is less than 5000

```sql
DELETE FROM Customer
WHERE (GRADE=3 OR AGENT_CODE='A008') 
    AND OUTSTANDING_AMT<5000;
```

**Output:**

<img width="1243" height="483" alt="Screenshot 2026-03-09 144312" src="https://github.com/user-attachments/assets/4710c075-c646-4a91-af89-759cf07c3d74" />


**Question 9**
---
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is less than 2.

 
Sample table: Customer

```sql
DELETE FROM customer
WHERE GRADE<2;
```

**Output:**

<img width="1233" height="621" alt="Screenshot 2026-03-09 144408" src="https://github.com/user-attachments/assets/49b1fd5b-31a6-4616-baa6-f5fe1a1f9ab6" />


**Question 10**
---
Write a SQL query to Delete a Specific Surgery whose ID is 3

Sample table: Surgeries

attributes: surgery_id, patient_id, surgeon_id, surgery_date

```sql
DELETE FROM surgeries
WHERE surgery_id=3;
```

**Output:**

<img width="1252" height="464" alt="Screenshot 2026-03-09 144456" src="https://github.com/user-attachments/assets/c49a3a2a-ae0f-40c8-a947-6d64290e0001" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
