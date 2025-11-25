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
<img width="1068" height="557" alt="image" src="https://github.com/user-attachments/assets/7028e64c-5c04-493b-a8fd-be5f07415170" />


```sql
SELECT PatientID,COUNT(*) AS TotalRecords
FROM MedicalRecords 
GROUP BY PatientID;
```

**Output:**

<img width="682" height="728" alt="image" src="https://github.com/user-attachments/assets/f0c16e99-7ef1-4942-8927-6ad9183ba88e" />


**Question 2**
---
<img width="1024" height="486" alt="image" src="https://github.com/user-attachments/assets/2ca5fd9f-39d9-400d-b802-05536193c393" />


```sql
SELECT Gender,COUNT(PatientID) AS TotalPatients FROM Patients
GROUP BY Gender;
```

**Output:**

<img width="714" height="442" alt="image" src="https://github.com/user-attachments/assets/1619d2f7-48b5-4d2f-ba3a-3763880a316e" />


**Question 3**
---
<img width="1052" height="493" alt="image" src="https://github.com/user-attachments/assets/96dc371b-1f48-4d0c-a798-a61eb2602d71" />


```sql
SELECT strftime('%Y-%m',Date)Month,COUNT(*) as TotalRecords from MedicalRecords 
Group by strftime('%Y-%m',date)
order by Month;
```

**Output:**

<img width="651" height="513" alt="image" src="https://github.com/user-attachments/assets/ec6df9f5-fef4-4b81-9587-f60f9266d782" />


**Question 4**
---
<img width="674" height="525" alt="image" src="https://github.com/user-attachments/assets/d8b488d6-63f5-4b94-a688-877cfc6862ed" />



```sql
select count(*) as employees_in_california from employee
where city='California';
```

**Output:**

<img width="688" height="386" alt="image" src="https://github.com/user-attachments/assets/983f9d9d-7f93-4c54-b63b-29b279ec279f" />



**Question 5**
---
<img width="865" height="470" alt="image" src="https://github.com/user-attachments/assets/fa5b9884-d2d4-48c4-be11-0af58048a81a" />


```sql
select avg(income) as avg_income from employee
where name like 'A%';
```

**Output:**

<img width="525" height="384" alt="image" src="https://github.com/user-attachments/assets/11cce95d-676f-4dcd-a0fe-2e2597758ab6" />


**Question 6**
---
<img width="1071" height="479" alt="image" src="https://github.com/user-attachments/assets/7b778a12-9502-46f3-b675-71c732b261fb" />


```sql
select sum(workhour) as 'Total working hours' from employee1;
```

**Output:**

<img width="579" height="392" alt="image" src="https://github.com/user-attachments/assets/594ca6c5-e6ed-4bba-9705-b96b000edaf9" />


**Question 7**
---
<img width="1051" height="474" alt="image" src="https://github.com/user-attachments/assets/388f1166-f76a-4fcc-ad56-f2d1374bfb7b" />


```sql
select count(distinct age) as COUNT from employee;
```

**Output:**

<img width="391" height="389" alt="image" src="https://github.com/user-attachments/assets/c0a659f5-d5f6-435c-aa70-a2c2229a161c" />


**Question 8**
---
<img width="1200" height="578" alt="image" src="https://github.com/user-attachments/assets/f14f60c6-a7b9-4347-bc4f-ac563f23370e" />


```sql
select city,sum(income) as Income from employee
group by city
having sum(income)>200000;
```

**Output:**

<img width="691" height="603" alt="image" src="https://github.com/user-attachments/assets/42484d97-b561-489b-9078-a2ff448d3d41" />


**Question 9**
---
<img width="1205" height="497" alt="image" src="https://github.com/user-attachments/assets/fffba3a0-03e4-4ac6-bb36-52432b87e12d" />


```sql
select age,SUM(income) from employee
group by age
having sum(income)>1000000;
```

**Output:**

<img width="652" height="495" alt="image" src="https://github.com/user-attachments/assets/5e8aaf74-b2e3-4bf7-aa13-4262e0dd17fe" />


**Question 10**
---
<img width="1207" height="507" alt="image" src="https://github.com/user-attachments/assets/2fb778f0-e5fd-42fd-9b9a-e299230792d1" />


```sql
select age,MIN(income) from employee
group by age
having min(income)<400000;
```

**Output:**

<img width="643" height="472" alt="image" src="https://github.com/user-attachments/assets/4b7485b9-8c5b-482e-aa61-ebc068ce4e43" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.

