# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
<img width="965" height="219" alt="Screenshot 2026-03-09 154511" src="https://github.com/user-attachments/assets/6f3b2d87-ccf1-4172-960a-d2fbd3f17747" />


```sql
SELECT Frequency,
COUNT(*) AS TotalPrescriptions
FROM Prescriptions
GROUP BY Frequency;
```

**Output:**

<img width="1245" height="610" alt="Screenshot 2026-03-09 154636" src="https://github.com/user-attachments/assets/377e5146-4e4e-461f-9b4a-332722acb6a5" />


**Question 2**
---
<img width="970" height="229" alt="Screenshot 2026-03-09 154642" src="https://github.com/user-attachments/assets/0479829c-1a69-41fb-b9dd-d532d46e94a0" />


```sql
SELECT Medication,
COUNT(*) AS TotalPrescriptions
FROM Prescriptions
GROUP BY Medication;
```

**Output:**

<img width="1264" height="806" alt="Screenshot 2026-03-09 154656" src="https://github.com/user-attachments/assets/3548f9e7-a04b-4d5f-bf1a-5bd82ee83e43" />


**Question 3**
---
What is the average duration of insurance coverage for patients covered by each insurance company?
```
Sample table:Insurance Table

name               type
-----------------  ----------
InsuranceID        INTEGER
PatientID          INTEGER
InsuranceCompany   TEXT
PolicyNumber       TEXT
PolicyHolder       TEXT
StartDate          DATE
EndDate            DATE
```
```sql
SELECT InsuranceCompany,
AVG(EndDate-StartDate) AS AvgCoverageDurationDays
FROM Insurance
GROUP BY InsuranceCompany
ORDER BY InsuranceCompany;
```

**Output:**

<img width="1228" height="735" alt="Screenshot 2026-03-09 154709" src="https://github.com/user-attachments/assets/e1dedac7-763f-4346-86ac-3357d979494a" />


**Question 4**
---
<img width="1113" height="299" alt="Screenshot 2026-03-09 154717" src="https://github.com/user-attachments/assets/1f06c70f-04c9-4e23-a384-7d4bcf447b54" />


```sql
SELECT 
    SUM(workhour) AS "Total working hours"
FROM employee1;
```

**Output:**

<img width="1114" height="397" alt="Screenshot 2026-03-09 154723" src="https://github.com/user-attachments/assets/962278c4-38b1-482f-af12-0b44661692b3" />


**Question 5**
---
Write a SQL query to calculate the average purchase amount of all orders. Return average purchase amount.
```
Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001
```
```sql
SELECT 
    AVG(purch_amt) AS AVERAGE
FROM orders;
```

**Output:**

<img width="1227" height="379" alt="Screenshot 2026-03-09 154734" src="https://github.com/user-attachments/assets/0ce3f20e-3974-4897-aa1c-a1ab5a70914d" />


**Question 6**
---
Write a SQL query to find the number of employees who are having the same age removing the duplicate values.
```
Sample table: employee

id   name   age   address     salary
1    Paul   32    California  20000
4    Mark   25    Richtown    65000
5    David  27    Texas       85000
```
```sql
SELECT 
    COUNT(DISTINCT age) AS COUNT
FROM employee;
```

**Output:**

<img width="1234" height="386" alt="Screenshot 2026-03-09 154745" src="https://github.com/user-attachments/assets/60285c26-4a98-4b92-8265-1af82ae54690" />

**Question 7**
---
Write a SQL query that counts the number of unique salespeople. Return number of salespeople.
```
Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001
```
```sql
SELECT 
    COUNT(DISTINCT salesman_id) AS COUNT
FROM orders;
```

**Output:**

<img width="1212" height="392" alt="Screenshot 2026-03-09 154752" src="https://github.com/user-attachments/assets/34694573-5227-4ff4-9ee9-e8f1028daafe" />


**Question 8**
---
<img width="1249" height="274" alt="Screenshot 2026-03-09 154759" src="https://github.com/user-attachments/assets/0aa0cbf2-e4eb-4673-a54f-f558aa259b28" />


```sql
SELECT jdate,
     AVG(workhour) AS "AVG(workhour)"
FROM employee1
GROUP BY jdate
HAVING AVG(workhour)<10;
```

**Output:**

<img width="1246" height="406" alt="Screenshot 2026-03-09 154806" src="https://github.com/user-attachments/assets/8798e5f4-3ec0-4f91-86f2-bf84c4b59537" />

**Question 9**
---
<img width="1243" height="300" alt="Screenshot 2026-03-09 154813" src="https://github.com/user-attachments/assets/62b3dcfb-a07d-4a5f-b798-217d44aa4190" />


```sql
SELECT category_id,
COUNT(*) AS "count(product_name)"
FROM products
GROUP BY category_id
HAVING category_id<3;
```

**Output:**

<img width="1236" height="432" alt="Screenshot 2026-03-09 154820" src="https://github.com/user-attachments/assets/f3ee6a42-3d85-40d7-b765-1e39c61ce137" />


**Question 10**
---
<img width="1243" height="261" alt="Screenshot 2026-03-09 154826" src="https://github.com/user-attachments/assets/139199c8-4c4f-491b-b04f-e3353bcbafba" />


```sql
SELECT 
(age/5)*5 AS age_group,
MIN(salary) AS "MIN(salary)"
FROM customer1
GROUP BY age_group
HAVING MIN(salary)<2000;
```

**Output:**

<img width="1219" height="411" alt="Screenshot 2026-03-09 154835" src="https://github.com/user-attachments/assets/54405cb1-ef78-4df9-8c03-91b16bb5bf76" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
