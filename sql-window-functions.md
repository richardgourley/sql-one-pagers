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

