---
title: Filtering Group Results
date: 2024-06-13
tags: [SQL]
author: "Tiationg Kho"
weight: 22
---

## Filtering Group Results

```sql
SELECT col1_name, SUM(col2_name)
FROM table_name
GROUP BY col1_name
HAVING condition;
-- the condition here will be involed the aggregate function
-- eg. HAVING SUM(revenue) > 1500
```

# [**182. Duplicate Emails**](https://leetcode.com/problems/duplicate-emails/)

```sql
/* Write your T-SQL query statement below */

SELECT email AS Email
FROM Person
GROUP BY email
HAVING COUNT(*) > 1;
```

# [**596. Classes More Than 5 Students**](https://leetcode.com/problems/classes-more-than-5-students/)

```sql
/* Write your T-SQL query statement below */

SELECT class
FROM Courses
GROUP BY class
HAVING COUNT(*) >= 5;
```

# [**1050. Actors and Directors Who Cooperated At Least Three Times**](https://leetcode.com/problems/actors-and-directors-who-cooperated-at-least-three-times/)

```sql
/* Write your T-SQL query statement below */

SELECT actor_id, director_id
FROM ActorDirector
GROUP BY actor_id, director_id
HAVING COUNT(actor_id) >= 3;
```

# [**1084. Sales Analysis III**](https://leetcode.com/problems/sales-analysis-iii/)

```sql
/* Write your T-SQL query statement below */

SELECT p.product_id, p.product_name
FROM Product p
INNER JOIN Sales s
ON p.product_id = s.product_id
GROUP BY p.product_id, p.product_name
HAVING MAX(s.sale_date) <= '2019-03-31' AND MIN(s.sale_date) >= '2019-01-01';
```

# [**1587. Bank Account Summary II**](https://leetcode.com/problems/bank-account-summary-ii/)

```sql
/* Write your T-SQL query statement below */

WITH cte AS (
    SELECT u.account, SUM(t.amount) AS balance
    FROM Users u
    INNER JOIN Transactions t
    ON u.account = t.account
    GROUP BY u.account
    HAVING SUM(t.amount) > 10000
)
SELECT u.name, cte.balance
FROM cte
INNER JOIN Users u
ON cte.account = u.account;
```