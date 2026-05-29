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
Write a SQL query to find the total number of unique cities in the customer table?

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER

```sql
SELECT COUNT(DISTINCT city) AS unique_cities
FROM customer;
```

**Output:**

<img width="831" height="387" alt="image" src="https://github.com/user-attachments/assets/a167bd49-5040-4745-84d3-1374f07cd5cc" />


**Question 2**
---
Write a SQL query to find the total income of employees aged 40 or above.

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER

```sql
SELECT SUM(income) AS total_income
FROM employee
WHERE age >= 40;

```

**Output:**

<img width="827" height="391" alt="image" src="https://github.com/user-attachments/assets/01e6c29d-31a5-472b-ba4d-7475a9ecfdeb" />


**Question 3**
---
Write a SQL query to find the shortest email address in the customer table?

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT   
city        TEXT
email       TEXT
phone       INTEGER

```sql
SELECT name, email, LENGTH(email) AS min_email_length
FROM customer
ORDER BY LENGTH(email)
LIMIT 1;
```

**Output:**

<img width="816" height="399" alt="image" src="https://github.com/user-attachments/assets/a3cbe7fb-5e54-47f5-81dc-7a6a1db89ad7" />


**Question 4**
---
What is the count of male and female patients?

Sample table: Patients Table



For example:

Result
Gender      TotalPatients
----------  -------------
Female      5
Male        5


```sql
SELECT Gender, COUNT(*) AS TotalPatients
FROM Patients
GROUP BY Gender;
```

**Output:**

<img width="842" height="438" alt="image" src="https://github.com/user-attachments/assets/c1e45f2a-ea0e-48cc-bfd0-403712aa7a21" />


**Question 5**
---
How many prescriptions were written in each frequency category (e.g., once daily, twice daily)?

Sample tablePrescriptions Table



```sql
SELECT Frequency, COUNT(*) AS TotalPrescriptions
FROM Prescriptions
GROUP BY Frequency;
```

**Output:**

<img width="823" height="596" alt="image" src="https://github.com/user-attachments/assets/26e7a133-8646-4ec5-b720-d1075cdc305c" />


**Question 6**
---
How many prescriptions were written by each doctor?

Sample tablePrescriptions Table



```sql
SELECT DoctorID, COUNT(*) AS TotalPrescriptions
FROM Prescriptions
GROUP BY DoctorID;
```

**Output:**

<img width="840" height="789" alt="image" src="https://github.com/user-attachments/assets/dbcbd08a-524a-4545-9cd1-ea645ea30634" />


**Question 7**
---
Write the SQL query that achieves the grouping of data by city, calculates the total income for each city, and includes only those cities where the total income sum is greater than 200,000.

Sample table: employee


```sql
SELECT city, SUM(income) AS Income
FROM employee
GROUP BY city
HAVING SUM(income) > 200000;
```

**Output:**

<img width="824" height="608" alt="image" src="https://github.com/user-attachments/assets/9c35ac7f-c21c-4bbc-95ed-9fe04d818147" />


**Question 8**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the minimum work hours for each occupation, and excludes occupations where the minimum work hour is not greater than 8.

Sample table: employee1



```sql
SELECT occupation, MIN(workhour)
FROM employee1
GROUP BY occupation
HAVING MIN(workhour) > 8;
```

**Output:**

<img width="841" height="548" alt="image" src="https://github.com/user-attachments/assets/a7935d04-3a51-4977-9d4a-250b3dc03db2" />


**Question 9**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the average work hours for each occupation, and includes only those occupations where the average work hour falls between 10 and 12.

Sample table: employee1



```sql
SELECT occupation, AVG(workhour)
FROM employee1
GROUP BY occupation
HAVING AVG(workhour) BETWEEN 10 AND 12;
```

**Output:**

<img width="829" height="462" alt="image" src="https://github.com/user-attachments/assets/4c3d81c1-5125-4342-b075-262e214cf5e4" />

**Question 10**
---
Write the SQL query that accomplishes the selection of total cost of all products in each category from the "products" table and includes only those products where the total cost is greater than 50.

Sample table: products


```sql
SELECT category_id, SUM(price) AS Total_Cost
FROM products
GROUP BY category_id
HAVING SUM(price) > 50;
```

**Output:**

<img width="826" height="401" alt="image" src="https://github.com/user-attachments/assets/29683af4-54ed-47b7-9868-1003a881259a" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
