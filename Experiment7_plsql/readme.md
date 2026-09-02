# Experiment 7: PL/SQL – Variables, Control Structures and Loops

## AIM
To write and execute simple PL/SQL programs using variables, loops, and conditional statements.


## THEORY

PL/SQL, which stands for Procedural Language extensions to the Structured Query Language (SQL). It is a combination of SQL along with the procedural features of programming languages.

**Syntax:**
```sql
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)>
EXCEPTION 
   <exception handling> 
END;
```

### Basic Components of PL/SQL Block:
- DECLARE: Section to declare variables and constants.
- BEGIN: The execution section that contains PL/SQL statements.
- EXCEPTION: Handles errors or exceptions that occur in the program.
- END: Marks the end of the PL/SQL block.

# PL/SQL Programs – Steps and Expected Output

## 1. Write a PL/SQL program to find the Greatest of Two Numbers

### Steps:
- Declare two numeric variables and initialize them.
- Use an `IF` statement to compare the values.
- Display the greater number using `DBMS_OUTPUT.PUT_LINE`.

#### Program:

```
DECLARE
    a NUMBER := 50;
    b NUMBER := 80;
BEGIN
    IF a > b THEN
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || a);
    ELSE
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || b);
    END IF;
END;
```


**Expected Output:**  
Greater number is: 80

<img width="1016" height="740" alt="image" src="https://github.com/user-attachments/assets/dd3ded7e-3af7-4453-9c73-f449d0801f6a" />


---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.


#### Program:
```
DECLARE
    n NUMBER := 10;
    i NUMBER := 1;
    sum NUMBER := 0;
BEGIN
    WHILE i <= n LOOP
        sum := sum + i;
        i := i + 1;
    END LOOP;
    DBMS_OUTPUT.PUT_LINE('Sum of first ' || n || ' natural numbers is: ' || sum);
END;
```


**Expected Output:**  
Sum of first 10 natural numbers is: 55

<img width="994" height="724" alt="image" src="https://github.com/user-attachments/assets/799616ab-93ee-4841-8315-ac3ccfa766b1" />


---

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.

#### Program:
```
DECLARE
    n NUMBER := 7;
    a NUMBER := 0;
    b NUMBER := 1;
    c NUMBER;
    i NUMBER := 3;
BEGIN
    DBMS_OUTPUT.PUT_LINE('Fibonacci sequence:');
    DBMS_OUTPUT.PUT_LINE(a);
    DBMS_OUTPUT.PUT_LINE(b);
    WHILE i <= n LOOP
        c := a + b;
        DBMS_OUTPUT.PUT_LINE(c);
        a := b;
        b := c;
        i := i + 1;
    END LOOP;
END;
```

**Expected Output:**  
n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8

<img width="996" height="725" alt="image" src="https://github.com/user-attachments/assets/1f591a59-b91d-4099-b516-b265fac67581" />


---

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.

#### Program:
```
DECLARE
    n NUMBER := 1535;
    rev NUMBER := 0;
    r NUMBER;
    temp NUMBER := n;
BEGIN
    WHILE temp > 0 LOOP
        r := MOD(temp, 10);
        rev := rev * 10 + r;
        temp := FLOOR(temp / 10);
    END LOOP;
    DBMS_OUTPUT.PUT_LINE('Reversed number is: ' || rev);
END;
```

**Expected Output:**  
n = 1535  
Reversed number is 5351

<img width="1004" height="732" alt="image" src="https://github.com/user-attachments/assets/d73124db-bed5-4295-a183-5137377a9f88" />


---

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.

#### Program:
```
DECLARE
    a NUMBER := 10;
    b NUMBER := 9;
    c NUMBER := 15;
    max NUMBER;
BEGIN
    IF a >= b AND a >= c THEN
        max := a;
    ELSIF b >= a AND b >= c THEN
        max := b;
    ELSE
        max := c;
    END IF;
    DBMS_OUTPUT.PUT_LINE('Largest of three number is ' || max);
END;
```



**Expected Output:**  
a = 10, b = 9, c = 15  
Largest of three number is 15

<img width="989" height="712" alt="image" src="https://github.com/user-attachments/assets/02ac0b03-5d81-4d6d-9cb9-e33cf95c563a" />




---
## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.
