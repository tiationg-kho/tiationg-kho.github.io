---
title: Normalization
date: 2024-06-13
tags: [SQL]
author: "Tiationg Kho"
weight: 6
---

## Normalization

- Normalization is a database design technique
- Normalization vs Denormalization
    - **Normalization**
        - Will divide large tables into smaller and related tables
        - Reduce redundancy
        - Improve data integrity
    - **Denormalization**
        - Improve read performance by reducing join operations
        - Will combining smaller tables into larger ones
- Step
    1. **1NF (First Normal Form)**
        - **Atomic**
            - Each cell must only contain a single value
            - Each column name must be unique
            - Each row must be unique
    2. **2NF (Second Normal Form)**
        - **No partial dependency**
    3. **3NF (Third Normal Form)**
        - **No transitive dependency**