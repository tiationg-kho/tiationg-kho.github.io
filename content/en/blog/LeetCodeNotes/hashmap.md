---
title: Hashmap
date: 2024-06-13
tags: [LeetCode, Hashmap]
author: "Tiationg Kho"
weight: 3
---
>Starred by 25+ users, GitHub Repo: <a href="https://github.com/tiationg-kho/leetcode-pattern-500" target="_blank">LeetCode Pattern 500</a> offers:
>- 500 solutions for LeetCode problems in Python and Java
>- 17 notes on essential concepts related to data structures and algorithms
>- 130 patterns for solving LeetCode problems

# hashmap

## intro

- Complexity
    - search/add/delete in `O(1)`
- Implementation
    - Array (we can think as lots of buckets)
        1. using a hash function to count key
        2. put that key’s value in that index
- Hash Collision Issue (when hash function told us to put in same idx)
    - Solution
        - Separate Chaining
            - use linked list to store key-value pairs at that index
        - Open Addressing
            - find the next unused space adding
        - 2-choice hashing
            - use two hash functions
            - still one hash table
            - will decrease the number of hash collisions
            - is useful for Rabin Karp (string pattern searching)
- Concept
    - can reflect some map relation
    - store key-value pairs
    - key must be hashable
    - if the number of keys is limited, can use array to simulate hashmap
    - if we want to push and pop at same time, make sure to push first then pop, to avoid the issue when the push element is equal to the pop element

## pattern

**separate chaining**

- init array as buckets
- use hash function to calc the idx
- use linked list to store key-value pairs at that index
- time complexity for search/add/delete is `O(n/k)`, k is the number of buckets, n/k is the length of linked list in bucket

**store val**

- the store val can be
    - num
    - idx
    - list or set
        - store key is every element met the condition/pattern of key
        - store value is a list or a set of elements

**store sth’s freq**

- the store key can be
  - num
  - char
  - word
  - point
  - freq (we can even store freq’s freq)
  - some pattern (use tuple as key)

**snapshot of hashmap**

- we can store these snapshots in a list or dict

**build bijection mapping relation**

- can solve isomorphic problems

**store valid val’s freq for finding pairs**

- count res, and then update freq