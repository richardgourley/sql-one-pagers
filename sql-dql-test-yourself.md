# SQL Data Query Language Queries - Test Yourself
- Use the examples and notes from 'sql-dql-queries.ipnb' to check syntax knowledge and understanding first.
- Try to write the query examples below and explain to yourself what the result should be. Check any gaps in your knowledge.

## 1. Query Order
- Write the order of SQL queries by keyword, eg. FROM, WHERE, SELECT etc.

## 2. Sorting

### 2a. Order By
- Write a query example with ORDER BY.
- Write a query example with ORDER BY, ordering by more than one column.

## 3. Limiting

### 3a. Offset Fetch
- Write a query example that skips a number of rows at the start and then fetches a number of rows after that.

### 3b. Select Top
- Write a query example that retrieves the top 10 rows of a specified column value.
- Write a query example that retrieves the top 1% of rows based on a column value.
- Write a query example that retrieves the top 3 rows with tied results, based on a column value.

## 4. Filtering

### 4a. Distinct
- Write a query example that returns the unique values within a column.

### 4b. And, Or, In
- Write a query example that retrieves rows using the AND and OR keywords.
- Write a query example that retrieves rows based on multiple OR statements.

### 4c. Between, Not Between
- Write a query example that retrieves rows based on a numerical value between two numbers.
- Write a query example that retrieves rows based on a datetime type between two dates.

### 4d. Like
- Write a query example that retrieves names starting with 'z'.
- Write a query example that retrieves names ending in 'er'.
- Write a query example that retrieves names beginning with 't' and ending in 's'.
- Write a query example that retrieves names that start with any character, followed by 'u', followed by any characters.
- Write a query example that retrieves names starting with 'Z' or 'Y'.
- Write a query example that retrieves names that do not start with the letter range 'A-D'.
- Write a query example to demonstrate how you would escape the '%' sign and retrieve columns containing the '%' sign in the text.

### 4e. Column Aliases
- Write a query example to demonstrate how you would give a column alias containing spaces.
- Write a query example to demonstrate how inner joins can have one letter alias names.

## 5. Joining Tables

### 5a. Inner Join
- Write a query that uses an INNER JOIN to find people who appear in both the candidates and employees table. The column they have in common is 'full_name'.
- Write a query that uses an INNER JOIN to retrieve all product names and their category name. The column they have in column is 'category_id'.

### 5b. Left Join
- Write a query that uses a LEFT JOIN. The table should display all candidates from the candidates table, and show if they are also in the employees table or not. The column they have in common is 'full name'.
- Write a query that uses a LEFT JOIN. The table should display all product_name from products and order_id from order_items. The table should show all products and matching order_id or NULL for order_id if the product has not been ordered so far. The column in common between the tables is 'product_id'. 

### 5c. Right Join
- Write a query that uses a RIGHT JOIN. The table should display all employees and whether they appear in the candidates table or not. The column the tables have in common is 'full_name'.

### 5d. Full Outer Join
- Write a query that uses FULL JOIN. The table should display all candidates and all employees from both tables and whether they appear in the other table or not.

### 5e. Cross Join
- Write a query that uses CROSS JOIN. The table should display all possible combinations of store id and product id. The columns should be store_id, product_id and a sales column which uses a function to return 0 the sales column is NULL. 

### 5f. Self Join
- Write a query that uses SELF JOIN to find all employees and their managers from the same employees table.

## 6. Grouping

### 6a. Group By
- Write a query that uses GROUP BY. The table should display the customer id, the year orders were placed and how many orders were placed from an orders table.
- Write a query that uses GROUP BY. The table should tell us how us how many customers are in each city.
- Write a query that uses GROUP BY and INNER JOIN. The table should display how the average list price for each brand name. The column the products and brands table have in common is 'brand_id'.
- Write a query that uses GROUP BY. The result should tell us the net value of all sales for each order_id from the orders table. The query should include the 'quantity' and 'discount' column inside an aggregate function for the net_value field. 

### 6b. Having
- Write a query that uses GROUP BY and HAVING. The result should tell us the sales totals for each salesperson but only where the sales total is more than 2000.
- Write a query that uses GROUP BY and HAVING. The result should display the maximum and minimum list price for each category_id in the products table. We only want to return maximum list prices over 4000 and minimum list prices of less than 500.
- Write a query that uses GROUP BY and HAVING. The result should display the average list price per category_id from the products table but only where the average list price is between 500 and 1000.

### 6c. Grouping Sets
- Write a query that uses GROUP BY and GROUPING SETS. The result should display the total sales for brand and category, the total sales for each brand, the total sales for each category and the total overall sales. The columns should include brand, category and the sum of sales.

### 6d. Cube
- Write a query example that uses GROUP BY and CUBE to show the syntax for getting all combinations of grouping sets for 3 columns.
- Write a query that uses GROUP BY and CUBE to demonstrate how to use a partial CUBE to only retrieve the sales totals for brand plus category, and brand only.

### 6e. Roll Up
- Write a query that uses GROUP BY and ROLLUP to get sales totals for brand plus category, brand only and the overall sales total.
- Write a query that uses GROUP BY and a partial ROLLUP to retrieve sales totals for brand plus category and brand only.

## 7. SubQuery

### 7a. Overview
- Write a query that has a subquery in the WHERE clause, using the IN keyword. 
- Write a query that has a subquery as a column. The subquery should query from a related table. The subquery should contain the MAX keyword.

### 7b. Correlated SubQuery
- Write a correlated subquery inside a WHERE clause and after the IN keyword. The subquery should contain the MAX keyword.

### 7c. Exists
- Write a correlated subquery inside the WHERE clause, after the EXISTS keyword. The subquery should contain the COUNT and HAVING keywords.

### 7d. Any
- Write a query that has a subquery inside the WHERE clause, after the ANY keyword. 

### 7e. All
- Write a query that has a subquery inside the WHERE clause, after the ALL keyword. The subquery should contain the AVG keyword.

## 8. Set Operators

### 8a. Union
- Write a query example to demonstrate how to combine two queries with identical data types, removing all duplicate rows between the two tables.

### 8b. Union All
- Write a query example to demonstrate how to combine two queries with identical data types, keeping all duplicate rows between the two tables.

### 8c. Intersect
- Write a query example to demonstrate how to use two tables and INTERSECT to find objects or people that appear in both tables.

### 8d. Except
- Write a query example to demonstrate how to use two tables and EXCEPT to find object or people that appear in the first table but not in the second tables.

## 9. CTEs

### 9a. CTEs
- Write a query example to demonstrate how to create a CTE with column aliases in the outer table to - Write a query example to return sales totals for each salesperson for the year 2019.
- Write a query example to demonstrate how to create a CTE that retrieves the average order count per member of staff for the year 2018.
- Write a query example showing how you could use multiple CTEs as the tables used by a join.

### 9b. Recursive CTEs
- Write a query example to demonstrate how a recursive CTE could return the numbers 1-4.
- Write a query example to demonstrate how a recursive CTE could return all employees and their managers from within the same table.

## 10. Pivot

### 10a. Pivot
- Write a query example to demonstrate how you could return the total number of products per category with the category names pivoted to become columns in the result.
- Write a query example to demonstrate how you could add a year column to the query to create a row group called year to display product totals by category in the columns and by year as a row group.

## 11. Expressions

### 11a. Case
- Write a query example to demonstrate how you could use CASE to create two columns - 'Pass' and 'Fail' that count how many exam scores recieved a 'Pass' or a 'Fail'.
- Write a query example to demonstrate how you could return all students, their results and a column called outcome with 'Pass' or 'Retake' added depending if the score was over 70 or not.

### 11b. Coalesce
- Write a query example to demonstrate how you could use COALESCE to return employee names and emails, returning 'N/A' if the email is NULL.
- Write a query example to demonstrate how you could use COALESCE to calculate a monthly salary column for all employees in a table, even if the employee has an hourly or daily salary rate in a corresponding column.

### 11c. NullIf
- Write a query example to demonstrate how you could use NULLIF to return an email address as NULL if the email address is blank.






