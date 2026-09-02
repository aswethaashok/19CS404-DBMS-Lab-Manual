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

How many appointments are scheduled for each doctor?

Sample table:Appointments Table

<img width="983" height="166" alt="image" src="https://github.com/user-attachments/assets/66da647f-cf07-4215-93a7-f7f9083f14ea" />


For example:

##### Result
DoctorID    TotalAppointments
----------  -----------------
3           3
4           2
6           1
7           3
10          1

#### Code:
```
SELECT DoctorID, COUNT(*) AS TotalAppointments
FROM Appointments 
GROUP BY DoctorID;
```

**Output:**

<img width="712" height="711" alt="image" src="https://github.com/user-attachments/assets/ad5b9c60-f5fe-4ef6-afc0-4659e33a3fea" />


**Question 2**

How many medical records does each doctor have?

Sample table:MedicalRecords Table

<img width="969" height="154" alt="image" src="https://github.com/user-attachments/assets/02c6443a-6b1e-4d7c-9fc8-a7e10c66a24b" />


For example:

##### Result

DoctorID    TotalRecords
----------  ------------
3           4
5           1
6           1
7           1
8           3

#### Code:
```
SELECT DoctorID, COUNT(*) AS TotalRecords
FROM MedicalRecords 
GROUP BY DoctorID;
```

**Output:**
<img width="619" height="708" alt="image" src="https://github.com/user-attachments/assets/aac7d9d0-08e1-49d8-807d-27be9cf0ccfb" />


**Question 3**

How many doctors specialize in each medical specialty?

Sample table:Doctors Table

<img width="982" height="160" alt="image" src="https://github.com/user-attachments/assets/f126d293-b3a7-4d1a-a210-adb3559638c6" />


For example:

##### Result
Specialty          TotalDocto
-----------------  ----------
Gastroenterology   1
Neurology          1
Obstetrics         3
Ophthalmology      1
Orthopedics        1
Pediatrics         2
Urology            1

#### Code:
```
SELECT Specialty, COUNT(*) AS TotalDocto
FROM Doctors 
GROUP BY Specialty;
```

**Output:**

<img width="718" height="759" alt="image" src="https://github.com/user-attachments/assets/0df74e09-0152-49ff-813e-f39cc92f24e2" />


**Question 4**

Write a SQL query to calculate total available amount of fruits that has a price greater than 0.5 . Return total Count. 

Note: Inventory attribute contains amount of fruits

Table: fruits

name        type
----------  ----------
id          INTEGER
name        TEXT
unit        TEXT
inventory   INTEGER
price       REAL
 

For example:

##### Result
total_available_amount
----------------------
160

#### Code:
```
SELECT SUM(inventory) AS total_available_amount
FROM fruits
WHERE price>0.5;
```


**Output:**

<img width="581" height="384" alt="image" src="https://github.com/user-attachments/assets/ef41a895-ae08-48f6-ac17-489131720e54" />





**Question 5**

Write a SQL query to Calculate the average email length (in characters) for people who lives in Mumbai city

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT   
city        TEXT
email       TEXT
phone       INTEGER
For example:

##### Result
avg_email_length_below_30
-------------------------
14.0

#### Code:
```
SELECT AVG(LENGTH(email)) AS avg_email_length_below_30
FROM customer
WHERE city='Mumbai';
```

**Output:**

<img width="633" height="378" alt="image" src="https://github.com/user-attachments/assets/d76316ee-1f3d-4e77-922e-50fe439bb63b" />


**Question 6**
Write a SQL query to find the average length of email addresses (in characters):

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER
For example:

##### Result
avg_email_length
----------------
15.0

#### Code:
```
SELECT AVG(LENGTH(email)) AS avg_email_length
FROM customer;
```

**Output:**


<img width="461" height="379" alt="image" src="https://github.com/user-attachments/assets/b11a6672-3acd-44d4-8bbb-13b330d0e510" />


**Question 7**

Write a SQL query to find  how many employees work in California?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
 

For example:

##### Result
employees_in_california
-----------------------
2

#### Code:
```
SELECT COUNT(*) AS employees_in_california
FROM employee
WHERE city='California';
```

**Output:**


<img width="581" height="377" alt="image" src="https://github.com/user-attachments/assets/10c27cbf-254d-4143-9280-a49ccf0d2032" />


**Question 8**

Write a SQL query to identify the cities (addresses) where the average salary is greater than Rs. 5000, as per the "customer1" table.

Sample table: customer1

<img width="785" height="148" alt="image" src="https://github.com/user-attachments/assets/a8ad6814-7e6c-467f-ab83-3b0fde583286" />


For example:

##### Result
address     AVG(salary)
----------  -----------
Bhopal      8500.0
Indore      10000.0
Mumbai      6500.0

#### Code:
```
SELECT address, AVG(salary)
FROM customer1
GROUP BY address
HAVING AVG(salary)>5000;
```

**Output:**


<img width="599" height="504" alt="image" src="https://github.com/user-attachments/assets/331cf975-0441-424a-998a-649895be3700" />


**Question 9**

Write the SQL query that accomplishes the grouping of data by age, calculates the average income for each age group, and includes only those age groups where the average income falls between 300,000 and 500,000.

Sample table: employee

<img width="788" height="174" alt="image" src="https://github.com/user-attachments/assets/290c4cf7-056e-40d9-a59c-8d1dadf46d2f" />


For example:

##### Result
age         AVG(income)
----------  -----------
45          450000.0

#### Code:
```
SELECT age, AVG(income)
FROM employee
GROUP BY age
HAVING AVG(income) BETWEEN 300000 AND 500000;
```

**Output:**

<img width="591" height="398" alt="image" src="https://github.com/user-attachments/assets/6a0f26f6-0981-4418-bd85-ad4bd73836c0" />


**Question 10**

Write the SQL query that achieves the selection of product names and the maximum price for each category from the "products" table, and includes only those products where the maximum price is greater than 15.

Sample table: products

<img width="789" height="178" alt="image" src="https://github.com/user-attachments/assets/c966ea68-54cc-4b9e-bc03-9b01733c628a" />


For example:

##### Result
category_id  product_name  Price
-----------  ------------  ----------
1            Orange        15.5
2            Monitor       25

#### Code:
```
SELECT category_id, product_name, MAX(price) AS Price
FROM products
GROUP BY category_id
HAVING MAX(price)>15;
```

**Output:**

<img width="845" height="450" alt="image" src="https://github.com/user-attachments/assets/7574f72a-ae4d-41b5-a3e6-2778d6c87737" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.


