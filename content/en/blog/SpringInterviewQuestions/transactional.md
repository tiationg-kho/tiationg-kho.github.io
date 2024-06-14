---
title: "@Transactional"
date: 2024-06-13
tags: [Spring]
author: "Tiationg Kho"
weight: 20
---

## @Transactional

- `@Transactional` on method means that the entire method will run in a single transaction. If any exception occurs during the execution of this method, the transaction will be rolled back, ensuring data consistency