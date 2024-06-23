---
title: CAP Theorem
date: 2024-06-13
tags: [SQL]
author: "Tiationg Kho"
weight: 1
---

## CAP Theorem

- **CAP Theorem** is a fundamental principle in distributed systems that addresses the trade-offs involved in building distributed databases
    - CP system (eg. banking system)
    - AP system (eg. e-commerce App)
- **Consistency**
    - Every read reflects the most recent write or an error
- **Availability**
    - Every request gets a non-error response, without guarantee of it being the latest
- **Partition Tolerance**
    - System continues to work regardless of losing network connectivity between nodes