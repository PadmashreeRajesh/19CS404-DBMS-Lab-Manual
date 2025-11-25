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
---
<img width="1221" height="628" alt="image" src="https://github.com/user-attachments/assets/d044c2ca-ba4f-4850-8120-e955b2e8ec06" />


```sql
UPDATE employees
SET salary = salary * 2
WHERE department_id = 20
  AND job_id LIKE '%MAN';
```

**Output:**

<img width="1246" height="429" alt="image" src="https://github.com/user-attachments/assets/6f4e8358-a935-407c-932b-fbe72af26545" />


**Question 2**
---
<img width="934" height="313" alt="image" src="https://github.com/user-attachments/assets/c7182c6a-78ab-450c-9197-2316dd73b1f9" />


```sql
UPDATE Products
SET quantity=quantity*1.10;
```

**Output:**

<img width="1302" height="473" alt="image" src="https://github.com/user-attachments/assets/9c2850fb-8e94-41eb-9d2b-2f82cd570f11" />


**Question 3**
---
<img width="1136" height="397" alt="image" src="https://github.com/user-attachments/assets/36b1ce21-4c67-4663-9ca7-3858b9c5d97b" />


```sql
UPDATE products
SET reorder_lvl = CAST(reorder_lvl * 1.30 AS INT)
WHERE category = 'Food'
  AND quantity < (reorder_lvl * 0.5);
```

**Output:**

<img width="1320" height="330" alt="image" src="https://github.com/user-attachments/assets/a90d18ff-850f-408d-8792-4ce8d2074638" />


**Question 4**
---
<img width="1051" height="474" alt="image" src="https://github.com/user-attachments/assets/78869c1d-a58e-445f-88a4-f73ba4617952" />


```sql
UPDATE products
SET reorder_lvl = CAST(reorder_lvl * 0.70 AS INT)
WHERE LOWER(product_name) LIKE '%cream%'
  AND quantity > reorder_lvl;
```

**Output:**

<img width="1316" height="387" alt="image" src="https://github.com/user-attachments/assets/86b55c23-70ea-4ab7-97f3-cb57bed2d1ad" />


**Question 5**
---
<img width="674" height="372" alt="image" src="https://github.com/user-attachments/assets/a85d0e27-af09-4410-84de-995ce7c683a3" />


```sql
UPDATE Products
SET reorder_lvl=40
WHERE category='Grocery';
```

**Output:**

<img width="1340" height="220" alt="image" src="https://github.com/user-attachments/assets/a45856fe-6e99-47df-be15-662fe94d8c59" />


**Question 6**
---
<img width="1198" height="175" alt="image" src="https://github.com/user-attachments/assets/208ee09a-5fe0-4260-a444-6918b09bdeb8" />


```sql
DELETE FROM doctors
WHERE specialization='Pediatrics'
AND first_name='Michael';
```

**Output:**

<img width="1215" height="450" alt="image" src="https://github.com/user-attachments/assets/99b2efea-2477-4275-955a-0ec0091c19f2" />


**Question 7**
---
<img width="907" height="147" alt="image" src="https://github.com/user-attachments/assets/9549821f-03db-4715-a01b-20cebc85c0da" />


```sql
DELETE FROM doctors
WHERE specialization='Cardiology';
```

**Output:**

<img width="1213" height="452" alt="image" src="https://github.com/user-attachments/assets/904b8c9c-9ebd-49d9-99a2-f6763fa33029" />


**Question 8**
---
<img width="1191" height="620" alt="image" src="https://github.com/user-attachments/assets/65cdeb70-2592-48cf-874d-cd540476f644" />


```sql
SELECT 
    id,
    value2,
    CASE
        WHEN value2 < 10 THEN 'Small'
        WHEN value2 BETWEEN 10 AND 50 THEN 'Medium'
        WHEN value2 > 50 THEN 'Large'
    END AS size_category
FROM Calculations;
```

**Output:**

<img width="875" height="560" alt="image" src="https://github.com/user-attachments/assets/de1e60c9-bdf9-49ec-ac61-24cff28042b4" />

**Question 9**
---
<img width="1197" height="481" alt="image" src="https://github.com/user-attachments/assets/6b66e163-2730-44ed-9acc-1772dafce368" />


```sql
SELECT 
    customer_id,
    cust_name,
    city,
    grade,
    salesman_id
FROM customer
WHERE city = 'New York'
   OR NOT (grade > 100);
```

**Output:**

<img width="1207" height="493" alt="image" src="https://github.com/user-attachments/assets/2b20bc97-2345-46dd-8d1d-08e10b9f63da" />


**Question 10**
---
<img width="1140" height="610" alt="image" src="https://github.com/user-attachments/assets/7454a651-f993-4877-8a56-175efa40cd2b" />


```sql
SELECT 
    EmployeeID,
    FirstName,
    BirthDate,
    CAST((julianday('2023-12-30') - julianday(BirthDate)) / 365.25 AS INT) AS age
FROM employees
WHERE CAST((julianday('2023-12-30') - julianday(BirthDate)) / 365.25 AS INT) > 50;
```

**Output:**

<img width="1076" height="653" alt="image" src="https://github.com/user-attachments/assets/31a15da9-2aac-4b62-8e1d-86fafbe4ed57" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
