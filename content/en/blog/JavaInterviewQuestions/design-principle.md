---
title: Design Pattern
date: 2024-06-13
tags: [Java]
author: "Tiationg Kho"
weight: 22
---

## Design Pattern

- Singleton Pattern
    - A creational pattern that restricts the instantiation of a class to a single instance
    - eg. beans in IoC Container
- Decorator Pattern
    - A structural pattern that allows behavior to be added to an individual object, dynamically, without affecting the behavior of other objects from the same class
    - eg. `@Transactional` annotation
- Observer Pattern
    - A behavioral pattern where an object/subject maintains a list of its dependents/observers and notifies them of any state changes
    - eg. event-driven architecture