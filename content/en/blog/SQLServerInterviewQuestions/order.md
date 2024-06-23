---
title: Sorting Results
date: 2024-06-13
tags: [SQL]
author: "Tiationg Kho"
weight: 19
---

## Sorting Results

```sql
SELECT *
FROM table_name
ORDER BY col_name ASC;
-- can use `ASC`, `DESC`

SELECT column1, column2, column3
FROM table_name
ORDER BY column1, column2 DESC, column3 ASC;
-- ascending is the default sort order
-- can `ORDER BY` multiple conditions
```

# [**620. Not Boring Movies**](https://leetcode.com/problems/not-boring-movies/)

```sql
/* Write your T-SQL query statement below */

SELECT id, movie, [description], rating
FROM Cinema
WHERE [description] != 'boring' AND id % 2 = 1
ORDER BY rating DESC;
```