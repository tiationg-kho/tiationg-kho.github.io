---
title: Delete Data In Table
date: 2024-06-13
tags: [SQL]
author: "Tiationg Kho"
weight: 15
---

## Delete Data In Table

```sql
-- without a join
DELETE FROM comments
WHERE commentID = 2;

-- with a join
DELETE comments
FROM comments
INNER JOIN posts ON comments.postID = posts.postID
WHERE posts.title = 'First Post';
```

# [**196. Delete Duplicate Emails**](https://leetcode.com/problems/delete-duplicate-emails/)

```sql
/* Write your T-SQL query statement below */

WITH cte AS (
    SELECT email, MIN(id) AS [id]
    FROM Person
    GROUP BY email
)
DELETE FROM Person
WHERE id NOT IN (SELECT id FROM cte);
```