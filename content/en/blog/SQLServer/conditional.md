---
title: Conditional Logic
date: 2024-06-13
tags: [SQL]
author: "Tiationg Kho"
weight: 29
---

## Conditional Logic

```sql
SELECT 
    name, 
    [status],
    CASE [status]
        WHEN 'active' THEN 'Currently in use'
        WHEN 'inactive' THEN 'No longer in use'
        WHEN 'pending' THEN 'Awaiting approval'
        WHEN 'obsolete' THEN 'Outdated and not used'
        ELSE 'Unknown status'
    END AS status_description
FROM products;

SELECT 
    name, 
    grade,
    CASE 
        WHEN grade >= 90 THEN 'A'
        WHEN grade >= 80 AND grade < 90 THEN 'B'
        WHEN grade >= 70 AND grade < 80 THEN 'C'
        WHEN grade >= 60 AND grade < 70 THEN 'D'
        ELSE 'F'
    END AS grade_letter
FROM students;

CASE col WHEN val THEN res_when_val_met ELSE res_when_val_not_met END

CASE WHEN expression THEN value_if_true ELSE value_if_false END

ISNULL(expression, replacement_value)
```

# [**262. Trips and Users**](https://leetcode.com/problems/trips-and-users/)

```sql
/* Write your T-SQL query statement below */

SELECT 
    t.request_at AS [Day], 
    ROUND(SUM(CASE t.status WHEN 'completed' THEN 0 ELSE 1 END) / CAST(COUNT(*) AS FLOAT), 2) AS [Cancellation Rate]
FROM Trips t
INNER JOIN Users u1
ON t.client_id = u1.users_id
INNER JOIN Users u2
ON t.driver_id = u2.users_id
WHERE u1.banned = 'No' AND u2.banned = 'No' AND t.request_at BETWEEN '2013-10-01' AND '2013-10-03'
GROUP BY t.request_at;
```

# [**608. Tree Node**](https://leetcode.com/problems/tree-node/)

```sql
/* Write your T-SQL query statement below */

WITH [root] AS (
    SELECT t1.id
    FROM Tree t1
    WHERE t1.p_id IS NULL
),
parent AS (
    SELECT DISTINCT t2.p_id
    FROM Tree t2
    WHERE t2.p_id IS NOT NULL
)
SELECT 
    t.id, 
    CASE
        WHEN t.id IN (SELECT id FROM [root]) THEN 'Root'
        WHEN t.id IN (SELECT p_id FROM parent) THEN 'Inner'
        ELSE 'Leaf'
    END AS [type]
FROM Tree t;
```

# [**626. Exchange Seats**](https://leetcode.com/problems/exchange-seats/)

```sql
/* Write your T-SQL query statement below */

WITH cte AS (
    SELECT 
        id,
        student,
        LAG(student) OVER (ORDER BY id ASC) AS prev_student,
        LEAD(student) OVER (ORDER BY id ASC) AS next_student
    FROM Seat
)
SELECT
    id,
    CASE 
        WHEN id % 2 = 1 AND next_student IS NULL THEN student
        WHEN id % 2 = 1 THEN next_student
        ELSE prev_student
    END AS student
FROM cte
ORDER BY id ASC;
```

# [**1393. Capital Gain/Loss**](https://leetcode.com/problems/capital-gainloss/)

```sql
/* Write your T-SQL query statement below */

WITH cte AS (
    SELECT stock_name, operation_day, CASE WHEN operation = 'Buy' THEN - price ELSE price END AS price
    FROM Stocks
)
SELECT stock_name, SUM(price) AS capital_gain_loss
FROM cte
GROUP BY stock_name;
```

# [**1407. Top Travellers**](https://leetcode.com/problems/top-travellers/)

```sql
/* Write your T-SQL query statement below */

WITH cte AS (
    SELECT u.id, u.name, ISNULL(SUM(r.distance), 0) AS travelled_distance
    FROM Users u
    LEFT JOIN Rides r
    ON u.id = r.user_id
    GROUP BY u.id, u.name
)
SELECT [name], travelled_distance
FROM cte
ORDER BY travelled_distance DESC, [name] ASC;
```