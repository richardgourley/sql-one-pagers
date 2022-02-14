# SQL Data Query Language Queries - Test Yourself
- 

# 1. Query Order
- Write the order of SQL queries by keyword, eg. FROM, WHERE, SELECT etc.

# 2. Sorting

## 2a. Order By

**QUERY AIM:**
- In this query, we retrieve all first_name from CUSTOMERS, ordered by first_name.

**QUERY AIM:**
- In this query, we retrieve all first_name from CUSTOMERS, ordered first by city, then wby first_name alphabetically.

**QUERY AIM:**
- This query returns all customers from the CUSTOMERS table in order of the length of their first_name.

# 3. Limiting

## 3a. Offset Fetch

**QUERY AIM:**
- In this query, from a 20 team league, we want to retrieve teams that are not in the top 4 (OFFSET) and teams that are not in the bottom 3 (FETCH FIRST 13 ROWS) after we offset the first 4 rows.

## 3b. Select Top

**QUERY AIMS:**
- The queries below would retrieve the TOP 10, the TOP 1% and the TOP 3 WITH TIES.
- (Just write the SELECT part of the 3 queries)

# 4. Filtering

## 4a. Distinct

**QUERY AIM:**
- This query tells us which countries we have customers in from the CUSTOMERS table.
- DISTINCT removes any duplicates.

## 4b. And, Or, In

**QUERY AIM:**
- This query uses OR and AND keywords to retrieve details from the PRODUCTS table where the brand_id is 1 or 2, and the list_price is higher than 40.

**QUERY AIM:**
- This query uses the IN operator to find products with a brand_id that is either 1,2,3 or 4.

# 4c. Between, Not Between

**QUERY AIM:**
- This query uses NOT BETWEEN to find products whose list_price does not match the price range below.

**QUERY AIM:**
- This query finds all orders from the table ORDERS where the date of the order matches a specific date range.

# 4d. Like

**QUERY AIMS:**
- These queries use types of regular expressions to return filtered string results.

1. Write a query to retrieve first names that start with 'z'.

2. Write a query to retrieve first names that end in 'er'.

3. Write a query to retrieve first names that begin with 't' but end in 's'.

4. Write a query to retrieve first names from a table that begin with any character, followed by a 'u', then followed by any characters.

5. Write a query to retrieve first names starting with 'Z' or 'Y'.

6. Write a query to retrieve first names not starting with any characters between 'A' and 'D'.

7. Write a query to retrieve comments that include '30%', escaping the '%' symbol in the query.

# 4e. Column Aliases

**QUERY AIM:**
- This query uses ' ' as we want to include a columns alias with spaces returning the first_name and last_name from CUSTOMERS as a column named 'Full Name'.

**QUERY AIM:**
- This query makes an inner join query giving the CUSTOMERS table the alias of 'c', and the ORDERS table the alias of 'o'.

# 5. Joining Tables

## 5a. Inner Join

**QUERY AIM:**
- This query retrieves all candidates from the CANDIDATES table whose name also appears in the EMPLOYEES table.

**QUERY AIM:**
- This inner join obtains data from two tables to get product details from the PRODUCTS table and category_name from the CATEGORIES table.

## 5b. Left Join

**QUERY AIM:**
- In this query, we want to see everyone from the CANDIDATES table, and return either NULL or if they are also in the EMPLOYEES table, returning their details.

**QUERY AIM:**
- In this query we want a list of all product names from the PRODUCTS table (LEFT table) and then either NULL or the order_ids for this product.

## 5c. Right Join

**QUERY AIM:**
- This query aims to retrieve and asses ALL employees from the EMPLOYEES table (RIGHT table) and see if they appear in the CANDIDATES table (on the left).

## 5d. Full Outer Join

**QUERY AIM:**
- This query aims to get all candidates from the CANDIDATES table and all employees from the EMPLOYEES table and show if they are in BOTH tables or just appear in one of the tables.

## 5e. Cross Join

**QUERY AIM:**
- This query aims to combine all possible combinations of store from STORES and product from PRODUCTS and then use that combination further as a LEFT table in a further left JOIN.

## 5f. Self Join

**QUERY AIM:**
- This query aims to return all employees and their manager_id using a SELF JOIN where the table EMPLOYEES is assessed against itself.

# 6. Grouping

## 6a. Group By

**QUERY AIM:**
- This query aims to return the COUNT of orders placed grouped by customer_id and year where the customer_id is either 1 or 2.

**QUERY AIM:**
- This query aims to get all cities with the COUNT of all customer_ids in each city.

**QUERY AIM:**
- This query retrieves the AVG list_price for each brand where the model_year is 2018, using GROUP BY to get the average list_price per brand.

**QUERY AIM:**
- This query aims to retrieve the total SUM of each order less discount for each order_id in the ORDER_ITEMS table.

## 6b. Having

**QUERY AIM:**
- This query aims to aggregate with SUM the totals for each salesperson but uses HAVING to only find each salesperson_name with total sales over 2000.

**QUERY AIM:**
- This query retrieves the MAX list_price and MIN list_price for each category where the MAX is less than 4000 but the MIN is greater than 500.

**QUERY AIM:**
- This query gets the AVG list_price for each category_id where the AVG is BETWEEN 500 and 1000.

## 6c. Grouping Sets

**QUERY AIM:**
- This query uses GROUPING SETS to get the SUM of sales for different combinations of brands and categories.
- The query finds the sum total for BRAND + CATEGORY, BRAND ONLY, CATEGORY ONLY and finally the blank () set returns the total SUM of sales.

## 6d. Cube

**QUERY AIM:**
- This query uses CUBE to get all possible combinations of aggregated results for columns named d1,d2 and d3. (A shorter way to create grouping sets)

**QUERY AIM:**
- This query uses a partial CUBE to only retrieve all GROUPING SETS with brand as the first dimension, so this will retrieve SUM of sales for BRAND + CATEGORY and BRAND TOTALS.

## 6e. Roll Up

**QUERY AIM:**
- This query aims to get SUM of sales for BRAND + CATEGORY, BRAND ONLY and OVERALL TOTAL.

**QUERY AIM:**
- This query assumes category is top of the hieracrchy and will retrieve the SUM of sales for CATEGORY + BRAND, CATEGORY ONLY and OVERALL TOTAL.

**QUERY AIM:**
- This query uses a partial ROLLUP to only retrieve BRAND + CATEGORY and BRAND ONLY but will not retrieve the SALES TOTAL as a full ROLLUP would do.
