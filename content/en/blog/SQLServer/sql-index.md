---
title: Index
date: 2024-06-13
tags: [SQL]
author: "Tiationg Kho"
weight: 31
---

## Index

- **Index** is a structure that speeds up data searches
    - Pros
        - Faster data retrieval
        - Efficient data sorting
    - Cons
        - Increase storage space
        - Slower data modification operations
- **B+ Tree** is a common data structure used to implement index
    - Non-leaf level
        - Nodes contains key and pointers
    - Leaf level
        - Nodes contain the actual data records
        - Nodes are linked together in a double linked list
- **CLUSTERED INDEX** vs **NONCLUSTERED INDEX**
    - `CLUSTERED INDEX`
        - A table can have only one clustered index
        - Clustered index determines the **physical order** of data in a table
        - eg. primary key
    - `NONCLUSTERED INDEX`
        - A table can have multiple non-clustered index
        - Organizes keys separately from physical row order
        - eg. unique constraint
- **Index Creation**
    - **Through adding** `PRIMARY KEY`
        - Values must be unique and cannot be `NULL`
        - Automatically creates a clustered index by default when you define a primary key on a column
    - **Through adding** `UNIQUE` **Constraint**
        - Values must be unique and can have one `NULL` only
        - Automatically creates a non-clustered index when you define a unique constraint on a column
    - **Manual Index Creation**
        
        ```sql
        CREATE CLUSTERED INDEX IX_MyClusteredIndex
        ON MyTable(MyColumn);
        ```
        
        ```sql
        CREATE NONCLUSTERED INDEX IX_MyNonClusteredIndex
        ON MyTable(MyOtherColumn);
        ```