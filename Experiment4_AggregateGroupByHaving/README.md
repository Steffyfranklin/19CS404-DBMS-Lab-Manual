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
How many patients are there in each city?

```sql
select Address , count(*) as TotalPatients
from Patients
group by Address
```

**Output:**

<img width="609" height="376" alt="image" src="https://github.com/user-attachments/assets/dcd3dfd2-ca06-47fc-bcb6-5b16ac5dfb8f" />

**Question 2**
---
How many medical records are there for each patient?

```sql
select PatientID , count(*) as TotalRecords
from MedicalRecords
group by PatientID
```

**Output:**

<img width="589" height="634" alt="image" src="https://github.com/user-attachments/assets/509588e7-10b3-4c63-ba8c-0f08d3f887b3" />

**Question 3**
---
How many doctors specialize in each medical specialty?

```sql
select Specialty,count(*) as TotalDocto
from Doctors
group by Specialty
```

**Output:**

<img width="653" height="641" alt="image" src="https://github.com/user-attachments/assets/1a26be51-dfd4-4c95-8d74-9b4bc2e4f7f5" />

**Question 4**
---
Write a SQL query to find the shortest email address in the customer table?

```sql
select name,email,MIN(length(email)) as min_email_length
from customer
```

**Output:**

<img width="990" height="296" alt="image" src="https://github.com/user-attachments/assets/9fe04746-0e79-4abe-9602-e3f9aefc780e" />

**Question 5**
---
Write a SQL query to find the average length of email addresses (in characters):

```sql
select AVG(length(email)) as avg_email_length
from customer
```

**Output:**

<img width="438" height="276" alt="image" src="https://github.com/user-attachments/assets/96317dc3-7bc6-4612-9308-d6b969f124ac" />

**Question 6**
---
Write a SQL query to find the Fruit with the lowest available quantity.

Note: Inventory attribute contains amount of fruits

```sql
select name as fruit_name,MIN(inventory) as lowest_quantity
from fruits
```

**Output:**

<img width="638" height="291" alt="image" src="https://github.com/user-attachments/assets/62d6370a-0121-44cf-bfa1-258f140a8f3f" />

**Question 7**
---
Write a SQL query to calculate the average purchase amount of all orders. Return average purchase amount.

```sql
select AVG(purch_amt) as AVERAGE
from orders

```

**Output:**

<img width="331" height="286" alt="image" src="https://github.com/user-attachments/assets/d926f54e-6179-4c07-9477-29cbfb6bfc30" />

**Question 8**
---
Write the SQL query that accomplishes the selection of total cost of all products in each category from the "products" table and includes only those products where the total cost is greater than 50.

```sql
select category_id,SUM(price) as Total_Cost
from products
group by Category_id
having SUM(price)>50
```

**Output:**

<img width="536" height="317" alt="image" src="https://github.com/user-attachments/assets/13960c9d-cbbd-4ff2-9941-f00d2d11c8ef" />

**Question 9**
---
Write the SQL query that achieves the grouping of data by occupation, calculates the average work hours for each occupation, and includes only those occupations where the average work hour falls between 10 and 12.

```sql
select occupation,AVG(workhour) 
from employee1
group by occupation
having AVG(workhour) between 10 and 12
```

**Output:**

<img width="580" height="350" alt="image" src="https://github.com/user-attachments/assets/3e4465f6-a09b-4626-a42d-f8360681980f" />

**Question 10**
---
Write a SQL query to identify the cities (addresses) where the average salary is greater than Rs. 5000, as per the "customer1" table.

```sql
select address,AVG(salary)
from customer1
group by address
having AVG(salary) > 5000
```

**Output:**

<img width="531" height="398" alt="image" src="https://github.com/user-attachments/assets/879c5d0a-0604-4ec6-aba8-f924cdd63ec1" />

<img width="1920" height="1200" alt="Screenshot 2025-11-22 153017" src="https://github.com/user-attachments/assets/31d468fc-b06e-42f7-9017-a069cce17473" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
