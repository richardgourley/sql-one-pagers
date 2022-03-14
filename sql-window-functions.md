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

## 6. Lead

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

----------

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

