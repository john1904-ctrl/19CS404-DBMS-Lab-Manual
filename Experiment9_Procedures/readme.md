# Experiment 9: PL/SQL – Procedures and Functions

## AIM
To understand and implement procedures and functions in PL/SQL for performing various operations such as calculations, decision-making, and looping.

---

## THEORY

PL/SQL (Procedural Language/SQL) extends SQL by adding procedural constructs like variables, conditions, loops, procedures, and functions. Procedures and functions are subprograms that help modularize the code and improve reusability.

### **Procedure**
A PL/SQL **procedure** is a subprogram that performs a specific action. It does not return a value directly but can return values using `OUT` parameters.

**Syntax:**
```sql
CREATE OR REPLACE PROCEDURE procedure_name (parameters)
IS
BEGIN
   -- statements
END;
```

To call the procedure

```sql
EXEC procedure_name(arguments);
```

### **Function**
A PL/SQL **function** is a subprogram that returns a single value using the RETURN keyword.

```sql
CREATE OR REPLACE FUNCTION function_name (parameters)
RETURN datatype
IS
BEGIN
   -- statements
   RETURN value;
END;
```

To call the function:

```sql
SELECT function_name(arguments) FROM DUAL;
```

Key Differences:

-A procedure does not return a value, whereas a function must return a value.
-Functions can be called from SQL queries, procedures cannot (in most cases).

## 1. Write a PL/SQL Procedure to Find the Square of a Number

### Steps:
- Create a procedure named `find_square`.
- Declare a parameter to accept a number.
- Inside the procedure, compute the square of the input number.
- Use `DBMS_OUTPUT.PUT_LINE` to display the result.
- Call the procedure with a number as input.

**Expected Output:**  
Square of 6 is 36

### CODE:
```
SET SERVEROUTPUT ON;

CREATE OR REPLACE PROCEDURE find_square (n IN NUMBER)
IS
    result NUMBER;
BEGIN
    result := n * n;
    DBMS_OUTPUT.PUT_LINE('Square of ' || n || ' is ' || result);
END;
/
```
``` sql
EXEC find_square(6);
```

### OUTPUT:
<img width="1002" height="954" alt="image" src="https://github.com/user-attachments/assets/6cfbba9e-1b32-4e48-9228-7fa438711ab7" />

---

## 2. Write a PL/SQL Function to Return the Factorial of a Number

### Steps:
- Create a function named `get_factorial`.
- Declare a parameter to accept a number.
- Use a loop to calculate the factorial.
- Return the result using the `RETURN` statement.
- Call the function using a `SELECT` statement or in an anonymous block.

**Expected Output:**  
Factorial of 5 is 120

### CODE:
```
CREATE OR REPLACE FUNCTION get_factorial (n IN NUMBER)
RETURN NUMBER
IS
    fact NUMBER := 1;
BEGIN
    FOR i IN 1..n LOOP
        fact := fact * i;
    END LOOP;

    RETURN fact;
END;
/
```
```sql
SELECT get_factorial(5) AS factorial FROM dual;
```

### OUTPUT:
<img width="1007" height="850" alt="image" src="https://github.com/user-attachments/assets/f48024cc-43d1-4cc7-9736-61979210a4f3" />

---

## 3. Write a PL/SQL Procedure to Check Whether a Number is Even or Odd

### Steps:
- Create a procedure named `check_even_odd`.
- Accept an input parameter.
- Use the `MOD` function to check if the number is divisible by 2.
- Display whether it is Even or Odd using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
12 is Even

### CODE:
```
SET SERVEROUTPUT ON;

CREATE OR REPLACE PROCEDURE check_even_odd (n IN NUMBER)
IS
BEGIN
    IF MOD(n,2) = 0 THEN
        DBMS_OUTPUT.PUT_LINE(n || ' is Even');
    ELSE
        DBMS_OUTPUT.PUT_LINE(n || ' is Odd');
    END IF;
END;
/
```
```sql
EXEC check_even_odd(12);
```

### OUTPUT:
<img width="1017" height="970" alt="image" src="https://github.com/user-attachments/assets/c222eaf8-1e48-4ea3-94be-7b9cd7cacb05" />

---

## 4. Write a PL/SQL Function to Return the Reverse of a Number

### Steps:
- Create a function named `reverse_number`.
- Accept an input number as parameter.
- Use a loop to reverse the digits of the number.
- Return the reversed number.
- Call the function and display the output.

**Expected Output:**  
Reversed number of 1234 is 4321

### CODE:
```
CREATE OR REPLACE FUNCTION reverse_number (n IN NUMBER)
RETURN NUMBER
IS
    num NUMBER := n;
    rev NUMBER := 0;
    rem NUMBER;
BEGIN
    WHILE num > 0 LOOP
        rem := MOD(num,10);
        rev := rev * 10 + rem;
        num := TRUNC(num/10);
    END LOOP;

    RETURN rev;
END;
/
```
```sql
SELECT reverse_number(1234) AS reversed_number FROM dual;
```

### OUTPUT:
<img width="1006" height="902" alt="image" src="https://github.com/user-attachments/assets/b57d06b0-b48e-40c5-a9ac-bebce5db5691" />

---

## 5. Write a PL/SQL Procedure to Display the Multiplication Table of a Number

### Steps:
- Create a procedure named `print_table`.
- Accept an input number.
- Use a loop from 1 to 10 to multiply the input number.
- Display the multiplication results using `DBMS_OUTPUT.PUT_LINE`.

**Expected Output:**  
Multiplication table of 5:  
5 x 1 = 5  
5 x 2 = 10  
5 x 3 = 15  
...  
5 x 10 = 50

### CODE:
```
SET SERVEROUTPUT ON;

CREATE OR REPLACE PROCEDURE print_table (n IN NUMBER)
IS
BEGIN
    DBMS_OUTPUT.PUT_LINE('Multiplication table of ' || n || ':');

    FOR i IN 1..10 LOOP
        DBMS_OUTPUT.PUT_LINE(n || ' x ' || i || ' = ' || (n*i));
    END LOOP;
END;
/
```
```sql
EXEC print_table(5);
```

### OUTPUT:
<img width="1009" height="975" alt="image" src="https://github.com/user-attachments/assets/40920149-1b1e-4745-ab25-46eb12c8457a" />

## RESULT
Thus, the PL/SQL programs using procedures and functions were written, compiled, and executed successfully.
