# SQL Window Functions - One Page

- A one page reference of the most common Window functions for SQL.
- These are often used in retrieving information for analysis.
- Query aims and notes are added to each query.
- To keep the length down, table creation is not included BUT the data types used in the examples are clear.

**CONTENT:**

**1. Cumulative Distribution**

**2. Dense Rank**

**3. First Value**

**4. Lag**

**5. Last Value**

**6. Lead**

**7. NTile**

**8.Percent Rank**

**9. Rank**

**10.Low Number**

---------
# 1. Cumulative Distribution

**QUERY AIM:**
- This query aims to tell us where the sales persons net_sales come, relative to the net_sales of all of the other sales people.

**NOTES:**
- The PARTITION BY clause is optional and not included in this query. So, the CUME_DIST function will treat the result set as one partition.
- An example of the middle section of a result set could like this:

**full_name, net_sales, cume_dist**

Bob, 360, 0.4

Sandra 320, 0.5

Debbie, 329, 0.62

- In the example above, we can see that Sandra's net_sales of 320 are the halfway point. 50% of the sales people have net_sales higher than 320.

```
SELECT 
    CONCAT_WS(' ',first_name,last_name) full_name,
    net_sales, 
    CUME_DIST() OVER (
        ORDER BY net_sales DESC
    ) cume_dist
FROM 
    sales.vw_staff_sales t
INNER JOIN sales.staffs m on m.staff_id = t.staff_id
WHERE 
    year = 2017;
```

**QUERY AIM:**
- This query aims to tell us where the sales persons net_sales come, relevant to other salespeople by year. Only the results for 2016 and 2017 are retrieved.

**NOTES:**
- PARTITION BY is used - we receive the cumulative distribution of net_sales in year groups.
- The query returns all salespeople, net sales, cumulative distribution for 2016 and then repeats for each salesperson for 2017.
- This query can be used as a CTE or in a subquery to further filter the results to find, say the top 10% of salespeople per year by adding a WHERE cume_dist >= 0.10

```
SELECT 
    CONCAT_WS(' ',first_name,last_name) full_name,
    net_sales, 
    year,
    CUME_DIST() OVER (
        PARTITION BY year
        ORDER BY net_sales DESC
    ) cume_dist
FROM 
    sales.vw_staff_sales t
INNER JOIN sales.staffs m on m.staff_id = t.staff_id
WHERE 
    year IN (2016,2017);
```

# 2. Dense Rank

**QUERY AIM:**
- This query aims to give rankings with ordered ranking groups with 1 for the highest for the list price of products.

**NOTES:**
- DENSE_RANK() is relevant when their are ties in totals.
- DENSE_RANK() groups totals into a rank in order 1,2,3,4 etc. regardless of how many items are tied in each group.
- Here is how a results with DENSE_RANK might look.....

**Total Rank**

50, 1

50, 1

50, 1

60, 2 (In normal ranking, this would be considered as 4th position)

60, 2

70, 3 (In normal ranking, this would be considered as 7th postion)

```
SELECT
    product_id,
    product_name,
    list_price,
    DENSE_RANK () OVER ( 
        ORDER BY list_price DESC
    ) price_rank 
FROM
    production.products;
```

**QUERY AIM:**
- This query again gives a ranking to each product list price inside a ranking group but this query ranks the products in sections of category id.

**NOTES:**
- The PARTITION BY category_id means we have the results returned in sections by category_id.
- DENSE_RANK() will group any tied values together (see above)

```
SELECT
        product_id,
        product_name,
        category_id,
        list_price,
        DENSE_RANK () OVER ( 
            PARTITION BY category_id
            ORDER BY list_price DESC
        ) price_rank 
    FROM
        production.products
```

# 3. First Value

**QUERY AIM:**
- This query aims to display category and quantity information for each category followed by a spearate column that has the category name of the category with the lowest quantity of orders.

**NOTES:**
- FIRST_VALUE is used to display the category_name in a lowest_sales_volume column for every row.
- PARTITION BY is not used so the entire result set is evaluated and ONE category will appear in the lowest_sales_volume column for the entire table.

```
SELECT 
    category_name,
    year,
    qty,
    FIRST_VALUE(category_name) OVER(
        ORDER BY qty
    ) lowest_sales_volume
FROM 
    sales.vw_category_sales_volume
WHERE
    year = 2017;
```

**QUERY AIM:**
- This query aims to display category, year and quantity information per year as well as a lowest_sales_volume column with the name of the category with the lowest sales volume for that year.

**NOTES:**
- PARTITION BY is used to partition the results by year.
- The results would look something like this:

**category_name year qty lowest_sales_volume**

CAT A, 2016, 52, CAT A

CAT B, 2016, 60, CAT A

CAT B, 2017, 41, CAT B

CAT A, 2017, 53, CAT B

```
SELECT 
    category_name,
    year,
    qty,
    FIRST_VALUE(category_name) OVER(
        `PARTITION BY` year
        ORDER BY qty
    ) lowest_sales_volume
FROM 
    sales.vw_category_sales_volume
WHERE
    year BETWEEN 2016 AND 2017;
```

# 4. Lag

**QUERY AIM:**
- This query aims to print net sales for each month in 2018 and in the same row, have a column that displays the previous months sales.

**NOTES:**
- LAG is useful for comparing a value in the current row with a value in the previous row.
- In this query, LAG allows us to create further columns calculating current months sales vs. previous months sales.
- When using LAG, the first result will have a NULL value because there are no previous results for the first column. An example...

**Month, net_sales, previous_month_sales**

January, 200, NULL

February, 240, 200

March, 190, 240

```
WITH cte_netsales_2018 AS(
    SELECT 
        month, 
        SUM(net_sales) net_sales
    FROM 
        sales.vw_netsales_brands
    WHERE 
        year = 2018
    GROUP BY 
        month
)
SELECT 
    month,
    net_sales,
    LAG(net_sales,1) OVER (
        ORDER BY month
    ) previous_month_sales
FROM 
    cte_netsales_2018;
```

**QUERY AIM:**
- This query aims to display net sales partitioned by brand and then grouped by month with an additional column in each row showing the previous months net sales.

**NOTES:**
- LAG allows us to see the previous months sales next to the current month.
- PARTITION BY allows us to group results together within the LAG function by brand.

```
SELECT 
    month,
    brand_name,
    net_sales,
    LAG(net_sales,1) OVER (
        PARTITION BY brand_name
        ORDER BY month
    ) next_month_sales
FROM 
    sales.vw_netsales_brands
WHERE
    year = 2018;
```

# 5. Last Value

**QUERY AIM:**
- This query retrieves category_name, year and quantity of orders, ordered in a non-ascending way, and then a highest sales volume column which displays the highest category_name (last value) for the entire table.

**NOTES:**
- PARTITON BY is not used so the entire table is used undivided.
- RANGE allows defining of start and end points within a partition.

```
SELECT 
    category_name,
    year,
    qty,
    LAST_VALUE(category_name) OVER(
        ORDER BY qty
         RANGE BETWEEN 
            UNBOUNDED PRECEDING AND 
            UNBOUNDED FOLLOWING
    ) highest_sales_volume
FROM 
    sales.vw_category_sales_volume
WHERE
    year = 2016;
```

**QUERY AIM:**
- This query aims to return the category name, year, quantity sold and for each category with a further column displaying the category with the highest quantity for the year of the row. The search limits results to the years 2016 and 2017.

**NOTES:**
- PARTITION BY year will break the results into two partition sets for each year with the highest quantity category being displayed in a column for that year appearing in all rows for that year.

```
SELECT 
    category_name,
    year,
    qty,
    LAST_VALUE(category_name) OVER(
            PARTITION BY year
        ORDER BY qty
        RANGE BETWEEN 
            UNBOUNDED PRECEDING AND 
            UNBOUNDED FOLLOWING
    ) highest_sales_volume
FROM 
    sales.vw_category_sales_volume
WHERE
    year IN (2016,2017);
```

# 6. Lead

**QUERY AIM:**
- This query aims to return net sales per brand, per month, ordered by month for 2018, with an additional column that returns the sales for the FOLLOWING month in a column next to the net sales for each month.

**NOTES:**
- LEAD is useful for comparing the value of the current row with the value of the next row, or a number of rows ahead.
- LEAD gives you side by side, a sales total for the current month (or year or quarter) and the result from the following month (or more than 1 month, as you require.)
-  The results would look something like this...

**Month, Brand, net_sales, next_month_sales**

1, BrandA, 300, 700

2, BrandA, 700, 400

3, BrandA, 400, 600

.....

12, BrandA, 380, NULL

```
SELECT 
	month,
	brand_name,
	net_sales,
	LEAD(net_sales,1) OVER (
		PARTITION BY brand_name
		ORDER BY month
	) next_month_sales
FROM 
	sales.vw_netsales_brands
WHERE
	year = 2018;
```

# 7. NTile

**QUERY AIM:**
- This query returns net_sales for each category by month and an extra column named 'net_sales_group' which uses NTILE(4) to group the results (ordered by net_sales DESC) into 4 groups.

**NOTES:**
- NTILE effectively groups the results returned. If you specify NTILE(4) for a result set of 12 rows, you will have 4 groups of 3.
- How you order the results determines if its the highest or lowest values appearing first. Then you can group those results.
- As an example, if the salespeople were ordered with highest sales first, here is how returning NTILE(3) as a column called 'sales_ranking' would result in 3 groups of 2 if we had 6 salespeople...

**Salesperson, Total, sales_ranking**

Bob, 4500, 1

Sally, 4300, 1

Jenny, 4000, 2

Bill, 3800, 2

Dave, 3500, 2

Tony, 3200, 3

```
SELECT
	category_name,
	month, 
	FORMAT(net_sales,'C','en-US') net_sales,
	NTILE(4) OVER(
		PARTITION BY category_name
		ORDER BY net_sales DESC
	) net_sales_group
FROM 
	sales.vw_netsales_2017;
```

# 8. Percent Rank

**QUERY AIM:**
- This query retrieves the full name of each salesperson, their net sales grouped by the years 2016 and 2017 using PARTITION BY and a column showing where their net_sales lie as a percentage rank (top 20%, top 40% etc.) relative to the other salespeople.

**NOTES:**
- PERCENT RANK gives you a column which ranks the row as a percentage relative to other results.
- PERCENT RANK returns the result as a numeric percentage.  FORMAT can be used to format the value into a %.
- As with most other window functions, PARTITION BY is optional. If not used, then the whole result set is treated as one partition.
- Here is an example of results you might get if using PERCENT RANK...

**Salesperson, Total, percent_rank**

Bob, 4500, 100.0%

Sally, 4300, 80.0%

Jenny, 4000, 60.0%

Bill, 3800, 40.0%

.......

```
SELECT 
    year,
    CONCAT_WS(' ',first_name,last_name) full_name,
    net_sales, 
    FORMAT(
        PERCENT_RANK() OVER (
            PARTITION BY year
            ORDER BY net_sales DESC
        ) ,
    'P') percent_rank

FROM 
    sales.vw_staff_sales t
INNER JOIN sales.staffs m on m.staff_id = t.staff_id
WHERE 
    YEAR IN (2016,2017);
```

