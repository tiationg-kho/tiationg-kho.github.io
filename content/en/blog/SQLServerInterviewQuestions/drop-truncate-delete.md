---
title:  DROP vs TRUNCATE vs DELETE
date: 2024-06-13
tags: [SQL]
author: "Tiationg Kho"
weight: 9
---

## DROP vs TRUNCATE vs DELETE

| DROP                                      | TRUNCATE                                                                                                                                  | DELETE                                                 |
| ----------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------ |
| Remove an entire object from the database | 1. Remove all rows from a table without logging individual row deletions or firing triggers. 2. Identity sequence reset to its seed value | Remove specific rows from a table based on a condition |
| DDL                                       | DDL                                                                                                                                       | DML                                                    |
|                                           |                                                                                                                                           | Can be rollback                                        |
| DROP TABLE comments;                      | TRUNCATE TABLE comments;                                                                                                                  | DELETE FROM comments WHERE commentID = 2;              |