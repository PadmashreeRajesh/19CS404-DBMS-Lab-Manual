# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
<img width="1048" height="557" alt="image" src="https://github.com/user-attachments/assets/f6d3d6a7-3d9e-4528-bbff-16c04510690d" />


```sql
select id,name,city,email,phone
from customer
where city<>(
    select city
    from customer
    where id=(select max(id) from customer)
);
```

**Output:**



**Question 2**
---
<img width="911" height="602" alt="image" src="https://github.com/user-attachments/assets/99473790-b84e-4aec-a7c1-1d28b54cada9" />


```sql
select * from CUSTOMERS
where SALARY>4500;
```

**Output:**

<img width="1103" height="452" alt="image" src="https://github.com/user-attachments/assets/3b40e313-55e4-4f88-b75f-e461a4c33f1d" />


**Question 3**
---
<img width="961" height="556" alt="image" src="https://github.com/user-attachments/assets/2d1507c4-e76c-48fe-9764-61300090ecf7" />


```sql
SELECT *
FROM CUSTOMERS
WHERE ADDRESS = 'Delhi'
  AND AGE < 30
ORDER BY ID
LIMIT 3;
```

**Output:**

<img width="1108" height="386" alt="image" src="https://github.com/user-attachments/assets/015302a6-e032-42c7-89e4-48a967c9bcab" />


**Question 4**
---
<img width="1005" height="594" alt="image" src="https://github.com/user-attachments/assets/3310615f-3dbc-4cd1-8c24-5f7a6d62e248" />


```sql
select id,name,age,city,income
from Employee
where age < (
select avg(age)
from Employee
where income > 250000
);
```

**Output:**

<img width="1296" height="516" alt="image" src="https://github.com/user-attachments/assets/16a8cd61-aa29-4b6e-88ca-066792b8eb35" />


**Question 5**
---
<img width="1275" height="655" alt="image" src="https://github.com/user-attachments/assets/c16f46f9-67b1-4568-b257-2a68869bcde3" />


```sql
select ord_no, purch_amt, ord_date, customer_id,o.salesman_id
from orders o
join salesman s
on o.salesman_id=s.salesman_id
where s.city='London';
```

**Output:**

<img width="1136" height="429" alt="image" src="https://github.com/user-attachments/assets/feddb1eb-93e3-4956-a95f-2b6a95ed8017" />


**Question 6**
---
<img width="1024" height="416" alt="image" src="https://github.com/user-attachments/assets/05573f2a-e0b3-43e6-850e-5ec92f496de1" />


```sql
select department_id,department_name
from Departments
where LENGTH(department_name)>(
      select avg(LENGTH(department_name)) 
      from Departments
);
```

**Output:**

<img width="561" height="423" alt="image" src="https://github.com/user-attachments/assets/e316ceba-e71f-4e0c-89a5-4458145b7c76" />


**Question 7**
---
<img width="994" height="489" alt="image" src="https://github.com/user-attachments/assets/2f9a3b37-c6dc-4c12-b6f1-e475b723b52a" />


```sql
select name,city
from customer
where city in(
    select city
    from customer
    where id in(3,7)
);
```

**Output:**

<img width="546" height="479" alt="image" src="https://github.com/user-attachments/assets/59f90168-5272-4bf8-861a-88834511b50c" />


**Question 8**
---
<img width="1235" height="558" alt="image" src="https://github.com/user-attachments/assets/ee073b4c-7b25-4e03-96d4-87f7cdc761e2" />


```sql
select student_name,grade
from GRADES g
where grade=(
     select max(grade)
     from GRADES
     where subject=g.subject
);
```

**Output:**

<img width="701" height="468" alt="image" src="https://github.com/user-attachments/assets/e67fa2c2-435e-4aa5-9b1c-6321041bbb39" />


**Question 9**
---
<img width="1288" height="642" alt="image" src="https://github.com/user-attachments/assets/424aeb8d-2eae-4671-b0bb-27a8e08b3c45" />


```sql
select ord_no, purch_amt, ord_date, customer_id,salesman_id
from orders
where salesman_id=(
     select salesman_id
     from salesman
     where name='Paul Adam'
);
```

**Output:**

<img width="1143" height="408" alt="image" src="https://github.com/user-attachments/assets/3a65e021-3bf5-4009-a019-7afc66e867c5" />


**Question 10**
---
<img width="894" height="551" alt="image" src="https://github.com/user-attachments/assets/ef4c9970-10a8-4ece-926e-b0e7af84fd2a" />


```sql
select * from CUSTOMERS 
where SALARY=1500;
```

**Output:**

<img width="1107" height="366" alt="image" src="https://github.com/user-attachments/assets/af630339-ca3b-47f9-aad8-61c157027b67" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
