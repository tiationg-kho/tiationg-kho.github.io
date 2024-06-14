---
title: Aspect-Oriented Programming (AOP)
date: 2024-06-13
tags: [Spring]
author: "Tiationg Kho"
weight: 6
---

## Aspect-Oriented Programming (AOP)

- AOP in Spring allows you to separate cross-cutting concerns from your application logic
    - eg. transaction management, logging, security, exception
- Use `@Aspect` with `@Component` on class can create a aspect bean
    - `@Before(”pointcut”)` on method let this method execute before pointcut methods
    - `@After(”pointcut”)` on method let this method execute after pointcut methods