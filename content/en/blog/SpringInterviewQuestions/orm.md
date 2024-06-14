---
title: Object-Relational Mapping (ORM)
date: 2024-06-13
tags: [Spring]
author: "Tiationg Kho"
weight: 14
---

## Object-Relational Mapping (ORM)

- **ORM** provides the foundational concept for mapping objects to relational databases
- **Java Persistence API (JPA)** standardizes ORM in Java, defining a set of rules and interfaces
- **Hibernate** implements JPA, offering the actual tools and functionalities for ORM
- **Spring Data JPA** builds on JPA and Hibernate, making it easier to implement data access layers with minimal configuration and code
    - `@Entity` on POJO
        
        ```java
        @Data
        @NoArgsConstructor
        @Entity
        @Table(name = "authors")
        public class Author {
        
            @Id
            @GeneratedValue(strategy = GenerationType.IDENTITY)
            private Long id;
        
            @Column(nullable = false)
            private String name;
        
            @OneToMany(mappedBy = "author", cascade = CascadeType.ALL, orphanRemoval = true)
            @JsonManagedReference
            private List<Book> books;
        }
        
        @Data
        @NoArgsConstructor
        @Entity
        @Table(name = "books")
        public class Book {
        
            @Id
            @GeneratedValue(strategy = GenerationType.IDENTITY)
            private Long id;
        
            @Column(nullable = false)
            private String title;
        
            @ManyToOne
            @JoinColumn(name = "author_id", nullable = false)
            @JsonBackReference
            private Author author;
        }
        ```
        
    - **`@Repository`**
        - With Spring Data JPA, marks a interface as a data access layer component
        
        ```java
        @Repository
        public interface AuthorRepository extends JpaRepository<Author, Long> {
        }
        ```
        
    - CRUD
        - eg. `findAll()`, `findById(id)`, `save(author)`, `deleteById(id)`
    - `@Query` on method can run native SQL query in Spring Data JPA