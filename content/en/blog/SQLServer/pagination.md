---
title: Pagination
date: 2024-06-13
tags: [SQL]
author: "Tiationg Kho"
weight: 28
---

## Pagination

- `TOP`
    - Return a specified number of rows from the beginning of the result set
    - Better used with `ORDER BY`
    - Can be like `TOP 5` or `TOP 5 PERCENT`
- `OFFSET n ROWS FETCH NEXT m ROWS ONLY`
    - Skip a specific number of rows and then take a fixed number of rows following the skipped ones
    - Must used with `ORDER BY`

```sql
SELECT TOP 10 *
FROM Person.Address;
-- select first 10 rows from this table

SELECT *
FROM Person.Address
ORDER BY AddressID ASC
OFFSET 5 ROWS FETCH NEXT 10 ROWS ONLY;
-- select 6th - 15th rows from this table by this order
```