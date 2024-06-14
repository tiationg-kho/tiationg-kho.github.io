---
title: Checked Exceptions vs Unchecked Exceptions
date: 2024-06-13
tags: [Java]
author: "Tiationg Kho"
weight: 15
---

## Checked Exceptions vs Unchecked Exceptions

|                      | Checked Exceptions                                                                                                 | Unchecked Exceptions                                                 |
| -------------------- | ------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------- |
| Definition           | Exceptions that are checked at compile-time                                                                        | Exceptions that occur at runtime and are not checked at compile-time |
| Handling Requirement | Must be either caught using a try-catch-finally block or declared in the method signature using the throws keyword | Not required to be caught or declared                                |
| Use Case             | Related to external factors                                                                                        | Related to logic issues                                              |
| Examples             | IOException, SQLException                                                                                          | NullPointerException, ArrayIndexOutOfBoundsException                 |