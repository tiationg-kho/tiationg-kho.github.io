---
title: Combine Or Exclude Result Sets
date: 2024-06-13
tags: [SQL]
author: "Tiationg Kho"
weight: 24
---

## Combine Or Exclude Result Sets

- `UNION`
    - Combines the result set of two or more `SELECT` statements
        - Contain only distinct values
        - Will sort the first col automatically
- `UNION ALL`
    - Combines the result set of two or more `SELECT` statements
        - Will includes duplicate values
        - Can be used in recursive CTE

```sql
SELECT col_name FROM table1_name
UNION
SELECT col_name FROM table2_name;
-- combines the result set of two or more SELECT statements (only distinct values)
-- must have the same number and same type of cols in the result sets

SELECT col_name FROM table1_name
UNION ALL
SELECT col_name FROM table2_name;
-- combines the result set of two or more SELECT statements (includes duplicates)
-- must have the same number and same type of cols in the result sets

SELECT col_name FROM table1_name
INTERSECT
SELECT col_name FROM table2_name;
-- only distinct values

SELECT col_name FROM table1_name
EXCEPT
SELECT col_name FROM table2_name;
-- only distinct values
```

# [**1795. Rearrange Products Table**](https://leetcode.com/problems/rearrange-products-table/)

```sql
/* Write your T-SQL query statement below */

SELECT product_id, 'store1' AS store, store1 AS price
FROM Products
WHERE store1 IS NOT NULL
UNION
SELECT product_id, 'store2' AS store, store2 AS price
FROM Products
WHERE store2 IS NOT NULL
UNION
SELECT product_id, 'store3' AS store, store3 AS price
FROM Products
WHERE store3 IS NOT NULL;
```

# [**1965. Employees With Missing Information**](https://leetcode.com/problems/employees-with-missing-information/)

```sql
/* Write your T-SQL query statement below */

SELECT e.employee_id
FROM Employees e
LEFT JOIN Salaries s
ON e.employee_id = s.employee_id
WHERE s.salary IS NULL
UNION
SELECT s.employee_id
FROM Employees e
RIGHT JOIN Salaries s
ON e.employee_id = s.employee_id
WHERE e.name IS NULL;
```