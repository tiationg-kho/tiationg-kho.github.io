---
title: Isolation Level
date: 2024-06-13
tags: [SQL]
author: "Tiationg Kho"
weight: 12
---

## Isolation Level

- Isolation level refers to the degree to which a transaction is isolated from modifications made by other transactions
    - eg. `SET TRANSACTION ISOLATION LEVEL REPEATABLE READ;`
- **Concurrency problem** in SQL database
    - **Dirty Reads**
        - Reading uncommitted changes
    - **Lost Update**
        - Concurrent updates overwrite each other
    - **Non-repeatable Reads**
        - Different results from the same query in a transaction
    - **Phantom Reads**
        - New rows appear in a query's results within the same transaction

| Isolation Level  | Dirty Reads | Lost Update | Non-repeatable Reads | Phantom Reads | Description                                                                                                                                                          |
| ---------------- | ----------- | ----------- | -------------------- | ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| READ UNCOMMITTED | O           | O           | O                    | O             | Allow reading uncommitted data                                                                                                                                       |
| READ COMMITTED   | X           | O           | O                    | O             | 1. Default isolation level. 2. Disallow reading uncommitted data                                                                                                     |
| REPEATABLE READ  | X           | X           | X                    | O             | 1. Disallow reading uncommitted data. 2. No other transactions can modify data that has been read by the current transaction until the current transaction completes |
| SERIALIZABLE     | X           | X           | X                    | X             | Ensure transactions occur in a strict sequence                                                                                                                       |