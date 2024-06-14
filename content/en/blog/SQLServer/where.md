---
title: Filtering Rows Based On Conditions
date: 2024-06-13
tags: [SQL]
author: "Tiationg Kho"
weight: 18
---

## Filtering Rows Based On Conditions

```sql
SELECT col_name
FROM table_name
WHERE condition;
-- condition can use `AND`, `OR`, `NOT`, `()`

SELECT col_name
FROM table_name
WHERE col_name IN (val_list); -- or sub_query
-- or `NOT IN`

SELECT col_name
FROM table_name
WHERE EXISTS (sub_query);
-- or `NOT EXISTS`

SELECT col_name
FROM table_name
WHERE col_name BETWEEN lower_bound AND upper_bound;

SELECT col_name
FROM table_name
WHERE col_name LIKE 'PatternWithWildcards';
```

### **Wildcard**

- **`_`** wildcard is used to represent exactly one character.
- **`%`** wildcard is used to represent zero, one, or multiple characters.
- **`[]`** wildcard is used to specify a set or range of characters to match.
    - **`-`** is used within **`[]`** to specify a range of characters.
    - **`^`** is used within **`[]`** to exclude characters specified in the brackets.
    - `,` is used within **`[]`** to separate the candidate characters.
    
    ```sql
    SELECT documentTitle
    FROM documents
    WHERE documentTitle LIKE '[A-C]dam';
    
    SELECT documentTitle
    FROM documents
    WHERE documentTitle LIKE 'Report [^0-9]%';
    
    SELECT documentTitle
    FROM documents
    WHERE documentTitle LIKE '[a,b]%';
    ```
    

# [**595. Big Countries**](https://leetcode.com/problems/big-countries/)

```sql
/* Write your T-SQL query statement below */

SELECT [name], [population], area
FROM World
WHERE area >= 3000000 OR [population] >= 25000000;
```

# [**1527. Patients With a Condition**](https://leetcode.com/problems/patients-with-a-condition/)

```sql
/* Write your T-SQL query statement below */

SELECT patient_id, patient_name, conditions
FROM Patients
WHERE conditions LIKE 'DIAB1%' OR conditions LIKE '% DIAB1%';
```

# [**1757. Recyclable and Low Fat Products**](https://leetcode.com/problems/recyclable-and-low-fat-products/)

```sql
/* Write your T-SQL query statement below */

SELECT product_id
FROM Products
WHERE low_fats = 'Y' AND recyclable = 'Y';
```

# [**1873. Calculate Special Bonus**](https://leetcode.com/problems/calculate-special-bonus/)

```sql
/* Write your T-SQL query statement below */

SELECT 
    employee_id, 
    CASE WHEN (employee_id % 2 = 1 AND [name] LIKE '[^M]%') THEN salary ELSE 0 END AS bonus
FROM Employees
ORDER BY employee_id ASC;
```