---
title: WHERE vs HAVING
date: 2024-06-13
tags: [SQL]
author: "Tiationg Kho"
weight: 8
---

## WHERE vs HAVING

| WHERE                                                              | HAVING                                                                |
| ------------------------------------------------------------------ | --------------------------------------------------------------------- |
| Filter individual rows based on conditions involving column values | Filter groups of rows based on conditions involving aggregated values |
|                                                                    | Must used after GROUP BY                                              |
|                                                                    | Contain aggregate function                                            |
| Used in SELECT, UPDATE, or DELETE statements                       | Used in SELECT statements                                             |