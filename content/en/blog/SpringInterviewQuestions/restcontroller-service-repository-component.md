---
title: "@RestController, @Service, @Repository, @Component"
date: 2024-06-13
tags: [Spring]
author: "Tiationg Kho"
weight: 11
---

## @RestController, @Service, @Repository, @Component

- **Presentation Layer**
    - **`@RestController`**
        - Marks a class as a Spring MVC controller
- **Service Layer**
    - **`@Service`**
        - Marks a class as a service layer component for defining business logic
- **Persistence Layer**
    - **`@Repository`**
        - With Spring Data JPA, marks a interface as a data access layer component
        
        ```java
        @Repository
        public interface AuthorRepository extends JpaRepository<Author, Long> {
        }
        ```
        
- **Generic Component**
    - **`@Component`**
        - Marks a class as a generic Spring-managed component with no specific layer role