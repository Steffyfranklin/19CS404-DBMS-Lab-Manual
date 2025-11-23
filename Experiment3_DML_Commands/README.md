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
Write a SQL statement to Update the hire_date of employees in department 50 to 2024-01-24.

```sql
update Employees
set hire_date = '2024-01-24'
where department_id=50;
```

**Output:**

<img width="1174" height="222" alt="image" src="https://github.com/user-attachments/assets/06d1888a-c851-4f23-a84a-37713670ef81" />

**Question 2**
---
Write a SQL query to Delete customers from 'customer' table where 'AGENT_CODE' is either 'A003' or 'A008'.

```sql
delete from customer
where agent_code='A003' or agent_code='A008';
```

**Output:**

<img width="642" height="952" alt="image" src="https://github.com/user-attachments/assets/058681b8-6f07-4691-96a9-5dd35eadca69" />

**Question 3**
---
Write a SQL query to delete a doctor from Doctors table whos specialization is 'Cardiology'

```sql
delete from Doctors 
where specialization='Cardiology';
```

**Output:**

<img width="1138" height="312" alt="image" src="https://github.com/user-attachments/assets/972880ed-9ad6-4216-92d8-ec2da39f3fcb" />

**Question 4**
---
Write a SQL query to categorize value1 in the Calculations table as 'High' if it is greater than 50, otherwise 'Low'.

```sql
select id ,value1,
  case 
    when value1>50 then 'High'
    else 'Low'
  end as value_category
from Calculations;
```

**Output:**

<img width="748" height="256" alt="image" src="https://github.com/user-attachments/assets/44075ba2-d24a-4bef-80e3-a8904c279c85" />

**Question 5**
---
write a SQL query to find details of all orders with a purchase amount less than 200 or exclude orders with an order date greater than or equal to '2012-02-10' and a customer ID less than 3009. Return ord_no, purch_amt, ord_date, customer_id and salesman_id.

```sql
select * from orders
where purch_amt<200 or not (ord_date >='2012-02-10' and customer_id<3009);
```

**Output:**

<img width="1107" height="389" alt="image" src="https://github.com/user-attachments/assets/0fe3bbbc-e4a3-4a3e-8374-045305716307" />

**Question 6**
---
Write a SQL query to find all orders that meet the following conditions. Exclude combinations of order date equal to '2012-08-17' or customer ID greater than 3005 and purchase amount less than 1000.

```sql
select * from orders
where not(ord_date='2012-08-17' or customer_id > 3005 and purch_amt <1000);
```

**Output:**

<img width="1118" height="696" alt="image" src="https://github.com/user-attachments/assets/38356cd7-7e33-49b4-88e7-9735c640d1c3" />

**Question 7**
---
Create a report that shows the capitalized FirstName and capitalized LastName renamed as FirstName and Lastname respectively and EmployeeId from the employees table sorted by EmployeeId in descending order.

```sql
select UPPER(FirstName) as FirstName,UPPER(LastName) as LastName,EmployeeID from employees
order by EmployeeID desc
```

**Output:**

<img width="769" height="557" alt="image" src="https://github.com/user-attachments/assets/dd90afc4-c236-48e5-908c-5064ea444772" />

**Question 8**
---
Write a SQL query to identify products where the discount amount is greater than $50. Return product_id, original_price, discount_percentage, and discount_amount.

```sql
select * ,(original_price*discount_percentage) as discount_amount from products
where discount_amount > 50;
```

**Output:**

<img width="1169" height="201" alt="image" src="https://github.com/user-attachments/assets/ec36499f-ddba-4f99-97b4-4eec4847c029" />

**Question 9**
---
Write a SQL query to find all employees who were hired on a weekend (Saturday or Sunday) from the emp table

```sql
select ename,hiredate,
strftime("%w",hiredate) as day_of_week from emp
where strftime("%w",hiredate) in("0","6")
```

**Output:**

<img width="799" height="254" alt="image" src="https://github.com/user-attachments/assets/04ff46df-7529-4c24-882a-50b02f12de46" />

**Question 10**
---
Write a SQL query to display hire dates in the format "DD-MM-YYYY" from the emp table

```sql
select ename,strftime('%d-%m-%Y',hiredate) as HireDateFormatted from emp;
```

**Output:**

<img width="666" height="348" alt="image" src="https://github.com/user-attachments/assets/3429efed-a429-4c29-a415-ec3586daf81c" />

<img width="1919" height="1198" alt="Screenshot 2025-11-22 153002" src="https://github.com/user-attachments/assets/f592c2a0-a53a-4893-a299-c020ad7687ed" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
