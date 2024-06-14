---
title: Window Function
date: 2024-06-13
tags: [SQL]
author: "Tiationg Kho"
weight: 27
---

## Window Function

- Used to perform calculations across a set of rows related to the current row in a query
- Can use aggregate function
    - `SUM(col)`, `AVG(col)`, `COUNT(col)`, `MIN(col)`, `MAX(col)`
- Can use ranking function
    - `ROW_NUMBER()`, `RANK()`, `DENSE_RANK()`, `LAG(col)`, `LEAD(col)`
- `PARTITION BY`
    - Allows you to split the result set into smaller groups and apply the window function independently to each group
    - Whether or not you need this clause depends on the requirement of the query
        - If you want to apply a uniform window calculation across the entire result set, you don't need it
        - If you need to perform calculations group-wise, then you must use it
- `ORDER BY`
    - Determines the order of data within the window
    - Required for rank function

```sql
SELECT 
    id, 
    salesperson_id, 
    amount,
    SUM(amount) OVER (PARTITION BY salesperson_id) AS total_amount
FROM sales;

-- if you want to compute the average salary for each department
SELECT department, AVG(salary) OVER (PARTITION BY department)
FROM employees;

-- if you want to compute the overall average salary for all employees
SELECT department, AVG(salary) OVER ()
FROM employees;

-- if you want to rank employees within each department by salary
SELECT department, salary, ROW_NUMBER() OVER (PARTITION BY department ORDER BY salary DESC)
FROM employees;

-- if you want to see the difference in salary between each employee and the prev when ranked by salary across the entire company
-- `LAG` for getting previous row, `LEAD` for getting next row
SELECT employee_name, salary, LAG(salary) OVER (ORDER BY salary DESC)
FROM employees;

-- combine `GROUP BY` with window funcction
-- in this specific scenario, `PARTITION BY` is not necessary
-- the reason is that the `GROUP BY` clause already ensures that the sum of SaleAmount is calculated per employee
SELECT 
  EmployeeID,
  SUM(SaleAmount) AS TotalSales,
  RANK() OVER(ORDER BY SUM(SaleAmount) DESC) AS SalesRank
FROM EmployeeSales
GROUP BY EmployeeID;
```

# [**178. Rank Scores**](https://leetcode.com/problems/rank-scores/)

```sql
/* Write your T-SQL query statement below */

SELECT score, DENSE_RANK() OVER (ORDER BY score DESC) AS [rank]
FROM Scores
ORDER BY [rank] ASC;
```

# [**180. Consecutive Numbers**](https://leetcode.com/problems/consecutive-numbers/)

```sql
/* Write your T-SQL query statement below */

WITH cte AS (
    SELECT id, num, LAG(num) OVER (ORDER BY id ASC) AS prev_num, LEAD(num) OVER (ORDER BY id ASC) AS next_num
    FROM Logs
)
SELECT num AS ConsecutiveNums
FROM cte
WHERE prev_num = num AND num = next_num
GROUP BY num;
```

# [**184. Department Highest Salary**](https://leetcode.com/problems/department-highest-salary/)

```sql
/* Write your T-SQL query statement below */

WITH cte AS (
    SELECT 
        e.name AS [Employee], 
        e.salary AS [Salary], 
        d.name AS [Department], 
        DENSE_RANK() OVER (PARTITION BY e.departmentId ORDER BY e.salary DESC) AS [rank]
    FROM Employee e
    INNER JOIN Department d
    ON e.departmentId = d.id
)
SELECT [Department], [Employee], [Salary]
FROM cte
WHERE [rank] = 1;
```

# [**185. Department Top Three Salaries**](https://leetcode.com/problems/department-top-three-salaries/)

```sql
/* Write your T-SQL query statement below */

WITH cte AS (
    SELECT
        e.name AS [Employee], 
        e.salary AS [Salary], 
        d.name AS [Department],
        DENSE_RANK() OVER (PARTITION BY e.departmentId ORDER BY e.salary DESC) AS [rank]
    FROM Employee e
    INNER JOIN Department d
    ON e.departmentId = d.id
)
SELECT [Department], [Employee], [Salary]
FROM cte
WHERE [rank] <= 3;
```

# [**601. Human Traffic of Stadium**](https://leetcode.com/problems/human-traffic-of-stadium/)

```sql
/* Write your T-SQL query statement below */

WITH cte AS (
    SELECT 
        id, 
        visit_date, 
        people, 
        LAG(id, 2) OVER (ORDER BY id ASC) AS prev_prev_id,
        LAG(id) OVER (ORDER BY id ASC) AS prev_id,
        LEAD(id) OVER (ORDER BY id ASC) AS next_id,
        LEAD(id, 2) OVER (ORDER BY id ASC) AS next_next_id
    FROM Stadium
    WHERE people >= 100
)
SELECT id, visit_date, people
FROM cte
WHERE 
    (prev_prev_id + 1 = prev_id AND prev_id + 1 = id) 
    OR (prev_id + 1 = id AND id + 1 = next_id) 
    OR (id + 1 = next_id AND next_id + 1 = next_next_id)
ORDER BY visit_date ASC;
```