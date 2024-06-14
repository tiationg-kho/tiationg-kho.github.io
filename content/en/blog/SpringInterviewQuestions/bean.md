---
title: Bean
date: 2024-06-13
tags: [Spring]
author: "Tiationg Kho"
weight: 4
---

## Bean

- A bean is a Java object managed by the Spring IoC container
- Bean Definition Type
    - **XML Configuration**
        - Define beans in `applicationContext.xml`
    - **Annotation-Based Configuration**
        - Define beans by using annotations like `@Component` on classes
    - **Java Configuration**
        - Defines beans in `@Configuration` classes and `@Bean` methods
- Bean Scope
    - **Singleton (Default)**
        - eg. logging service
    - **Prototype**
        - eg. order processor
    - **Request**
        - eg. user preferences
    - **Session**
        - eg. shopping cart
    - **Application**
        - eg. cache
    - **WebSocket**
        - eg. order tracking