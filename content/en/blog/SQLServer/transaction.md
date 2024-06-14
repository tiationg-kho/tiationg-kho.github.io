---
title: Transaction
date: 2024-06-13
tags: [SQL]
author: "Tiationg Kho"
weight: 3
---

## Transaction

- A sequence of one or more operations performed as a single logical unit of work
- Modes to handle transaction in SQL Server
    - Autocommit (default)
        - Each individual statement is considered a transaction
    - Implicit
        - SQL Server starts the transaction for you
        - Must configure `SET IMPLICIT_TRANSACTIONS ON;`
        - Must call `COMMIT;` at the end of transaction
    - Explicit
        - Fully control over when a transaction starts and ends
        - Must call `BEGIN TRANSACTION;` at the start of transaction
        - Must call `COMMIT;` at the end of transaction  

