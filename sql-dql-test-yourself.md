# SQL Data Query Language Queries - Test Yourself
- The tests in this page are all based on the 'sql-dql-queries.ipynb' file queries.
- The tests are to make sure you can remember query syntax but it is really important to also understand the queries in depth before trying the tests. Check the query aims and notes in the 'sql-dql-queries.ipynb' file.

# 1. Query Order
- Write the order SQL performs queries in by keyword, eg. FROM, WHERE, SELECT etc.

# 2. Sorting

## 2a. Order By

1. Write a query to retrieve all first names from a table ordering the names alphabetically.

2. Write a query to retrieve first names and city from a table, ordering first by city and then by first name alphabetically.

3. Write a query to retrieve all first names from a table, ordering the first names by length, starting with the shortest name first.

# 3. Limiting

## 3a. Offset Fetch

1. Write a query to retrieve team name and points from a table, ordering by points highest to lowest. Then limit the query to skip the first 4 rows and only retrieve the next 13 rows after that.

2. Write the first part of a query (the SELECT part) to retrieve the first 10 results of a query.

3. Write the first part of a query (the SELECT part) to retrieve the top 1 percent of results.

4. Write the first part of a query (the SELECT part) to retrieve the top 3 results with ties (any results that are equal third)

# 4. Filtering

## 4a. Distinct

1. Write a query to retrieve the unique countries from a table.

## 4b. And, Or, In

1. Write a query to retrieve products that have a brand id of 1 or 2, and have a list price greater than 40.

2. Write a query to retrieve products that have a brand id of 10,11,12 or 13.

# 4c. Between, Not Between

1. Write a query to retrieve products that don't have a list price between 180 and 200.

2. Write a query to retrieve orders that have an order date between May 20th, 2021 and June 20th, 2021.

# 4d. Like

1. Write a query to retrieve first names that start with 'z'.

2. Write a query to retrieve first names that end in 'er'.

3. Write a query to retrieve first names that begin with 't' but end in 's'.

4. Write a query to retrieve first names from a table that begin with any character, followed by a 'u', then followed by any characters.

5. Write a query to retrieve first names starting with 'Z' or 'Y'.

6. Write a query to retrieve first names not starting with any characters between 'A' and 'D'.

7. Write a query to retrieve comments that include '30%', escaping the '%' symbol in the query.

# 4e. Column Aliases

1. Write a query to retrieve first name and last name, combined into one column with the alias 'Full Name'

2. Write a join query that uses two tables giving a single letter alias to each table.

# 5. Joining Tables

## 5a. Inner Join

**1. QUERY AIM:**
- This query retrieves all candidates from the CANDIDATES table whose name also appears in the EMPLOYEES table.

**2. QUERY AIM:**
- This inner join obtains data from two tables to get product details from the PRODUCTS table and category_name from the CATEGORIES table.

## 5b. Left Join

**1. QUERY AIM:**
- In this query, we want to see everyone from the CANDIDATES table, and return either NULL or if they are also in the EMPLOYEES table, return their details.

**2. QUERY AIM:**
- In this query we want a list of all product names from the PRODUCTS table (LEFT table) and then either NULL or the order_ids for this product.

## 5c. Right Join

**1. QUERY AIM:**
- This query aims to retrieve and asses ALL employees from the EMPLOYEES table (RIGHT table) and see if they appear in the CANDIDATES table (on the left).


## 5d. Full Outer Join

**1. QUERY AIM:**
- This query aims to get all candidates from the CANDIDATES table and all employees from the EMPLOYEES table and show if they are in BOTH tables or just appear in one of the tables.

## 5e. Cross Join

**1. QUERY AIM:**
- This query aims to combine all possible combinations of store from STORES and product from PRODUCTS and then use that combination further as a LEFT table in a further left JOIN.

## 5f. Self Join

**1. QUERY AIM:**
- This query aims to return all employees and their manager_id using a SELF JOIN where the table EMPLOYEES is assessed against itself.












