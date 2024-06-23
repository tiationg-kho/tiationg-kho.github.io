---
title: Subquery
date: 2024-06-13
tags: [SQL]
author: "Tiationg Kho"
weight: 25
---

## Subquery

- A subquery is a `SELECT` query that is nested within another DML statement
    - Subquery used in `FROM` clause is called **Derived Table**
- **Simple subquery**
    - Simple subquery is independent of the outer query
    - Simple subquery executed before the main query and provide results to the outer query
- **Correlated subquery**
    - Correlated subquery references cols from the outer query
    - Correlated subquery is executed for each row of the main query

```sql
-- simple subquery
SELECT 
    s.id, 
    s.salesperson_id, 
    s.amount, 
    total_sales.total_amount
FROM sales s
JOIN 
    (SELECT salesperson_id, SUM(amount) AS total_amount
     FROM sales
     GROUP BY salesperson_id) total_sales
ON s.salesperson_id = total_sales.salesperson_id;

-- correlated subquery
SELECT 
    s.id, 
    s.salesperson_id, 
    s.amount,
    (SELECT SUM(amount)
     FROM sales
     WHERE salesperson_id = s.salesperson_id) AS total_amount
FROM sales s;
```

# [**607. Sales Person**](https://leetcode.com/problems/sales-person/)

```sql
/* Write your T-SQL query statement below */

WITH cte AS (
    SELECT DISTINCT s.sales_id
    FROM SalesPerson s
    LEFT JOIN Orders o
    ON s.sales_id = o.sales_id
    LEFT JOIN Company c
    ON o.com_id = c.com_id
    WHERE c.name = 'RED'
)
SELECT [name]
FROM SalesPerson
WHERE sales_id NOT IN (SELECT sales_id FROM cte);
```

# [**1581. Customer Who Visited but Did Not Make Any Transactions**](https://leetcode.com/problems/customer-who-visited-but-did-not-make-any-transactions/)

```sql
/* Write your T-SQL query statement below */

SELECT customer_id, COUNT(visit_id) AS count_no_trans
FROM Visits v
WHERE visit_id NOT IN (SELECT DISTINCT visit_id FROM Transactions)
GROUP BY customer_id;

/* Write your T-SQL query statement below */

SELECT v.customer_id, COUNT(v.visit_id) AS count_no_trans
FROM Visits v
LEFT JOIN Transactions t
ON v.visit_id = t.visit_id
WHERE t.transaction_id IS NULL
GROUP BY customer_id;
```