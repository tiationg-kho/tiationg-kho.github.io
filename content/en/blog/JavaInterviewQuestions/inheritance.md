---
title: Inheritance
date: 2024-06-13
tags: [Java]
author: "Tiationg Kho"
weight: 6
---

## Inheritance

- Reusing code across classes (creating PARENT-CHILD relationship)
- `extends`
    - Used in class declarations to create a subclass that inherits fields and methods from a superclass
- `@Override`
    - Subclasses can override methods of the superclass to provide specific implementations
- `super()`
    - Calling the superclass constructor in subclass constructor
- `super`
    - Refer to parent class object in subclass

```java
public class Main {
    public static void main(String[] args) {
        Dog myDog = new Dog();
        /*
        Animal is created.
        Dog is created.
         */
        myDog.eat();
        /*
        This animal eats food.
        The dog eats dog food.
         */
        myDog.bark();
        /*
        The dog barks.
         */
        myDog.move();
        /*
        This animal is moving.
         */
    }
}

class Animal {
    public Animal() {
        System.out.println("Animal is created.");
    }

    public void eat() {
        System.out.println("This animal eats food.");
    }

    public void move() {
        System.out.println("This animal is moving.");
    }
}

class Dog extends Animal {
    public Dog() {
        super();
        System.out.println("Dog is created.");
    }

    @Override
    public void eat() {
        super.eat();
        System.out.println("The dog eats dog food.");
    }

    public void bark() {
        System.out.println("The dog barks.");
    }
}
```