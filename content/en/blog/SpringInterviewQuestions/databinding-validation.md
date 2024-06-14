---
title: Data Binding, Validation
date: 2024-06-13
tags: [Spring]
author: "Tiationg Kho"
weight: 13
---

## Data Binding, Validation

- **Data Binding**
    - `@RequestParam`
        
        ```java
        @GetMapping("/search")
        public List<Item> searchItems(
            @RequestParam(name = "query") String query,
            @RequestParam(name = "page", required = false, defaultValue = "0") int page,
            @RequestParam(name = "size", required = false, defaultValue = "10") int size,
            @RequestParam(name = "sort", required = false, defaultValue = "asc") String sort) {
            return itemService.search(query, page, size, sort);
        }
        ```
        
    - `@RequestBody`
        
        ```java
        @PostMapping("/users")
        public ResponseEntity<User> createUser(@RequestBody User user) {
            User createdUser = // Create user
            return ResponseEntity.status(HttpStatus.CREATED).body(createdUser);
        }
        ```
        
    - `@PathVariable`
        
        ```java
        @DeleteMapping("/users/{id}")
        public ResponseEntity<Void> deleteUser(@PathVariable("id") Long id) {
            // Delete user
            return ResponseEntity.noContent().build();
        }
        ```
        
    - `@RequestHeader`
        
        ```java
        @GetMapping("/headerDetails")
        public String headerDetails(@RequestHeader(name = "User-Agent") String userAgent) {
            return "User-Agent: " + userAgent;
        }
        ```
        
- **Validation**
    - **Validating Request Body**
        - `@Valid` with `@RequestBody`, and ****Validation Annotation on fields of POJO
        
        ```java
        class User {
            @NotNull(message = "Name cannot be null")
            private String name;
        }
        
        @PostMapping("/users")
        public ResponseEntity<User> createUser(@Valid @RequestBody User user) {
            User createdUser = // Create user
            return ResponseEntity.status(HttpStatus.CREATED).body(createdUser);
        }
        ```
        
    - **Validating Request Parameters, Path Variables, and Request Headers**
        - `@Validated` with `@RestController`, and Validation Annotation on Request Parameters, Path Variables, or Request Headers
        
        ```java
        @Validated
        @RestController
        public class UserController {
        
            @DeleteMapping("/users/{id}")
            public ResponseEntity<Void> deleteUser(@PathVariable("id") @Min(1) Long id) {
                // Delete user
                return ResponseEntity.noContent().build();
            }
        }
        ```
        
    - **Validation Annotation**
        - `@NotNull`
        - `@NotBlank`
        - `@NotEmpty`
        - `@Min(value)`
        - `@Max(value)`
        - `@Email`
        - `@AssertTrue`
        - `@AssertFalse`
        - `@Null`
        - `@Size(min=val, max=val)`
        - `@Past`
        - `@Future`