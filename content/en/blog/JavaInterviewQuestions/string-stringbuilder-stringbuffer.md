---
title: String vs StringBuilder vs StringBuffer
date: 2024-06-13
tags: [Java]
author: "Tiationg Kho"
weight: 13
---

## String vs StringBuilder vs StringBuffer

|               | String                                | StringBuilder                                                                            | StringBuffer                                               |
| ------------- | ------------------------------------- | ---------------------------------------------------------------------------------------- | ---------------------------------------------------------- |
| Mutability    | Immutable                             | Mutable                                                                                  | Mutable                                                    |
| Thread Safety | Thread-safe                           | Not thread-safe                                                                          | Thread-safe                                                |
| Use Case      | Suitable for values that won't change | Best for strings that are expected to change frequently in a single-threaded environment | Suitable for strings that are modified by multiple threads |