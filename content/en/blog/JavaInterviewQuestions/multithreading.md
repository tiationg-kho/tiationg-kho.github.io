---
title: Multithreading
date: 2024-06-13
tags: [Java]
author: "Tiationg Kho"
weight: 19
---

## Multithreading

- Multithreading is a Java feature that allows concurrent execution of two or more threads for maximum utilization of the CPU
- **Process vs Thread**
    - A **process** is an executing program. It has its own memory space and resources
    - A **thread** is a single unit of execution within a process. Multiple threads within the same process share the same memory space
- **Main Thread**
    - When a Java application starts, it creates a main thread, which is responsible for executing the `main` method
    - The main thread is the entry point of the program
- **Create a Thread**
    - `extends` the `Thread` Class
    - `implements` the `Runnable` Interface
    - Use an `ExecutorService` for managing thread pool
- **Lifecycle of a Thread**
    - New
        - When a thread is created
        - Use `start()` to become Runnable
    - Runnable
        - When the thread is ready to run but waiting for CPU time
        - Use `run()` to become Running
    - Running
        - When the thread is executing
        - Use `sleep()`, `wait()`, or `join()` to become Blocked
    - Blocked
        - When the thread is waiting for a resource
        - Use `notify()`, or `notifyAll()` to become Runnable
    - Terminated
        - When the thread has finished executing
- `synchronized`
    - Ensures that only one thread can execute a synchronized method or block at a time
- `volatile`
    - Used to indicate that a variable's value may be changed by different threads