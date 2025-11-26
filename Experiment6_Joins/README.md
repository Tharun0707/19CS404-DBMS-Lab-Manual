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
From the following tables write a SQL query to locate those salespeople who do not live in the same city where their customers live and have received a commission of more than 12% from the company. Return Customer Name, customer city, Salesman, salesman city, commission.  

```
SELECT
  T1.cust_name AS "Customer Name",
  T1.city AS "city",
  T2.name AS "Salesman",
  T2.city AS "city",
  T2.commission
FROM
  customer AS T1
INNER JOIN
  salesman AS T2
  ON T1.salesman_id = T2.salesman_id
WHERE
  T1.city <> T2.city
  AND T2.commission > 0.12;
```

**Output:**



<img width="1314" height="500" alt="image" src="https://github.com/user-attachments/assets/9344e719-3e96-4862-bd78-b6d069381248" />


**Question 2**
---
Write the SQL query that achieves the selection of all columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column and a condition filtering for salesman with the name 'Mc Lyon'.


```
SELECT
  c.*
FROM
  customer AS c
LEFT JOIN
  salesman AS s
  ON c.salesman_id = s.salesman_id
WHERE
  s.name = 'Mc Lyon';
```

**Output:**


<img width="1314" height="319" alt="image" src="https://github.com/user-attachments/assets/a142452c-ad60-4ca7-beb6-4fcde2495216" />



**Question 3**
---
 From the following tables write a SQL query to find salespeople who received commissions of more than 12 percent from the company. Return Customer Name, customer city, Salesman, commission.  

```
SELECT
  T1.cust_name AS "Customer Name",
  T1.city AS "city",
  T2.name AS "Salesman",
  T2.commission
FROM
  customer AS T1
INNER JOIN
  salesman AS T2
  ON T1.salesman_id = T2.salesman_id
WHERE
  T2.commission > 0.12;
```

**Output:**


<img width="1317" height="619" alt="image" src="https://github.com/user-attachments/assets/bfd13716-d842-494f-974e-5e65ac54470e" />


**Question 4**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and all columns from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column and a condition filtering for test results with the test name 'Blood Pressure'.

```
SELECT
  p.first_name AS patient_name,
  t.*
FROM
  patients AS p
INNER JOIN
  test_results AS t
  ON p.patient_id = t.patient_id
WHERE
  t.test_name = 'Blood Pressure';
```

**Output:**


<img width="1311" height="341" alt="image" src="https://github.com/user-attachments/assets/7922edcb-d747-4057-b753-bcc68f30f65a" />


**Question 5**
---
Write an SQL query to select all columns from the 'customer' table (aliased as 'c') by performing a LEFT JOIN with the 'orders' table on the 'customer_id' column, including only those orders where the order date falls between '2012-08-01' and '2012-08-30'.

```
SELECT
  c.*
FROM
  customer AS c
LEFT JOIN
  orders AS o
  ON c.customer_id = o.customer_id
WHERE
  o.ord_date BETWEEN '2012-08-01' AND '2012-08-30';
```

**Output:**


<img width="1308" height="379" alt="image" src="https://github.com/user-attachments/assets/97aaef63-29ec-4f59-a404-853dbb9c0f39" />


**Question 6**
---
 From the following tables write a SQL query to find the salesperson(s) and the customer(s) he represents. Return Customer Name, city, Salesman, commission.

```
SELECT
  T1.cust_name AS "Customer Name",
  T1.city AS "city",
  T2.name AS "Salesman",
  T2.commission
FROM
  customer AS T1
INNER JOIN
  salesman AS T2
  ON T1.salesman_id = T2.salesman_id;
```

**Output:**


<img width="1312" height="730" alt="image" src="https://github.com/user-attachments/assets/40959947-c192-4d95-825f-23bd9ef5c5cd" />


**Question 7**
---
Write the SQL query that achieves the selection of all columns from the "patients" table and the specialization from the "doctors" table (aliased as "doctor_specialization"), with an inner join on the "doctor_id" column.

```
SELECT
  p.*,
  d.specialization AS doctor_specialization
FROM
  patients AS p
INNER JOIN
  doctors AS d
  ON p.doctor_id = d.doctor_id;
```

**Output:**


<img width="1306" height="459" alt="image" src="https://github.com/user-attachments/assets/d7c7f86f-8fcf-464f-aa61-80564c54f3ba" />


**Question 8**
---
From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id. 

```
SELECT
  T1.cust_name AS "cust_name",
  T1.city AS "city",
  T1.grade AS "grade",
  T2.name AS "Salesman",
  T2.city AS "city"
FROM
  customer AS T1
INNER JOIN
  salesman AS T2
  ON T1.salesman_id = T2.salesman_id
WHERE
  T1.grade < 300 OR T1.grade IS NULL
ORDER BY
  T1.customer_id ASC;
```

**Output:**


<img width="1316" height="623" alt="image" src="https://github.com/user-attachments/assets/bd87291c-2016-41a1-9bec-4f8225d41d58" />


**Question 9**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the test name from the "test_results" table (aliased as "t"), with an inner join on the "patient_id" column.

```
SELECT
  p.first_name AS patient_name,
  t.test_name
FROM
  patients AS p
INNER JOIN
  test_results AS t
  ON p.patient_id = t.patient_id;
```

**Output:**


<img width="634" height="439" alt="image" src="https://github.com/user-attachments/assets/f51898d4-aaf3-4855-be02-e1a8199df232" />



**Question 10**
---
Write a SQL statement to make a report with customer name, city, order number, order date, and order amount in ascending order according to the order date to determine whether any of the existing customers have placed an order or not.

```
SELECT
  T1.cust_name AS "cust_name",
  T1.city AS "city",
  T2.ord_no AS "ord_no",
  T2.ord_date AS "ord_date",
  T2.purch_amt AS "Order Amount"
FROM
  customer AS T1
LEFT JOIN
  orders AS T2
  ON T1.customer_id = T2.customer_id
ORDER BY
  T2.ord_date ASC;
```

**Output:**


<img width="1354" height="774" alt="image" src="https://github.com/user-attachments/assets/0a481700-8dff-4919-999c-3b519f9753bf" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
