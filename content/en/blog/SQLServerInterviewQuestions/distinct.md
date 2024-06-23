---
title: Query Without Duplicate Rows
date: 2024-06-13
tags: [SQL]
author: "Tiationg Kho"
weight: 17
---

## Query Without Duplicate Rows

```sql
SELECT DISTINCT col_name
FROM table_name;

SELECT DISTINCT column1, column2, column3
FROM table_name;

SELECT COUNT(DISTINCT col_name)
FROM table_name;
```

- `DISTINCT`
    - Only get the unique values
    - Can be used with multiple columns
- `COUNT(DISTINCT col)`
    - Counts all unique non-null values in the specified column

# [**1141. User Activity for the Past 30 Days I**](https://leetcode.com/problems/user-activity-for-the-past-30-days-i/)

```sql
/* Write your T-SQL query statement below */

SELECT activity_date AS [day], COUNT(DISTINCT user_id) AS active_users
FROM Activity
WHERE activity_date > '2019-06-27' AND activity_date <= '2019-07-27'
GROUP BY activity_date;
```

# [**1148. Article Views I**](https://leetcode.com/problems/article-views-i/)

```sql
/* Write your T-SQL query statement below */

SELECT DISTINCT author_id AS id
FROM Views
WHERE author_id = viewer_id
ORDER BY author_id ASC;
```