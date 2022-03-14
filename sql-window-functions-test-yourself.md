# SQL Window Functions - Test Yourself
- Use the examples and notes from 'sql-window-functions.ipnb' to check syntax knowledge and understanding first.
- Try to write the query examples below and explain to yourself what the result should be. Check any gaps in your knowledge.

## 1. Cumulative Distribution
- Write a query that uses CUME_DIST and ORDER BY. The result should tell us the cumulative distribution for net sales for each salesperson ordered by net_sales.
- Write a query that uses CUME_DIST, PARTITION BY and ORDER BY. The result should tell us the cumulative distribution for net sales of each salesperson, first for 2016, and then for 2017.

## 2. Dense Rank
- Write a query that uses DENSE_RANK, PARTITION BY and ORDER BY. The result should give a ranking to all products based on and ordered by their list price ranked using DENSE_RANK.
- Write a query that uses DENSE_RANK and ORDER BY. The result should give a ranking to all products based on and ordered by their list price ranked using DENSE_RANK. The results should be partitioned into category_ids.

## 3. First Value
- Write a query that uses FIRST_VALUE and ORDER BY. The query should return sales quantity information for each category. The category with the lowest sales quantity should appear in every row in a lowest_sales_volume column.  The results should be for the year 2017.
- Write a query that uses FIRST_VALUE. PARTITION BY and ORDER BY. The query should return sales quantity information for each category. The category with the lowest sales quantity should appear in every row in a lowest_sales_volume column.  The results should be partitioned by year. Only show results for 2016 and 2017.

## 4. Lag
- Write a query that uses LAG and ORDER BY. The query should return the month, net sales for that month and another column with the previous months net sales.  The sales should be for 2018.  A CTE is required to firstly group the SUM of net sales by month.
- Write a query that uses LAG, PARTITION BY and ORDER BY. The query should partition the results by brand and then order by month. The query should display month, brand, net sales, previous months sales. The query should return results for 2018.
**EXTRA:** Add another column that calculates the % differences between net sales for the current month and the net sales from the previous month.

## 5. Last Value
- Write a query that uses LAST VALUE, ORDER BY and RANGE. The query should return quantity sales for each category name and year and include another column that states the category with the highest overall quantity total for the table. The years required are 2016 and 2017.
- Write a query that uses LAST VALUE, PARTITION BY, ORDER BY and RANGE. The query should return quantity sales for each category name and year and include another column that states the category with the highest overall quantity total for the year of the row. The query should be partitioned into years.  The years required are 2016 and 2017.

## 6. Lead
- Write a query that uses LEAD (OVER), PARTITTION BY and ORDER BY. The query should return net sales per brand for 2018, and a column named next_month_sales that returns the net_sales value for the next month.

## 7. NTile
- Write a query that uses NTILE (OVER), PARTITION BY and ORDER BY. The query should return the net_sales for each category, by month, with the an extra column named net_sales_group which has a number which indicates the group the results belongs to, after ordering net_sales in descending order, and dividing the results into 4 groups.

## 8. Percent Rank
- Write a query that uses FORMAT, PERCENT_RANK (OVER), PARTITION BY and ORDER BY. The query should return the full name of the staff member, their total net_sales grouped (partitioned) by 2016 and 2017, and a column named percent_rank showing where each person's net_sales appears as a formatted percentage figure, relative to every other sales person.
