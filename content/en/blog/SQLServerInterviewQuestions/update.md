---
title: Update Data In Table
date: 2024-06-13
tags: [SQL]
author: "Tiationg Kho"
weight: 14
---

## Update Data In Table

```sql
UPDATE posts
SET title = 'Updated First Post'
WHERE postID = 1;
```

# [**627. Swap Salary**](https://leetcode.com/problems/swap-salary/)

```sql
/* Write your T-SQL query statement below */

UPDATE Salary
SET sex =
    CASE sex 
        WHEN 'm' THEN 'f'
        ELSE 'm'
    END;
```