---
title: Request Mapping
date: 2024-06-13
tags: [Spring]
author: "Tiationg Kho"
weight: 12
---

## Request Mapping

- `@GetMapping`
    
    ```java
    @GetMapping("/users")
    public ResponseEntity<List<User>> getUsers() {
        List<User> users = // Fetch users
        return ResponseEntity.ok(users);
    }
    ```
    
- `@PostMapping`
    
    ```java
    @PostMapping("/users")
    public ResponseEntity<User> createUser(@RequestBody User user) {
        User createdUser = // Create user
        return ResponseEntity.status(HttpStatus.CREATED).body(createdUser);
    }
    ```
    
- `@PutMapping`
    
    ```java
    @PutMapping("/users/{id}")
    public ResponseEntity<User> updateUser(@PathVariable("id") Long id, @RequestBody User user) {
        User updatedUser = // Update user
        return ResponseEntity.ok(updatedUser);
    }
    ```
    
- `@DeleteMapping`
    
    ```java
    @DeleteMapping("/users/{id}")
    public ResponseEntity<Void> deleteUser(@PathVariable("id") Long id) {
        // Delete user
        return ResponseEntity.noContent().build();
    }
    ```