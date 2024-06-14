---
title: "@Autowired"
date: 2024-06-13
tags: [Spring]
author: "Tiationg Kho"
weight: 8
---

## @Autowired

- `@Autowired` is used for automatic dependency injection in Spring. It can be applied to constructors, methods, and fields
    
    ```java
    @Component
    public class MyService {
    
        @Autowired
        private MyRepository myRepository;
    }
    ```
    
- Use `@Autowired` with `@Qualifier` can specify which implementation to inject
- Use `@Primary` with `@Component` can set that implementation as default bean