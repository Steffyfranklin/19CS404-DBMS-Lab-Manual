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
Write a SQL statement to increase the salary of employees under the department 40, 90 and 110 according to the company rules.
Salary will be increased by 25% for the department 40, 15% for department 90 and 10% for the department 110 and the rest of the departments will remain same.
```sql
update Employees
set salary=
    case
        when department_id=40 then round(salary*1.25 )
        when department_id=90 then round(salary*1.15 )
        when department_id=110 then round(salary*1.1 )
        else salary
    end;
```

**Output:**

<img width="1173" height="265" alt="image" src="https://github.com/user-attachments/assets/8f8857bd-ab5c-431e-9d55-75cd38374296" />

**Question 2**
---
Write a SQL statement to double the availability of the product with product_id 1.

```sql
update products
set availability=2*availability
where product_id=1;
```

**Output:**

<img width="976" height="220" alt="image" src="https://github.com/user-attachments/assets/d2426339-e40e-4f94-a491-7d2fa574b18c" />

**Question 3**
---
Write a SQL statement to Increase the selling price by 15% in the products table where quantity in stock is less than 50 and supplier ID is 10.

```sql
update Products
set sell_price=sell_price*1.15
where quantity<50 and  supplier_id=10;
```

**Output:**

<img width="1220" height="293" alt="image" src="https://github.com/user-attachments/assets/4733d570-98bb-45b4-8553-5c4100bc8d0c" />

**Question 4**
---
Write a SQL statement to Update the product_name to 'Premium Bread' whose product ID is 5 in the products table.

```sql
update Products
set product_name='Premium Bread'
where product_id=5;
```

**Output:**

<img width="1181" height="233" alt="image" src="https://github.com/user-attachments/assets/93a6655c-1adc-4055-9732-81844553bf7a" />

**Question 5**
---
Change the supplier name to upper case where contact person contains ' Singh' in suppliers table.

```sql
update suppliers
set supplier_name=upper(supplier_name) 
where contact_person like '%Singh';
```

**Output:**

<img width="1362" height="231" alt="image" src="https://github.com/user-attachments/assets/c464446d-601e-48ce-9a47-b4ff9a602bcb" />

**Question 6**
---
Write a SQL query to Delete customers with 'GRADE' 3 and whose 'CUST_NAME' contains the substring 'BBB', and 'PAYMENT_AMT' is greater than 2000

```sql
delete from customer
where grade=3 and cust_name like "%BBB%" and PAYMENT_AMT>2000;
```

**Output:**

<img width="1358" height="302" alt="image" src="https://github.com/user-attachments/assets/e4195b9c-b253-4740-8bd4-9dce7c11b08d" />

**Question 7**
---
Write a SQL query to Delete a Specific Surgery whose ID is 3

```sql
delete from Surgeries
where surgery_id=3;
```

**Output:**

<img width="655" height="233" alt="image" src="https://github.com/user-attachments/assets/a1027702-d148-4bb1-90c7-a8abe3f5b82b" />

**Question 8**
---
Write a SQL query to delete a specific doctor from Doctors table whose ID is 1.

```sql
delete from doctors
where doctor_id=1;
```

**Output:**

<img width="710" height="172" alt="image" src="https://github.com/user-attachments/assets/139b1f93-df1f-447d-9680-cd71f61927a1" />

**Question 9**
---
Write a SQL query to Delete customers whose 'GRADE' is greater than 2 and have a 'PAYMENT_AMT' less than the average 'PAYMENT_AMT' for all customers, or whose 'OUTSTANDING_AMT' is greater than 8000.

```sql
delete from customer
where grade>2 and payment_amt<(select avg(payment_amt) from customer) or outstanding_amt>8000;
```

**Output:**

<img width="1448" height="339" alt="image" src="https://github.com/user-attachments/assets/f210b08c-8741-4fb0-9612-b16c81d5b6fd" />

**Question 10**
---
Write a SQL query to Delete All Doctors with a NULL Specialization

```sql
delete from doctors
where specialization is null;
```

**Output:**

<img width="609" height="517" alt="image" src="https://github.com/user-attachments/assets/cde49bf8-0eeb-428a-bc06-133b060b1c47" />

<img width="1918" height="1146" alt="Screenshot 2025-11-18 102012" src="https://github.com/user-attachments/assets/b41292cc-b7f8-4740-9b31-4f63e4051d25" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
