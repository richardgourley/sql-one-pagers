# SQL Data Query Language Queries - Test Yourself
- Use the examples and notes from 'sql-dql-queries.ipnb' to check syntax knowledge and understanding first.
- Write a query example for each section below and explain to yourself what the query is going to produce and why.

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

# 4d. Like
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
- Write a query example to demonstrate how you would use an inner join to find matches between two tables.
- Write a query example to demonstrate how an inner join can be used to retrive column data from a second table that is linked to a first table but not available in the first table.

### 5b. Left Join
- Write a query example to demonstrate how a left join can display all rows from a first table, and whether or not there is a match in a second table.
- Write a query example to demonstrate how a left join and searching for null values could be used to find out where there are no matches from a first table in the second table.

### 5c. Right Join
- Write a query example to demonstrate how a right join is the opposite of a left join

### 5d. Full Outer Join
- Write a query example to demonstrate how a full join can get all results and any matches or non matches from a first and second table.

### 5e. Cross Join
- Write a query example to demonstrate how you could get all combinations of store ids and product ids. Then use that query as the left table of a further left join. 

### 5f. Self Join
- Write a query example to demonstrate how to use a self join to find all employees and their managers from the same table .

## 6. Grouping

### 6a. Group By
- Write a query example to demonstrate how you could count how many orders have been placed by customer_id and year where the customer_id is between 1 and 10.
- Write a query example to demonstrate how you could count how many customers are in each city.
- Write a query example to demonstrate how you could get the average list price of products per brand.
- Write a query example to demonstrate how you could get the total sum of orders items from an order items table for each order in an orders table.

### 6b. Having
- Write a query example to demonstrate how you could get the total sales for each salesperson where the sales total is more than 5000.
- Write a query example to demonstrate how you could get the maximum list price and minimum list price for products in each category where the maximum price is less than 10000 but the minimum price is more than 2000.
- Write a query example to demonstrate how you could get the average list price for each category where the average list price is between 500 and 3000.

### 6c. Grouping Sets
- Write a query example to demonstrate how you would get grouping sets of sales totals for brand and category, brand only, category only and an overall total.

### 6d. Cube
- Write a query example to demonstrate how to use CUBE to get all combinations of grouping sets for 3 columns.
- Write a query example to demonstrate how to use a partial CUBE to only retrieve the sales totals for brand plus category, and brand only.

### 6e. Roll Up
- Write a query example to demonstrate how use ROLLUP to get sales totals for brand plus category, brand only ad the overall sales total.
- Write a query example to demonstrate how to use a partial ROLLUP to retrieve sales totals for brand plus category and brand only.

