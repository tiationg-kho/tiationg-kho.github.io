---
title: Object vs Class
date: 2024-06-13
tags: [Java]
author: "Tiationg Kho"
weight: 3
---

## Object vs Class

|            | Class                          | Object              |
| ---------- | ------------------------------ | ------------------- |
| Definition | Blueprint for creating objects | Instance of a class |

```java
public class Main {
    public static void main(String[] args) {
        Car myCar = new Car("Toyota", 2000);
        myCar.displayInfo(); // Make by Toyota in 2000
    }
}

class Car {
    private String make;
    private int year;

    public Car(String make, int year) {
        this.make = make;
        this.year = year;
    }

    public void displayInfo() {
        System.out.println("Make by " + make + " in " + year);
    }
}
```