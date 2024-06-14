---
title: final vs finally vs finalize
date: 2024-06-13
tags: [Java]
author: "Tiationg Kho"
weight: 11
---

## final vs finally vs finalize

|       | final                                                                             | finally                         | finalize                                                                                           |
| ----- | --------------------------------------------------------------------------------- | ------------------------------- | -------------------------------------------------------------------------------------------------- |
| Usage | Prevents modification (variables), overriding (methods), or inheritance (classes) | Use in try-catch-finally blocks | Method invoked by the garbage collector before an object is reclaimed, used for cleanup operations |