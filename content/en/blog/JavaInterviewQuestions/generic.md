---
title: Generic
date: 2024-06-13
tags: [Java]
author: "Tiationg Kho"
weight: 16
---

## Generic

- Generics enable types (classes and interfaces) to be parameters when defining classes, interfaces, and methods
- Pros
    - Stronger type checks at compile time
    - No casting needed
    - Ability to implement generic algorithms
- Declare Generics
    - Generic class
        - `class Name<T1, T2, ...> { /* ... */ }`
    - Generic method
        - `public <T1, T2, ...> returnType methodName(T1 param) { /* ... */ }`
- Generics Type Parameters
    - They must be defined in the class or method signature
    - Naming convention
        - `E` for element (used extensively by the Java Collections Framework)
        - `K` for key, and `V` for value
        - `N` for number
        - `T` for type
- Bound on Type Parameters
    - eg. `<T extends Number>` limits the type parameter `T` to subclasses of `Number`
- Wildcards
    - `?` for unknown type