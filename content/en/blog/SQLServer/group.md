---
title: Grouping Rows With Same Values In Specified Columns
date: 2024-06-13
tags: [SQL]
author: "Tiationg Kho"
weight: 21
---

## Grouping Rows With Same Values In Specified Columns

```sql
SELECT col1_name, SUM(col2_name)
FROM table_name
GROUP BY col1_name;
-- `GROUP BY` is used with aggregate functions to perform calculations on the grouped data
-- every column in the SELECT clause must either be listed in the GROUP BY clause or be used within an aggregate function

SELECT column1, column2, AVG(column3)
FROM table_name
GROUP BY column1, column2;
-- can `GROUP BY` multiple cols
```

# [**511. Game Play Analysis I**](https://leetcode.com/problems/game-play-analysis-i/)

```sql
/* Write your T-SQL query statement below */

SELECT player_id, MIN(event_date) AS first_login
FROM Activity
GROUP BY player_id;
```

# [**586. Customer Placing the Largest Number of Orders**](https://leetcode.com/problems/customer-placing-the-largest-number-of-orders/)

```sql
/* Write your T-SQL query statement below */

SELECT TOP 1 customer_number
FROM Orders
GROUP BY customer_number
ORDER BY COUNT(*) DESC;
```

# [**1729. Find Followers Count**](https://leetcode.com/problems/find-followers-count/)

```sql
/* Write your T-SQL query statement below */

SELECT [user_id], COUNT(follower_id) AS followers_count
FROM Followers
GROUP BY [user_id];
```

# [**1741. Find Total Time Spent by Each Employee**](https://leetcode.com/problems/find-total-time-spent-by-each-employee/)

```sql
/* Write your T-SQL query statement below */

SELECT event_day AS [day], emp_id, SUM(out_time - in_time) AS total_time
FROM Employees
GROUP BY emp_id, event_day;
```