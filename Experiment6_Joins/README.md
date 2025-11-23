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
From the following tables write a SQL query to find salespeople who received commissions of more than 12 percent from the company. Return Customer Name, customer city, Salesman, commission.  

```sql
select c.cust_name as 'Customer Name', c.city , s.name as Salesman,s.commission
from customer as c
join salesman as s
on c.salesman_id=s.salesman_id
where s.commission > 0.12
```

**Output:**

<img width="1231" height="773" alt="image" src="https://github.com/user-attachments/assets/6cdc693e-b03c-455f-8a6b-32227bb331d0" />

**Question 2**
---
Write an SQL query to select all columns from the 'customer' table (aliased as 'c') by performing a LEFT JOIN with the 'orders' table on the 'customer_id' column, including only those orders where the order date falls between '2012-08-01' and '2012-08-30'.

'customer' Table: (customer_id, cust_name, city, grade, salesman_id)

'orders' Table: (ord_no, purch_amt, ord_date, customer_id, salesman_id)

```sql
select c.customer_id,c.cust_name,c.city,c.grade,c.salesman_id
from customer as c
join orders as o
on c.salesman_id=o.salesman_id
where o.ord_date between "2012-08-01" and '2012-08-30'
```

**Output:**

<img width="1225" height="467" alt="Screenshot 2025-11-23 164055" src="https://github.com/user-attachments/assets/7debb4c7-88eb-4758-b2c6-b1ed238d6887" />

**Question 3**
---
From the following tables write a SQL query to find the details of an order. Return ord_no, ord_date, purch_amt, Customer Name, grade, Salesman, commission. 

```sql
select o.ord_no,o.ord_date,o.purch_amt,c.cust_name as "Customer Name",c.grade,s.name as Salesman,s.commission
from orders as o
join customer as c
on o.customer_id=c.customer_id
join salesman as s
on o.salesman_id=s.salesman_id
```

**Output:**

<img width="1273" height="966" alt="image" src="https://github.com/user-attachments/assets/6188a855-946d-42ba-9bcb-ab533b71389f" />

**Question 4**
---
Write the SQL query that achieves the selection of the first name from the "patients" table (aliased as "patient_name") and the specialization from the "doctors" table (aliased as "Doctor_specialization"), with an inner join on the "doctor_id" column and a condition filtering for patients admitted between '2024-01-01' and '2024-01-31'.

```sql
SELECT 
    p.first_name AS patient_name,
    d.specialization AS Doctor_specialization
FROM 
    patients p
INNER JOIN 
    doctors d
ON 
    p.doctor_id = d.doctor_id
WHERE 
    p.admission_date BETWEEN '2024-01-01' AND '2024-01-31';

```

**Output:**

<img width="593" height="293" alt="image" src="https://github.com/user-attachments/assets/50b5153b-1972-4d7c-83fa-6cc389bf0f95" />

**Question 5**
---
 From the following tables write a SQL query to find the salesperson(s) and the customer(s) he represents. Return Customer Name, city, Salesman, commission.


```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.commission AS "commission"
FROM 
    customer c
INNER JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id;

```

**Output:**

<img width="1054" height="716" alt="image" src="https://github.com/user-attachments/assets/13769ab2-9a1d-4baf-a6e6-6d98847b0dc2" />

**Question 6**
---
Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), with a left join on the "salesman_id" column and a condition filtering for customers in the city 'London'.

```sql
select s.name 
from salesman as s
join Customer as c
on s.salesman_id=c.salesman_id
where c.city='London'
```

**Output:**

<img width="330" height="362" alt="image" src="https://github.com/user-attachments/assets/2cf854ad-11bf-453b-96bb-01ab59fc7632" />

**Question 7**
---
Write the SQL query that achieves the selection of all columns from the "patients" table (aliased as "p"), with an inner join on the "patient_id" column and a condition filtering for test results with a test date between '2024-03-01' and '2024-03-31'.

```sql
select 
p.patient_id,
p.first_name,
p.last_name,
p.date_of_birth,
p.admission_date,
p.discharge_date,
p.doctor_id
from patients as p
join test_results as t
on p.patient_id=t.patient_id
where test_date between '2024-03-01' and '2024-03-31'
```

**Output:**

<img width="1277" height="310" alt="image" src="https://github.com/user-attachments/assets/b4ad5152-9055-4e07-8d4e-a5d36b05c0c4" />

**Question 8**
---
From the following tables write a SQL query to find those customers with a grade less than 300. Return cust_name, customer city, grade, Salesman, salesmancity. The result should be ordered by ascending customer_id. 

```sql
SELECT 
    c.cust_name,
    c.city ,
    c.grade,
    s.name AS "Salesman",
    s.city 
FROM 
    customer c
INNER JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id
WHERE 
    c.grade < 300
ORDER BY 
    c.customer_id ASC;

```

**Output:**

<img width="1231" height="590" alt="image" src="https://github.com/user-attachments/assets/731de528-7eb9-4971-bf15-dbbdeab0b07e" />

**Question 9**
---
From the following tables write a SQL query to locate those salespeople who do not live in the same city where their customers live and have received a commission of more than 12% from the company. Return Customer Name, customer city, Salesman, salesman city, commission. 

```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.city AS "city",
    s.commission AS "commission"
FROM 
    customer c
INNER JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id
WHERE 
    c.city <> s.city
    and s.commission > 0.12;

```

**Output:**

<img width="1225" height="464" alt="image" src="https://github.com/user-attachments/assets/7a21f997-0da7-4ce0-a95f-52f9eef53bd7" />

**Question 10**
---
Write the SQL query that achieves the selection of all columns from the "patients" table, with an inner join on the "doctor_id" column, and includes a condition filtering for patients whose doctors have the first name 'John' and last name 'Smith'.

```sql
SELECT 
    p.*
FROM 
    patients p
INNER JOIN 
    doctors d
ON 
    p.doctor_id = d.doctor_id
WHERE 
    d.first_name = 'John'
    AND d.last_name = 'Smith';

```

**Output:**

<img width="1297" height="311" alt="image" src="https://github.com/user-attachments/assets/9c4db42a-6e92-4b43-8d11-244b68a01785" />

<img width="1920" height="1200" alt="Screenshot 2025-11-22 153041" src="https://github.com/user-attachments/assets/45f254de-f4f1-4d7d-b716-eeec528f0ea6" />


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
