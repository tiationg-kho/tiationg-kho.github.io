---
title: Stream
date: 2024-06-13
tags: [Java]
author: "Tiationg Kho"
weight: 17
---

## Stream

- An abstraction that allows you to process sequences of elements in a functional style
- Stream Operations
    - Intermediate Operations
        - eg. `filter`
    - Terminal Operations
        - eg. `toList`

```java
public class Main {
    public static void main(String[] args) {
        List<String> myList = Arrays.asList("apple", "banana", "cherry");
        List<String> filteredList = myList.stream().filter(e -> e.startsWith("b")).toList();
        System.out.println(filteredList); // [banana]
    }
}
```