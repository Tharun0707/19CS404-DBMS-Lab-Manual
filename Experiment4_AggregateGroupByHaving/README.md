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
Write a SQL Query to find how many medications are prescribed for each patient?

```
SELECT
    PatientID,
    COUNT(DISTINCT Medications) AS AvgMedications
FROM
    MedicalRecords
GROUP BY
    PatientID
ORDER BY
    PatientID;
```

**Output:**


<img width="1281" height="485" alt="image" src="https://github.com/user-attachments/assets/8274a289-efd0-458a-bda9-578527103114" />


**Question 2**
---
How many medical records does each doctor have?
For example:

Result
DoctorID    TotalRecords
----------  ------------
3           4
5           1
6           1
7           1
8           3

```
SELECT
    DoctorID,
    COUNT(*) AS TotalRecords
FROM
    MedicalRecords
GROUP BY
    DoctorID
ORDER BY
    DoctorID;
```

**Output:**


<img width="1268" height="504" alt="image" src="https://github.com/user-attachments/assets/9547b400-8a4e-421d-9e99-9d4b4f55cacb" />


**Question 3**
---
Write a SQL query to calculate the total number of working hours of all employees
For example:
Result
Total working hours
-------------------
111

```
SELECT SUM(workhour) AS "Total working hours"
FROM
    employee1;
```

**Output:**


<img width="1277" height="254" alt="image" src="https://github.com/user-attachments/assets/625187f3-19b2-4986-be6f-9f3bfd215617" />


**Question 4**
---
Write a SQL query to find What is the age difference between the youngest and oldest employee in the company.

For example:

Result

age_difference

--------------
13


```
SELECT
    MAX(age) -
    MIN(age) AS age_difference
FROM
    employee;
```

**Output:**


<img width="1273" height="250" alt="image" src="https://github.com/user-attachments/assets/fca431de-b773-4622-ab91-a0bda712b8d4" />


**Question 5**
---
Write a SQL query to find the average length of names for people living in Chennai?
For example:

Result
avg_name_length
---------------
10.0

```
SELECT
    AVG(LENGTH(name)) AS avg_name_length
FROM
    customer
WHERE
    city = 'Chennai';
```

**Output:**


<img width="1270" height="252" alt="image" src="https://github.com/user-attachments/assets/bce2da29-130d-4711-9b98-a08478c2e055" />


**Question 6**
---
Write a SQL query to Calculate the average email length (in characters) for people who lives in Mumbai city
For example:

Result
avg_email_length_below_30
-------------------------
14.0

```
SELECT
    AVG(LENGTH(email)) AS avg_email_length_below_30
FROM
    customer
WHERE
    city = 'Mumbai';
```

**Output:**


<img width="1268" height="243" alt="image" src="https://github.com/user-attachments/assets/ba30b565-65b2-4f28-a098-29f10ec04fe9" />


**Question 7**
---
Write the SQL query to find how many patients have more than 3 medical records?.
For example:

Result
PatientID   TotalRecords
----------  ------------
1           4


```
SELECT
    PatientID,
    COUNT(RecordID) AS TotalRecords 
FROM
    MedicalRecords
GROUP BY
    PatientID
HAVING
    COUNT(RecordID) > 3;
```

**Output:**


<img width="1275" height="280" alt="image" src="https://github.com/user-attachments/assets/5f6acc3e-ed8d-473c-a576-7b9c54329b87" />


**Question 8**
---
Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the average age for each group, and excludes groups where the average age is not less than 24.
For example:

Result
age_group   AVG(age)
----------  ----------
20          23.0


```
SELECT
    (age / 5) * 5 AS age_group,
    AVG(age)
FROM
    customer1
GROUP BY
    age_group
HAVING
    AVG(age) < 24;
```

**Output:**


<img width="540" height="247" alt="image" src="https://github.com/user-attachments/assets/ee7e67b8-2451-49f1-937e-f08bec692b4b" />


**Question 9**
---
Write the SQL query that achieves the grouping of data by city, calculates the average income for each city, and includes only those cities where the average income is greater than 500,000.
For example:

Result
city        AVG(income)
----------  -----------
Arizona     1000000.0
California  2650000.0
Florida     2675000.0


```
SELECT
    city,
    AVG(income)
FROM
    employee
GROUP BY
    city
HAVING
    AVG(income) > 500000;
```

**Output:**


<img width="528" height="358" alt="image" src="https://github.com/user-attachments/assets/97a8ee55-f6a9-449a-ba2f-38b5af7678fe" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
