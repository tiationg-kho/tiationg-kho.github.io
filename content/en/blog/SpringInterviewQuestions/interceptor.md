---
title: Interceptor
date: 2024-06-13
tags: [Spring]
author: "Tiationg Kho"
weight: 19
---

## Interceptor

- Interceptors in Spring allow you to intercept HTTP requests and responses
- Step
    - Create a class which implement the `HandlerInterceptor` interface
        
        ```java
        @Component
        public class MyInterceptor implements HandlerInterceptor {
        
            @Override
            public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception {
                System.out.println("PreHandle method is Calling");
                return true;
            }
        }
        ```
        
    - Register the interceptor with Spring's `InterceptorRegistry`
        
        ```java
        @Configuration
        public class WebConfig implements WebMvcConfigurer {
        
            @Autowired
            private MyInterceptor myInterceptor;
        
            @Override
            public void addInterceptors(InterceptorRegistry registry) {
                registry.addInterceptor(myInterceptor).addPathPatterns("/**");
            }
        }
        ```