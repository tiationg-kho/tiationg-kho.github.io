---
title: Common Table Expression (CTE)
date: 2024-06-13
tags: [SQL]
author: "Tiationg Kho"
weight: 26
---

## Common Table Expression (CTE)

- A Common Table Expression (CTE) is a temporary result set in SQL Server that you can reference within a DML statement
    - Pros
        - Improve readability
        - Can be recursively defined
    
    ```sql
    WITH TotalSales AS (
        SELECT 
            salesperson_id, 
            SUM(amount) AS total_amount
        FROM sales
        GROUP BY salesperson_id
    )
    SELECT 
        s.id, 
        s.salesperson_id, 
        s.amount,
        ts.total_amount
    FROM sales s
    JOIN TotalSales ts 
    ON s.salesperson_id = ts.salesperson_id;
    ```
    
- Recursive CTE includes anchor member and recursive member
    - Use `UNION ALL` to combine these result sets
    
    ```sql
    WITH RecursiveCTE AS (
        -- Anchor member
        SELECT 
            2 AS Number,
            1 AS Iteration
    
        UNION ALL
    
        -- Recursive member
        SELECT 
            Number * 2,
            Iteration + 1
        FROM RecursiveCTE
        WHERE Iteration < 5
    )
    SELECT 
        Number,
        Iteration
    FROM RecursiveCTE;
    ```
    
    ```sql
    WITH RecursiveCTE AS (
        -- Anchor member
        SELECT 
            EmployeeId,
            EmployeeName,
            ManagerId,
            0 AS [Level]
        FROM Employees
        WHERE ManagerId IS NULL
    
        UNION ALL
    
        -- Recursive member
        SELECT 
            e.EmployeeId,
            e.EmployeeName,
            e.ManagerId,
            r.[Level] + 1
        FROM Employees e
        INNER JOIN RecursiveCTE r 
        ON e.ManagerId = r.EmployeeId
    )
    SELECT 
        EmployeeId,
        EmployeeName,
        ManagerId,
        [Level]
    FROM RecursiveCTE;
    ```
    

# [**1158. Market Analysis I**](https://leetcode.com/problems/market-analysis-i/)

```sql
/* Write your T-SQL query statement below */

WITH cte AS (
    SELECT u.user_id, COUNT(o.order_id) AS total
    From Users u
    INNER JOIN Orders o
    ON u.user_id = o.buyer_id
    WHERE o.order_date BETWEEN '2019-01-01' AND '2019-12-31'
    GROUP BY u.user_id
)
SELECT u.user_id AS buyer_id, u.join_date, ISNULL(cte.total, 0) AS orders_in_2019
FROM Users u
LEFT JOIN cte
ON u.user_id = cte.user_id;
```
