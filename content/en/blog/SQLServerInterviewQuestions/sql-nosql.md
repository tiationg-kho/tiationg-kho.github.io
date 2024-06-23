---
title: SQL Database vs NoSQL Database
date: 2024-06-13
tags: [SQL]
author: "Tiationg Kho"
weight: 2
---

## SQL Database vs NoSQL Database

- **SQL Database**
    - Suitable for applications requiring a fixed schema
    - Support complex queries
    - Strict data integrity
    - **ACID properties**
        - **Atomicity**
            - A transaction is all-or-nothing
        - **Consistency**
            - Database remains in valid state before and after a transaction
        - **Isolation**
            - Transactions do not affect each other
        - **Durability**
            - Committed transactions are saved permanently
- **NoSQL Database**
    - Suitable for applications with changing requirements
    - Store and query unstructured or semi-structured data
    - Handle high volumes of data and traffic
    - **BASE properties**
        - **Basically Available**
            - System guarantees availability
        - **Soft State**
            - System's state is not fixed
        - **Eventually Consistent**
            - System will become consistent over time
    - Type
        1. Key-Value Pair
            - eg. cache
        2. Document-Oriented
            - eg. content management system
        3. Graph-Based
            - eg. recommendation engine
        4. Column-Oriented
            - eg. big data analytic
        5. Search Engine
            - eg. full-text search
        6. Time Series
            - eg. monitoring system