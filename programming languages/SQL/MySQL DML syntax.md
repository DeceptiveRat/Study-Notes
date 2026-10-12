*To create a SQL query, you first need to open a database in your computer*

# (1) SELECT
### • SELECT * FROM products(1)
Will select all the data from the products table

### • SELECT cup FROM products^(1)^
Select cup from the products table

### • SELECT * FROM products LIMIT 5^(1)^
Return only the first 5 results from the products table

### • SELECT column1, column2, column3 FROM table_name^(1)^

## - WHERE
### • WHERE price < 25^(1)^
Filter results to only include products under 25$

## - ORDER BY
### • ORDER BY price DESC^(1)^
Sort the results by descending price

## - JOIN
### • INNER JOIN^(1)^
Returns only the matching rows from 2 tables
example:

```sql
SELECT *
FROM table1
INNER JOIN table2 ON table1.col1 = table2.col1;
```


### • LEFT JOIN^(1)^
Returns all the rows from the left table and the matching rows from the right table
If there are no matches, the result will contain NULL values in the right table columns
example:

```sql
SELECT *
FROM table1
LEFT JOIN table2 ON table1.col1 = table2.col1;
```


### • RIGHT JOIN^(1)^
Returns all the rows from the right table and the matching rows from the left table
If there are no matches, the result will contain NULL values in the left table columns
example:



```sql
SELECT *
FROM table1
RIGHT JOIN table2 ON table1.col1 = table2.col1;
```
### • FULL OUTER JOIN^(1)^
example:

```sql
SELECT *
FROM table_1
FULL OUTER JOIN table_2
ON table_1.id = table_2.id;
```

In this example, FULL OUTER JOIN is used to combine the data from two tables ‘table_1’ and ‘table_2’ where the ‘id’ column matches in both tables

example:

```sql
SELECT A.emplyee_id, A.employee_name,
A.department_name, B.manager_id
FROM employees A
FULL OUTER JOIN departments B
ON A.department_id = B.department_id
ORDER BY employee_id;
```

In this example, FULL OUTER JOIN is used to combine data from the ‘employees’ and ‘departments’ table, where the 'department_id' matches both tables
The SELECT statement returns the ‘employee_id', ‘employee_name’, ‘department_name’ and the ‘manager_id’

## - Aliases
### • AS^(1)^
example:

```sql
SELECT product_name AS name, product_price AS price
FROM products AS p
WHERE p.product_price < 50;
```

Selects the ‘product_name’ and ‘product_price’ columns from the ‘products’ table and creates aliases ‘name’ and ‘price’

## - Functions
### • SUM()^(1)^
Calculates the sum of all the values in the specified column
example:

```sql
SELECT SUM(column_name) AS sum_of_numbers
FROM table_name;
```

‘column_name' is the name of the column that contains the numbers you want to sum up, and ‘table_name’ is the name of the table that holds the data

## - String operations
- 

# (2) INSERT
### • INSERT syntax:^(2)^
Single row:

```sql
insert into table_name([column list])
values(value list);
```

Multiple row:

eg.




```sql
insert into table_name([column list])
Subquery;
```

```sql
insert into student
values('10101', 'John', 15);
```

```sql
insert into takes
(
	select ID, 'CS-347', '2', 'Fall', 2017, NULL
	from student
	where dept_name='Comp. Sci.'
);
```
### • No need to specify the columns if the value list is in the same order^(2)^

# (3) UPDATE
### • UPDATE syntax:^(2)^



```sql
update table_name
set column=value
where condition
```
### • where can be omitted^(2)^

# (4) Delete
### • DELETE syntax:^(2)^



```sql
delete from table_name
where condition
```
### • where can be omitted^(2)^

# (5) ETC
## - Procedure
### • CREATE PROCEDURE^(1)^
usage:

```sql
CREATE PROCEDURE [dname] ([params])
```

[dname] is the name of the store procedure
[params] is the parameter list. It looks like: [name] AS [type], [value]

example:

```sql
CREATE PROCEDURE customer_name AS [name] AS VARCHAR(50),
[last_name] AS VARCHAR(50)
```

Stored procedure that gets the customer's first name and last name

### • Calling procedures^(1)^
usage:
SELECT [name] AS [type], [value]

example:
SELECT customer_name.name AS [type], customer_name.value

## - DESCRIBE^(1)^
Can be used to view the data in the table
usage:
DESCRIBE table_name

## - SHOW CREATE TABLE
- shows the SQL statement necessary to recreate a table in its current form^(3)^
- columns and their types, constraint info, etc^(3)^
- usage:^(3)^

```sql
show create table table_name;
```


---
reference:
(1) <https://medium.com/javarevisited/sql-queries-everything-you-need-to-know-to-get-started-948780fa2d87>
(2) School Database class
(3) <https://stackoverflow.com/questions/4004205/show-constraints-on-tables-command>