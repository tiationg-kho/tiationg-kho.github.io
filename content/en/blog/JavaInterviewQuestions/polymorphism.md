---
title: Polymorphism
date: 2024-06-13
tags: [Java]
author: "Tiationg Kho"
weight: 7
---

## Polymorphism

- Same name, different execution
- **Method Overloading**
    - Compile-Time Polymorphism
    - Static binding
    - Same method name, different parameter lists
        - Different parameter lists are decided by different number/type/order of parameters
- **Method Overriding**
    - Runtime Polymorphism
    - Dynamic binding
    - Same method name and parameter list, but different implementations in different classes (superclass and subclass)
    - Require inheritance and using `@Override`