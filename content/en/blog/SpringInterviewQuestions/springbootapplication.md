---
title: "@SpringBootApplication"
date: 2024-06-13
tags: [Spring]
author: "Tiationg Kho"
weight: 7
---

## @SpringBootApplication

- `@SpringBootApplication` on main class as an entry point

```java
@SpringBootApplication
public class SpringLearningApplication {

    public static void main(String[] args) {
        SpringApplication.run(SpringLearningApplication.class, args);
    }
}

@RestController
class MyController {

    @GetMapping("/")
    public String hello(){
        return "hello";
    }
}
```