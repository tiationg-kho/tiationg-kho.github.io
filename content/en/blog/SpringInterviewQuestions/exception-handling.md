---
title: Exception Handling
date: 2024-06-13
tags: [Spring]
author: "Tiationg Kho"
weight: 18
---

## Exception Handling

- `@ControllerAdvice`
    - Used on a class to make it a global exception handler
    - `@ExceptionHandler`
        - Used on methods within a `@ControllerAdvice` class to define the HTTP response for specific exceptions
    
    ```java
    @ControllerAdvice
    public class GlobalExceptionHandler {
    
        @ExceptionHandler(Exception.class)
        public ResponseEntity<Map<String, String>> handleGenericExceptions(Exception ex) {
            Map<String, String> response = new HashMap<>();
            response.put("message", ex.getMessage());
            return ResponseEntity.status(HttpStatus.INTERNAL_SERVER_ERROR).body(response);
        }
    }
    ```