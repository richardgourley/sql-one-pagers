# SQL Data Query Language Queries - Test Yourself
- Use the examples and notes from 'sql-dql-queries.ipnb' to check syntax knowledge and understanding first.
- Try to write the query examples below and explain to yourself what the result should be. Check any gaps in your knowledge.

## 1. Query Order
- Write the keyword order in which a SQL query is performed eg. FROM, WHERE, SELECT etc.

## 2. Sorting

### 2a. Order By
- Write a query that uses ORDER BY. The query should order by one column such as name. The results should appear in ascending order.
- Write a query that uses ORDER BY. The query should order results by two columns, city and first name. The results should be in alphabetical order.

## 3. Limiting

### 3a. Offset Fetch
- Write a query that uses OFFSET and FETCH. The query should skip the first 4 rows and retrieve the following 13 rows.

### 3b. Select Top
- Write a query that uses SELECT TOP. The query should retrieve the top 10 rows based on a column value. The query could retrieve the 10 highest list prices from the products table.
- Write a query that uses SELECT TOP. The query should retrieve the top 1% of rows based on a column value. The query could retrieve the highest list prices for products that are in the top 1%.
- Write a query that uses SELECT TOP. The query should retrieve the top 3 rows based on a column value with any ties included.  The query could return the 3 highest list prices for products including any ties.  (The result return more than 3 if multiple products have the same list price.)
 
## 4. Filtering

### 4a. Distinct
- Write a query that uses DISTINCT. The query should return all cities from the customers table without any duplicate cities.

### 4b. And, Or, In
- Write a query that uses AND and OR. The query should use brackets to avoid errors. The query should return product information for all products whose brand_id is 1 or 2 and whose list price is higher than 40.
- Write a query that uses IN. The query should return all products whose brand_id is 1,2,3 or 4.

### 4c. Between, Not Between
- Write a query that uses BETWEEN. The query should retrieve all products that have a list price that isn't between 149.99 AND 199.99.
- Write a query that uses BETWEEN. The query should retrieve all orders that have a date January 15th 2017 and January 17th 2017.

### 4d. Like
- Write a query that uses LIKE. The query should retrieve names starting with 'z'.
- Write a query that uses LIKE. The query should retrieve names ending in 'er'.
- Write a query that uses LIKE. The query should retrieve names beginning with 't' and ending in 's'.
- Write a query that uses LIKE. The query should retrieve names that start with any character, followed by 'u', followed by any characters.
- Write a query that uses LIKE. The query should retrieve names starting with 'Z' or 'Y'.
- Write a query that uses LIKE. The query should retrieve names that do not start with the letter range 'A-D'.
- Write a query that uses LIKE and ESCAPE. The query should retrieve comments that include the text '30%'.

### 4e. Column Aliases
- Write a query that uses a column alias.  The query should return all customers first names and last names joined together with an alias 'Full Name'.
- Write a query that uses a column alias. The query should be an inner join where a column alias is used for the table names and the table name alias is used in columns where required.

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
- Write a query that uses SELF JOIN. The query should find all employees and their managers from the same employees table.

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
- Write a query that has a subquery in the WHERE clause, after the IN keyword. The query should return order information and the customer id of the order, for customers whose city is New York. 
- Write a query that has uses a subquery for a column. The query should return order id, order date and the maximum list price from the order items for that order.

### 7b. Correlated SubQuery
- Write a correlated subquery inside a WHERE clause and after the IN keyword. The query should return product name, list price and category from the products table, where the product has the highest list price in its category.

### 7c. Exists
- Write a correlated subquery inside the WHERE clause, after the EXISTS keyword. The subquery should contain the COUNT and HAVING keywords. The query should return all customers who have placed more than 2 orders in the orders table.

### 7d. Any
- Write a query that has a subquery inside the WHERE clause, after the ANY keyword. The query should return any products that have a quantity of more than 2 in the order items table.

### 7e. All
- Write a query that has a subquery inside the WHERE clause, after the ALL keyword. The subquery should contain the AVG keyword. The query should return all products who have a higher list price than all of average list prices grouped by brand_id.

## 8. Set Operators

### 8a. Union
- Write a query that uses UNION. The query should retrieve the first name and last name of all staff and customers, removing any duplicates where staff are also customers.

### 8b. Union All
- Write a query that uses UNION ALL. The query should retrieve the first name and last name of all staff and customers, keeping any duplicates in the result, for example, where staff are also customers.

### 8c. Intersect
- Write a query that uses INTERSECT. The query should find players that appear in both of these invented tables - player_of_the_year_2021 and player_of_the_year_2020.

### 8d. Except
- Write a query that uses EXCEPT. The query should retrieve employees from the employees table who do not also appear in an invented health_and_safety certificate table.

## 9. CTEs

### 9a. CTEs
- Write a query that uses a CTE inlcuding WITH and GROUP BY. The query should return the sales totals per salesperson per year for the year 2019.
- Write a query that uses CTE including WITH, COUNT, GROUP BY and AVG. The query should retrieve the average order count per member of staff for the year 2018.
- Write a query example that shows the outline syntax (without specific columns) showing how you could write multiple CTEs to be used as tables within a join query.

### 9b. Recursive CTEs
- Write a query that uses a CTE including UNION ALL to return the numbers 1 to 4 recursively.
- Write a query that uses a CTE including UNION ALL. The query should recursively return all employees and their managers from within the same employees table.

## 10. Pivot

### 10a. Pivot
- Write a query that uses PIVOT. The query should retrieve the total number of products per category name. The category names should be pivoted to become column headings.
- Write a query that uses PIVOT. The query should retrieve the total number of products per category name per model year. The category names should be pivoted to become column headings, while the model year should be row headings.

## 11. Expressions

### 11a. Case
- Write a query that uses CASE. The query should return students names, their test scores and an outcome column saying 'Pass' or 'Fail', depending if the test score was over 70 or not, from an invented test_scores table.
- Write a query that uses CASE. The query should return students names, their test scores and an outcome column saying 'Pass', 'Fail' or 'Possible retake', depending if the test score was over 70, between 60 and 70, or less than 60, from an invented test_scores table.

### 11b. Coalesce
- Write a query that uses COALESCE. The query should retrieve the first name, last name and email of all employees. If the email address is NULL, then a string saying 'N/A' should be returned instead. 
- Write a query that uses COALESCE. The query should return a monthly_salary column for each employee.  Employees have one of hourly_rate, weekly_rate or monthly_rate already in the salaries table. 
The query should calcaulte a monthly rate if the employees salary is saved as hourly or weekly.

### 11c. NullIf
- Write a query that uses NULLIF. The query should return name and email columns from the clients table. If the email is an empty string, then NULL should be returned instead.






