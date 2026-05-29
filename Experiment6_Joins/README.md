# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
Write the SQL query that achieves the selection of all columns from the "patients" table (aliased as "p"), with an inner join on the "patient_id" column and a condition filtering for appointments with an appointment date between '2024-02-01' and '2024-02-28'.

PATIENTS TABLE:



APPOINTMENTS TABLE:



```sql
SELECT p.*
FROM patients p
INNER JOIN appointments a
ON p.patient_id = a.patient_id
WHERE a.appointment_date BETWEEN '2024-02-01' AND '2024-02-28';
```

**Output:**

<img width="833" height="489" alt="image" src="https://github.com/user-attachments/assets/2d814e5d-2398-418a-b625-08cf8b5b5bb6" />


**Question 2**
---
Write the SQL query that achieves the selection of all columns from the "patients" table (aliased as "p"), with an inner join on the "patient_id" column and conditions filtering for test results with the test names 'Blood Test' or 'Blood Pressure' and results not containing the substring 'Normal'.

PATIENTS TABLE:



TEST_RESULT TABLES:



```sql
SELECT p.*
FROM patients p
INNER JOIN test_results t
ON p.patient_id = t.patient_id
WHERE (t.test_name = 'Blood Test' OR t.test_name = 'Blood Pressure')
AND t.result NOT LIKE '%Normal%';

```

**Output:**

<img width="840" height="500" alt="image" src="https://github.com/user-attachments/assets/344a4bb2-2ff2-42d1-a600-219251024704" />


**Question 3**
---
Write the SQL query that achieves the selection of all columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column and a condition filtering for salesmen with the name 'Mc Lyon'.

Customer Table:



Salesmen Table:



```sql
SELECT c.*
FROM customer c
LEFT JOIN salesman s
ON c.salesman_id = s.salesman_id
WHERE s.name = 'Mc Lyon';
```

**Output:**

<img width="838" height="485" alt="image" src="https://github.com/user-attachments/assets/041c2f84-d139-454e-9f67-34ef5809af91" />


**Question 4**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and all columns from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column.

PATIENTS TABLE:



TEST_RESULT TABLES:



```sql
SELECT p.first_name AS patient_name,
       t.*
FROM patients p
INNER JOIN test_results t
ON p.patient_id = t.patient_id
```

**Output:**

<img width="828" height="619" alt="image" src="https://github.com/user-attachments/assets/e16e1b1d-4d48-4722-a1a5-4e0bccb4d7cd" />


**Question 5**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name"), with an inner join on the "doctor_id" column and conditions filtering for patients whose doctor has the first name 'Emily', last name 'Johnson', and a non-null discharge date.

PATIENTS TABLE:



DOCTORS TABLE:



```sql
SELECT p.first_name AS patient_name
FROM patients p
INNER JOIN doctors d
ON p.doctor_id = d.doctor_id
WHERE (d.first_name = 'Emily' AND d.last_name = 'Johnson')
AND p.discharge_date IS NOT NULL;
```

**Output:**

<img width="687" height="468" alt="image" src="https://github.com/user-attachments/assets/a24e71ae-796f-46ba-a580-748103ced945" />


**Question 6**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the test name from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column.

PATIENTS TABLE:



TEST_RESULT TABLES:



```sql
SELECT p.first_name AS patient_name, t.test_name
FROM patients p
INNER JOIN test_results t
ON p.patient_id = t.patient_id

```

**Output:**

<img width="841" height="614" alt="image" src="https://github.com/user-attachments/assets/3854822e-fd70-4b70-88b5-02a91f556a69" />


**Question 7**
---
Write the SQL query that achieves the selection of the "cust_name" and "city" columns from the "customer" table (aliased as "c"), and the "ord_no," "ord_date," and "purch_amt" columns from the "orders" table (aliased as "o"), with a left join on the "customer_id" column and a condition filtering for customers in the city 'London'.

CUSTOMER TABLE:



ORDERS TABLE:



```sql
SELECT c.cust_name,c.city,o.ord_no,o.ord_date,o.purch_amt
FROM customer c
LEFT JOIN orders o
ON c.customer_id = o.customer_id
WHERE c.city = 'London';
```

**Output:**

<img width="826" height="567" alt="image" src="https://github.com/user-attachments/assets/4704a991-081e-40e7-ba0e-658d75aa2b93" />


**Question 8**
---
Write the SQL query that achieves the selection of the date of birth from the "patients" table (aliased as "p") and all columns from the "appointments" table (aliased as "a"), with an inner join on the "patient_id" column and a condition filtering for patients with the first name 'Alice'.

PATIENTS TABLE:



APPOINTMENTS TABLE:



```sql
SELECT p.date_of_birth,a.*
FROM patients p
INNER JOIN appointments a
ON p.patient_id = a.patient_id
WHERE p.first_name = 'Alice'
```

**Output:**

<img width="837" height="501" alt="image" src="https://github.com/user-attachments/assets/f5ca2780-5fe1-49ac-b1ed-d7130e044f88" />


**Question 9**
---
Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), the "cust_name," "city," "grade," and "salesman_id" columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column and a condition filtering for customers with a grade less than or equal to 100.

Customer Table:



Salesmen Table:



```sql
SELECT s.name,c.cust_name,c.city,c.grade,c.salesman_id
FROM salesman s
LEFT JOIN customer c
ON s.salesman_id = c.salesman_id
WHERE c.grade <= 100
```

**Output:**

<img width="827" height="635" alt="image" src="https://github.com/user-attachments/assets/3cef3e31-56c8-4593-89b9-1d7ade18454b" />


**Question 10**
---
Write the SQL query that accomplishes the selection of the first name and last name from the "patients" table, with an inner join on the "patient_id" column and a condition filtering for surgeries with a surgery date between '2024-01-01' and '2024-01-31'.

PATIENTS TABLE:

name             type
---------------  ---------------
patient_id       INT
first_name       VARCHAR(50)
last_name        VARCHAR(50)
date_of_birth    DATE
admission_date   DATE
discharge_date   DATE
doctor_id        INT

SURGERIES TABLE:

name             type
---------------  ---------------
surgery_id       INT
patient_id       INT
surgeon_id       INT
surgery_date     DATE

```sql
SELECT p.first_name,p.last_name
FROM patients p
INNER JOIN surgeries s
ON p.patient_id = s.patient_id
WHERE s.surgery_date BETWEEN '2024-01-01' AND '2024-01-31';
```

**Output:**

<img width="834" height="480" alt="image" src="https://github.com/user-attachments/assets/852ddd36-7606-4257-b1af-b7073417d215" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
