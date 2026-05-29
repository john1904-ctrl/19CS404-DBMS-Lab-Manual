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
Write a SQL query to remove rows from the table 'customer' with the following condition -

1. 'cust_city' should begin with the letter 'L',

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |


```sql
DELETE FROM customer
WHERE cust_city LIKE 'L%';

```

**Output:**

<img width="836" height="875" alt="image" src="https://github.com/user-attachments/assets/aeb116f5-59c3-4725-b128-f6e1683e536d" />


**Question 2**
---
Write a SQL statement to Double the salary for employees in department 20 who have a job_id ending with 'MAN'


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

```sql
UPDATE employees
SET salary = salary * 2
WHERE department_id = 20
AND job_id LIKE '%MAN';

```

**Output:**

<img width="835" height="435" alt="image" src="https://github.com/user-attachments/assets/038aa877-b216-44d3-a18f-8ff56fb4919a" />


**Question 3**
---
Write a SQL statement to Change the supplier name to 'A1 Suppliers' where the supplier ID is 8 in the suppliers table.

Table info

suppliers(supplier_id,supplier_name,contact_person,phone_number,email,address)

```sql
UPDATE suppliers
SET supplier_name = 'A1 Suppliers'
WHERE supplier_id = 8;

```

**Output:**

<img width="834" height="472" alt="image" src="https://github.com/user-attachments/assets/98b5e735-7236-44a4-ab02-45585be5bf8a" />


**Question 4**
---
Write a SQL query to find all employees who were hired in the last 6 months from the emp table. 

Note: Assume current date as '01-09-2024'

emp table

cid         name        type        
----------  ----------  ---------- 
0           empno       INT         
1           ename       VARCHAR(100)
2           job         VARCHAR(50)
3           mgr         INT        
4           hiredate    DATE        
5           sal         DECIMAL(10,2)  
6           comm        DECIMAL(10,2)  
7           deptno      INT      

```sql
SELECT *
FROM emp
WHERE hiredate BETWEEN '2024-03-01' AND '2024-09-01';

```

**Output:**

<img width="842" height="430" alt="image" src="https://github.com/user-attachments/assets/90d7d118-fe9c-425b-9614-5cf7268b1f32" />


**Question 5**
---
Write a SQL statement to Update the product_name to 'Premium Bread' whose product ID is 5 in the products table.

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

```sql
UPDATE products
SET product_name = 'Premium Bread'
WHERE product_id = 5;

```

**Output:**

<img width="832" height="485" alt="image" src="https://github.com/user-attachments/assets/5fbd1bbb-00fc-4264-bcac-935121275f07" />


**Question 6**
---
Write a SQL query to find customers who are either from the city 'New York' or who do not have a grade greater than 100. Return customer_id, cust_name, city, grade, and salesman_id.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002

```sql
SELECT customer_id, cust_name, city, grade, salesman_id
FROM customer
WHERE city = 'New York'
OR grade <= 100;

```

**Output:**

<img width="824" height="496" alt="image" src="https://github.com/user-attachments/assets/ad34fccb-f2f1-4c77-a8d9-b454b88c0504" />


**Question 7**
---
Write a SQL query to calculate the original price using the discount percentage and the given discounted price. Return product_id, discounted_price, discount_percentage, and original_price.

Sample table: Products

product_id | discounted_price | discount_percentage

 ------------+------------------+---------------------

 101 | 45.00 | 0.10 

102 | 63.75 | 0.15 

103 | 80.00 | 0.20

```sql
SELECT 
    product_id,
    discounted_price,
    discount_percentage,
    discounted_price / (1 - discount_percentage) AS original_price
FROM Products;

```

**Output:**

<img width="835" height="377" alt="image" src="https://github.com/user-attachments/assets/6876208f-0845-4e5d-a033-9630ccb9b841" />


**Question 8**
---
For  Increase the selling price per unit by 3 for all products supplied by supplier ID 4 in the sales table.

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

SALES TABLE
name               type
-----------------  ---------------
sale_id            INT
sale_date          DATE
product_id         INT
quantity           INT
sell_price         DECIMAL(10,2)
total_sell_price   DECIMAL(10,2)

```sql
UPDATE sales
SET sell_price = sell_price + 3
WHERE product_id IN (
    SELECT product_id
    FROM products
    WHERE supplier_id = 4
);

```

**Output:**

<img width="838" height="445" alt="image" src="https://github.com/user-attachments/assets/84c41f61-387e-4144-855e-13d7f8aedee1" />


**Question 9**
---
Write a SQL query to find the details of those salespeople who live in cities other than Paris and Rome. Return salesman_id, name, city, commission.

Sample table: salesman

 salesman_id |    name    |   city   | commission 
-------------+------------+----------+------------
        5001 | James Hoog | New York |       0.15
        5002 | Nail Knite | Paris    |       0.13
        5005 | Pit Alex   | London   |       0.11

```sql
SELECT salesman_id, name, city, commission
FROM salesman
WHERE city NOT IN ('Paris', 'Rome');

```

**Output:**

<img width="834" height="481" alt="image" src="https://github.com/user-attachments/assets/cc55c5d7-bae0-4b20-a76c-cdd195eab879" />


**Question 10**
---
Write a SQL query to Delete all Doctors whose Specialization is either 'Pediatrics' or 'Cardiology' and Last Name is Brown.

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization
For example:

Test	Result
SELECT * FROM doctors;
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology
2           Emily       Johnson     Orthopedics
3           Michael     Brown       Pediatrics
doctor_id   first_name  last_name   specialization
----------  ----------  ----------  --------------
1           John        Smith       Cardiology
2           Emily       Johnson     Orthopedics


```sql
DELETE FROM doctors
WHERE specialization IN ('Pediatrics', 'Cardiology')
AND last_name = 'Brown';

```

**Output:**

<img width="823" height="912" alt="image" src="https://github.com/user-attachments/assets/e6971145-cb64-46f5-be27-b4f4dcffb8db" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
