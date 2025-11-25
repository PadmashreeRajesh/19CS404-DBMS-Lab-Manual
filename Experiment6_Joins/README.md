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
<img width="1088" height="790" alt="image" src="https://github.com/user-attachments/assets/a4e4a8f9-c42c-4a2f-892b-c3b6f71bd9ff" />


```sql
SELECT 
    o.ord_no,
    o.ord_date,
    o.purch_amt,
    c.cust_name AS "Customer Name",
    c.grade,
    s.name AS "Salesman",
    s.commission
FROM 
    orders o
JOIN 
    customer c ON o.customer_id = c.customer_id
JOIN 
    salesman s ON o.salesman_id = s.salesman_id;

```

**Output:**

<img width="1317" height="281" alt="image" src="https://github.com/user-attachments/assets/1b47a552-9542-431a-b5ac-ab0a1daa5059" />


**Question 2**
---
<img width="1116" height="607" alt="image" src="https://github.com/user-attachments/assets/57f8f612-0fce-4fed-8faf-240097e1c8cc" />


```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city,
    s.name AS "Salesman",
    s.commission
FROM 
    customer c
JOIN 
    salesman s ON c.salesman_id = s.salesman_id
WHERE 
    s.commission > 0.12;
```

**Output:**

<img width="908" height="558" alt="image" src="https://github.com/user-attachments/assets/3f0990a3-fd49-483c-937c-e7b610ecb470" />


**Question 3**
---
<img width="1358" height="524" alt="image" src="https://github.com/user-attachments/assets/fd008bb8-a85c-45a1-bb6f-14acad90cf71" />


```sql
SELECT 
    p.first_name,
    s.surgery_id,
    s.patient_id,
    s.surgeon_id,
    s.surgery_date
FROM 
    patients p
INNER JOIN 
    surgeries s ON p.patient_id = s.patient_id
WHERE 
    p.date_of_birth > '1990-01-01';
```

**Output:**

<img width="1075" height="317" alt="image" src="https://github.com/user-attachments/assets/a00d9de1-ee68-4d2d-983a-98a2776e926f" />


**Question 4**
---
<img width="1344" height="250" alt="image" src="https://github.com/user-attachments/assets/a752458a-5dba-49bf-a62a-c2d49e02b57d" />


```sql
SELECT 
    c.*
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id
WHERE 
    o.ord_date BETWEEN '2012-07-01' AND '2012-07-30';
```

**Output:**

<img width="1067" height="323" alt="image" src="https://github.com/user-attachments/assets/08d29ef7-e8e6-4c3a-9130-d5cb1c9cf57d" />


**Question 5**
---
<img width="1346" height="275" alt="image" src="https://github.com/user-attachments/assets/86e743e2-6059-4957-9ac9-6239708014a0" />


```sql
SELECT 
    c.cust_name,
    c.city,
    o.ord_no,
    o.ord_date,
    o.purch_amt
FROM 
    customer c
LEFT JOIN 
    orders o ON c.customer_id = o.customer_id
WHERE 
    c.city = 'London';
```

**Output:**

<img width="1039" height="370" alt="image" src="https://github.com/user-attachments/assets/688a6ba6-a01e-4544-b99c-753323f36116" />


**Question 6**
---
<img width="952" height="654" alt="image" src="https://github.com/user-attachments/assets/b0e0f75e-c8f0-44b9-88fc-b1e206cf1c6c" />


```sql
SELECT 
    o.ord_no,
    o.purch_amt,
    c.cust_name,
    c.city
FROM 
    orders o
JOIN 
    customer c ON o.customer_id = c.customer_id
WHERE 
    o.purch_amt BETWEEN 500 AND 2000;
```

**Output:**

<img width="928" height="360" alt="image" src="https://github.com/user-attachments/assets/5704e36f-33f9-46ed-ac35-731cb9d6a81d" />


**Question 7**
---
<img width="1344" height="464" alt="image" src="https://github.com/user-attachments/assets/f648e70a-4192-4f07-8674-432f44549b8a" />


```sql
SELECT p.*
FROM patients AS p
INNER JOIN test_results AS t
    ON p.patient_id = t.patient_id
WHERE t.test_date BETWEEN '2024-03-01' AND '2024-03-31';
```

**Output:**

<img width="1087" height="250" alt="image" src="https://github.com/user-attachments/assets/092098a4-5971-4154-90a1-d7a2efe1a848" />


**Question 8**
---
<img width="1336" height="503" alt="image" src="https://github.com/user-attachments/assets/e4fd3908-a507-4e87-91e6-b72fcd4c3139" />


```sql
SELECT
    p.first_name AS patient_name, 
    a.* 
FROM
    patients p                      
INNER JOIN
    appointments a ON p.patient_id = a.patient_id;
```

**Output:**

<img width="1164" height="426" alt="image" src="https://github.com/user-attachments/assets/333d2365-a601-44d1-aa36-2fdbe4b05404" />


**Question 9**
---
<img width="1354" height="602" alt="image" src="https://github.com/user-attachments/assets/e0ded5d4-1057-4667-8cb8-657c9cd590c5" />


```sql
SELECT
    C.cust_name AS "Customer Name",
    C.city AS "city",
    S.name AS "Salesman",
    S.city AS "city",
    S.commission
FROM
    customer C
JOIN
    salesman S ON C.salesman_id = S.salesman_id
WHERE
    C.city <> S.city  
    AND S.commission > 0.12; 

```

**Output:**

<img width="1101" height="462" alt="image" src="https://github.com/user-attachments/assets/0967b9b1-3328-48bd-95d6-b8eaf42cc996" />


**Question 10**
---
<img width="908" height="644" alt="image" src="https://github.com/user-attachments/assets/067b4b8a-2d87-4df0-b1d6-d3872362a095" />


```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city,
    s.name AS "Salesman",
    s.commission
FROM 
    customer c
JOIN 
    salesman s ON c.salesman_id = s.salesman_id;
```

**Output:**

<img width="929" height="658" alt="image" src="https://github.com/user-attachments/assets/ed3636dd-53e5-4045-8c44-b6a0d014088e" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
