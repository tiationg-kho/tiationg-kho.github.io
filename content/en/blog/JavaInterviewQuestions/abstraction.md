---
title: Abstraction
date: 2024-06-13
tags: [Java]
author: "Tiationg Kho"
weight: 8
---

## Abstraction

- Hide complexity, show essentials
- `abstract class` vs `interface`
    
    
    |                       | abstract class                                                                            | interface                                           |
    | --------------------- | ----------------------------------------------------------------------------------------- | --------------------------------------------------- |
    | Inheritance           | Supports single inheritance                                                               | Supports multiple inheritances                      |
    | Subclass              | Use extends to inherit                                                                    | Use implements to inherit                           |
    | Instantiation         | Cannot be instantiated                                                                    | Cannot be instantiated                              |
    | Constructor           | Can have constructors                                                                     | Cannot have constructors                            |
    | Method Accessibility  | Methods can be public, protected, default, or private                                     | Methods are public by default                       |
    | Method Implementation | Methods can be abstract or concrete                                                       | Methods are abstract by default                     |
    | Fields                | Field can be final, non-final, static, non-static, public, protected, default, or private | All fields are public, static, and final by default |