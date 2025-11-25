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



**Expected Output:**  
Greater number is: 80

#### Program:
```
DECLARE
    a NUMBER := 80;
    b NUMBER := 45;
BEGIN
    IF a > b THEN
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || a);
    ELSE
        DBMS_OUTPUT.PUT_LINE('Greater number is: ' || b);
    END IF;
END;
```
#### Output:

<img width="302" height="142" alt="image" src="https://github.com/user-attachments/assets/0a0c5478-a9c6-4f6f-a69d-c67414d60758" />

---

## 2. Write a PL/SQL program to Calculate Sum of First N Natural Numbers

### Steps:
- Declare a variable `n` and assign a value (e.g., 10).
- Initialize a `sum` variable to 0.
- Use a `WHILE` loop to iterate from 1 to `n`, adding each number to the sum.
- Display the result using `DBMS_OUTPUT.PUT_LINE`.


**Expected Output:**  
Sum of first 10 natural numbers is: 55

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

#### Output:

<img width="437" height="117" alt="image" src="https://github.com/user-attachments/assets/dcbad441-6a10-4a1b-a6f1-827d469f35b3" />


---

## 3. Write a PL/SQL program to generate Fibonacci series

### Steps:
- Declare the variable `n` to indicate how many terms to generate.
- Initialize the first two Fibonacci numbers (0 and 1).
- Use a loop to generate the next terms using the formula `c = a + b`.
- Print each term in the series.

**Expected Output:**  
n = 7  
Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8

#### Program:
```

DECLARE
    n NUMBER := 7;
    a NUMBER := 0;
    b NUMBER := 1;
    c NUMBER;
    output_series VARCHAR2(4000);
BEGIN
    DBMS_OUTPUT.PUT_LINE('N = ' || n);
    DBMS_OUTPUT.PUT_LINE('---------------------------');
    IF n <= 0 THEN
        output_series := 'No terms generated.';
    ELSIF n = 1 THEN
        output_series := TO_CHAR(a);
    ELSE 
        output_series := TO_CHAR(a) || ', ' || TO_CHAR(b);
        FOR i IN 3..n LOOP
            c := a + b;
            output_series := output_series || ', ' || TO_CHAR(c);
            a := b;
            b := c;
        END LOOP;
    END IF;
    DBMS_OUTPUT.PUT_LINE('Fibonacci sequence: ' || output_series);
END;
```

#### Output:

<img width="436" height="194" alt="image" src="https://github.com/user-attachments/assets/603dbdbf-bf1f-43c9-b44d-dce726e7d44a" />

---

## 4. Write a PL/SQL Program to display the number in Reverse Order

### Steps:
- Declare a variable `n` and assign a value (e.g., 1535).
- Use a loop to extract each digit using modulo and reverse the number.
- Display the reversed number.

**Expected Output:**  
n = 1535  
Reversed number is 5351

#### Program:
```
DECLARE
    n NUMBER := 1535;
    temp NUMBER := n;
    rev NUMBER := 0;
    digit NUMBER;
BEGIN
    WHILE temp > 0 LOOP
        digit := MOD(temp, 10);
        rev := rev * 10 + digit;
        temp := FLOOR(temp / 10);
    END LOOP;

    DBMS_OUTPUT.PUT_LINE('Reversed number is ' || rev);
END;

```

#### Output:

<img width="305" height="121" alt="image" src="https://github.com/user-attachments/assets/bbec37b7-7be3-4782-8df2-8514f6cf1c3d" />

---

## 5. Write a PL/SQL program to find the largest of three numbers

### Steps:
- Declare three numeric variables `a`, `b`, and `c`.
- Use nested `IF-ELSIF-ELSE` conditions to find the largest among the three.
- Display the largest number.

**Expected Output:**  
a = 10, b = 9, c = 15  
Largest of three number is 15

#### Program:
```
DECLARE
    a NUMBER := 10;
    b NUMBER := 9;
    c NUMBER := 15;
    largest NUMBER;
BEGIN
    IF a > b AND a > c THEN
        largest := a;
    ELSIF b > a AND b > c THEN
        largest := b;
    ELSE
        largest := c;
    END IF;

    DBMS_OUTPUT.PUT_LINE('Largest of three numbers is ' || largest);
END;
```

#### Output:

<img width="362" height="127" alt="image" src="https://github.com/user-attachments/assets/c0082bbf-81df-42b9-a717-7bea28ece2a8" />


## RESULT
Thus, the PL/SQL programs using variables, conditionals, and loops were executed successfully.



