---
title: "@PostConstruct"
date: 2024-06-13
tags: [Spring]
author: "Tiationg Kho"
weight: 9
---

## @PostConstruct

- `@PostConstruct` allows to perform initialization tasks on a bean right after all its necessary dependencies have been injected by Spring but before the bean is put to use
- The method annotated with `@PostConstruct` must have no parameters, return void, and be public