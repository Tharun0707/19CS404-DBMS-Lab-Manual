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
Write a SQL statement to change the email column of employees table with 'Unavailable' for all employees in employees table.
For example:

Test	Result
SELECT EMPLOYEE_ID,FIRST_NAME,EMAIL FROM EMPLOYEES LIMIT 2;
EMPLOYEE_ID  FIRST_NAME  EMAIL
-----------  ----------  -----------
100          Steven      Unavailable
101          Neena       Unavailable


```
UPDATE employees
SET email = 'Unavailable';
```

**Output:**


<img width="1289" height="351" alt="image" src="https://github.com/user-attachments/assets/eb0746e8-1af8-43b3-89b5-f62d841a9739" />



**Question 2**
---
Increase the reorder level by 30% for products from 'Food' category having quantity in stock less than 50% of existing reorder level in the products table
For example:

Test	Result
select changes();
changes()
----------
4


```
UPDATE products
SET reorder_lvl = reorder_lvl * 1.30
WHERE category = 'Food'
  AND quantity < reorder_lvl * 0.50;
```

**Output:**


<img width="1271" height="324" alt="image" src="https://github.com/user-attachments/assets/506e53b0-954e-4caa-842d-e454b8f90690" />



**Question 3**
---
Write a SQL statement to change the EMAIL and COMMISSION_PCT column of the following EMPLOYEES table with 'not available' and 0.55 for those employees whose DEPARTMENT_ID is 110.
For example:

Test	Result
SELECT EMPLOYEE_ID,FIRST_NAME,EMAIL,COMMISSION_PCT FROM EMPLOYEES 
WHERE DEPARTMENT_ID=110 LIMIT 1;
EMPLOYEE_ID  FIRST_NAME  EMAIL          COMMISSION_PCT
-----------  ----------  -------------  --------------
205          Shelley     not available  0.55


```
UPDATE EMPLOYEES
SET
    email = 'not available',
    commission_pct = 0.55
WHERE
    department_id = 110;
```

**Output:**

<img width="1274" height="308" alt="image" src="https://github.com/user-attachments/assets/dea77cb5-9183-43b8-bd1b-59553526fa90" />


**Question 4**
---
Change the supplier name to upper case where contact person contains ' Singh' in suppliers table.
For example:

Test	Result
select changes();
changes()
-----------------
2


```
UPDATE suppliers
SET supplier_name = UPPER(supplier_name)
WHERE contact_person LIKE '% Singh%';
```

**Output:**


<img width="1269" height="283" alt="image" src="https://github.com/user-attachments/assets/a6ae677a-bab9-46bb-afeb-47cf64865a54" />


**Question 5**
---
Write a SQL query to reduce the reorder level by 30% where cost price is more than 50 and quantity in stock is less than 100 in the products table.
For example:
Test	Result
--pragma table_info('products');
select changes();
changes()
----------
2


```
UPDATE products
SET reorder_lvl = reorder_lvl * 0.70
WHERE cost_price > 50
  AND quantity < 100;
```

**Output:**


<img width="1273" height="365" alt="image" src="https://github.com/user-attachments/assets/49a3b86f-4431-49df-9998-b122f8eb9d52" />


**Question 6**
---
Write a SQL query to Delete customers from 'customer' table where 'OPENING_AMT' is between 4000 and 6000.

```
DELETE FROM customer
WHERE OPENING_AMT BETWEEN 4000 AND 6000;
```

**Output:**

<img width="1275" height="506" alt="image" src="https://github.com/user-attachments/assets/6f597c69-6365-49f3-b882-728fe34b978a" />


**Question 7**
---
Write a SQL query to Delete customers from 'customer' table where 'CUST_NAME' contains the substring 'Holmes'.

```
DELETE FROM customer
WHERE CUST_NAME LIKE '%Holmes%';
```

**Output:**


<img width="1270" height="446" alt="image" src="https://github.com/user-attachments/assets/5de97559-1243-42bd-9abd-711d8c9b112f" />


**Question 8**
---
Write a SQL query to Delete customers with following conditions

'CUST_COUNTRY' is not in a list of specified countries ('UK', 'USA', 'Canada')
'GRADE' is greater than or equal to 3

```
DELETE FROM customer
WHERE CUST_COUNTRY NOT IN ('UK', 'USA', 'Canada')
  AND GRADE >= 3;
```

**Output:**


<img width="1269" height="345" alt="image" src="https://github.com/user-attachments/assets/80170435-ce22-4809-89ca-a4254ee10b50" />


**Question 9**
---
Write a SQL query to remove rows from the table 'customer' with the following condition -

1. 'cust_country' must be 'India',

2. 'cus_city' must not be 'Chennai',


```
DELETE FROM customer
WHERE CUST_COUNTRY = 'India'
  AND CUST_CITY != 'Chennai';
```

**Output:**


<img width="1270" height="719" alt="image" src="https://github.com/user-attachments/assets/d31762bf-9d72-4da7-942f-40a6421eedf7" />


**Question 10**
---
Write a SQL query to Delete customers with 'GRADE' 3 or 'AGENT_CODE' 'A008' whose 'OUTSTANDING_AMT' is less than 5000

```
DELETE FROM customer
WHERE OUTSTANDING_AMT < 5000
  AND (GRADE = 3 OR AGENT_CODE = 'A008');
```

**Output:**


<img width="1263" height="324" alt="image" src="https://github.com/user-attachments/assets/7be08dc0-a39e-45fa-b5eb-5ab7896820ad" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
