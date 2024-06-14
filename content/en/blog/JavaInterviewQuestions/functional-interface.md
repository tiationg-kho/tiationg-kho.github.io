---
title: Functional Interface
date: 2024-06-13
tags: [Java]
author: "Tiationg Kho"
weight: 18
---

## Functional Interface

- An interface that contains exactly one abstract method
- `@FunctionalInterface`
    - Used to mark an interface as a functional interface
- Usage with Lambda Expressions
    - Lambda expressions provide a simple way to implement functional interface
    - Lambda expression syntax
        - `(parameters) -> { body }`
    
    ```java
    public class Main {
        public static void main(String[] args) {
            CheckEven func = (n) -> (n % 2) == 0;
            System.out.println(func.execute(2)); // true
        }
    }
    
    @FunctionalInterface
    interface CheckEven {
        boolean execute(int number);
    }
    ```
    
- Common Function Interface
    - `Predicate<T>`
        - Represents a function that takes one argument and returns a boolean
        
        ```java
        Predicate<Integer> func = (n) -> (n % 2) == 0;
        System.out.println(func.test(10)); // true
        ```
        
    - `Function<T, R>`
        - Represents a function that takes one argument and produces a result
        
        ```java
        Function<String, Integer> func = (s) -> s.length();
        System.out.println(func.apply("Hello")); // 5
        ```
        
    - `BiFunction<T, U, R>`
        - Represents a function that takes two arguments and produces a result
    - `Consumer<T>`
        - Represents a function that takes one argument and returns no result
        
        ```java
        Consumer<String> func = (s) -> System.out.println(s);
        func.accept("Hello"); // Hello
        ```
        
    - `Supplier<T>`
        - Represents a function that takes no argument and returns a result
        
        ```java
        Supplier<String> func = () -> "Hello";
        System.out.println(func.get()); // Hello
        ```