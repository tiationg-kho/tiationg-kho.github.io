---
title: Entity Relationship
date: 2024-06-13
tags: [SQL]
author: "Tiationg Kho"
weight: 4
---

## Entity Relationship

- **One-to-One**
    - Relationship where a record in one table is linked to exactly one record in another table
    - eg. each student has a unique locker
- **One-to-Many**
    - Relationship where a single record in one table can be associated with one or more records in another table
    - eg. each student belongs to exactly one department, but a department can have many students
- **Many-to-Many**
    - Relationship where many records in one table are associated with many records in another table
    - Typically implemented using a conjunction table that contains foreign keys linking to the primary keys of the two tables involved
    - The conjunction table’s primary key is a composite key
    - eg. students can join multiple clubs and each club can have multiple students