---
title: Aggregate Function
date: 2024-06-13
tags: [SQL]
author: "Tiationg Kho"
weight: 20
---

## Aggregate Function

- Perform a calculation on a set of values and return a single value

```sql
SELECT AVG(col_name)
FROM table_name
-- we can use `AVG`, `MIN`, `MAX`, `SUM`, `COUNT`
```

- `COUNT(*)`
    - Counts the total number of rows in the result set, even if some of those rows contain only `NULL` values in all their columns
    - Will returns `0` when used on an empty set
- `COUNT(col)`
    - It counts non-NULL values in that col
    - Will returns `0` when used on an empty set
- `AVG(col)`, `MIN(col)`, `MAX(col)`, `SUM(col)`
    - Will ignore `NULL` in calculation
    - But if all values are `NULL`, then return will be `NULL`
    - If use in empty set, then return will be `NULL`
    
    ```sql
    // result is one row with a NULL value
    SELECT MAX(columnName)
    FROM table_name
    WHERE 1=0;
    ```
    

# [**176. Second Highest Salary**](https://leetcode.com/problems/second-highest-salary/)

```sql
/* Write your T-SQL query statement below */

WITH cte AS (
    SELECT salary, DENSE_RANK() OVER (ORDER BY salary DESC) AS [rank]
    FROM Employee
)
SELECT MAX(salary) AS SecondHighestSalary
FROM cte
WHERE [rank] = 2;
```

# [**1179. Reformat Department Table**](https://leetcode.com/problems/reformat-department-table/)

```sql
/* Write your T-SQL query statement below */

SELECT 
    id,
    SUM(CASE WHEN month = 'Jan' THEN revenue ELSE NULL END) AS Jan_Revenue,
    SUM(CASE WHEN month = 'Feb' THEN revenue ELSE NULL END) AS Feb_Revenue,
    SUM(CASE WHEN month = 'Mar' THEN revenue ELSE NULL END) AS Mar_Revenue,
    SUM(CASE WHEN month = 'Apr' THEN revenue ELSE NULL END) AS Apr_Revenue,
    SUM(CASE WHEN month = 'May' THEN revenue ELSE NULL END) AS May_Revenue,
    SUM(CASE WHEN month = 'Jun' THEN revenue ELSE NULL END) AS Jun_Revenue,
    SUM(CASE WHEN month = 'Jul' THEN revenue ELSE NULL END) AS Jul_Revenue,
    SUM(CASE WHEN month = 'Aug' THEN revenue ELSE NULL END) AS Aug_Revenue,
    SUM(CASE WHEN month = 'Sep' THEN revenue ELSE NULL END) AS Sep_Revenue,
    SUM(CASE WHEN month = 'Oct' THEN revenue ELSE NULL END) AS Oct_Revenue,
    SUM(CASE WHEN month = 'Nov' THEN revenue ELSE NULL END) AS Nov_Revenue,
    SUM(CASE WHEN month = 'Dec' THEN revenue ELSE NULL END) AS Dec_Revenue
FROM Department
GROUP BY id;
```

# [**1693. Daily Leads and Partners**](https://leetcode.com/problems/daily-leads-and-partners/)

```sql
/* Write your T-SQL query statement below */

SELECT date_id, make_name, COUNT(DISTINCT lead_id) AS unique_leads, COUNT(DISTINCT partner_id) AS unique_partners
FROM DailySales
GROUP BY date_id, make_name;
```