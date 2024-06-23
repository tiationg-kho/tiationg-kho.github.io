---
title: SELECT Execution Order
date: 2024-06-13
tags: [SQL]
author: "Tiationg Kho"
weight: 16
---

## SELECT Execution Order

```sql
6. SELECT 
       col, 
       aggregate_func(col), 
       windwo_func(col) OVER (PARTITION BY col ORDER BY col)
1. FROM table1
2. JOIN table2 ON table1.col1 = table2.col2
3. WHERE condition
4. GROUP BY col
5. HAVING condition
7. ORDER BY col
---
1. FROM -> 2. JOIN ON -> 
3. WHERE ->
4. GROUP BY -> 5. HAVING
6. SELECT -> 7. DISTINCT
8. ORDER BY -> 9. `TOP` or `OFFSET n ROWS FETCH NEXT m ROWS ONLY`
```