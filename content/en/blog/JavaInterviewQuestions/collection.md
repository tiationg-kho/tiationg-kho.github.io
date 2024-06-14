---
title: Collection
date: 2024-06-13
tags: [Java]
author: "Tiationg Kho"
weight: 12
---

## Collection

- A collection in Java is a framework that provides an architecture to store and manipulate a group of objects

| Collection            | Ordering         | Duplicates            | Null Values             | Key Characteristics                                        |
| --------------------- | ---------------- | --------------------- | ----------------------- | ---------------------------------------------------------- |
| ArrayList             | Ordered (index)  | Yes                   | Yes                     | Resizable array and good for random access and iterating   |
| LinkedList (as queue) | FIFO             | Yes                   | Yes                     | Doubly-linked list                                         |
| ArrayDeque (as queue) | FIFO             | Yes                   | No                      | Resizable array                                            |
| ArrayDeque (as stack) | LIFO             | Yes                   | No                      | Resizable array                                            |
| PriorityQueue         | Natural ordering | Yes                   | No                      | Elements are ordered by default comparator or provided one |
| TreeSet               | Sorted           | No                    | No                      | Elements are sorted and unique                             |
| HashSet               | Unordered        | No                    | Yes                     | Hashtable based                                            |
| LinkedHashSet         | Insertion order  | No                    | Yes                     | Hashtable and linked list based                            |
| TreeMap               | Sorted           | Keys: No, Values: Yes | Keys: No, Values: Yes   | Red-Black tree                                             |
| Hashtable             | Unordered        | Keys: No, Values: Yes | Keys: No, Values: No    | Legacy                                                     |
| HashMap               | Unordered        | Keys: No, Values: Yes | Keys: Once, Values: Yes | Hashtable based (array plus linked list or red-black tree) |
| LinkedHashMap         | Insertion order  | Keys: No, Values: Yes | Keys: Once, Values: Yes | Hashtable and linked list based                            |