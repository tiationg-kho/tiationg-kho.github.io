---
title: String
date: 2024-06-13
tags: [LeetCode, String]
author: "Tiationg Kho"
weight: 6
---
>Starred by 25+ users, GitHub Repo: <a href="https://github.com/tiationg-kho/leetcode-pattern-500" target="_blank">LeetCode Pattern 500</a> offers:
>- 500 solutions for LeetCode problems in Python and Java
>- 17 notes on essential concepts related to data structures and algorithms
>- 130 patterns for solving LeetCode problems

# string

## intro

- terms
    - palindrome
        - use two pointers
        - odd length or even length
    - anagram
        - use hashmap
        - need to have same length
    - isomorphic
        - use hashmap
        - build bijection mapping relation 
    - strobogrammatic number
        - a number whose numeral is rotationally symmetric
        - eg. "69", "81018"
    - substring
        - is contiguous like subarray, not like subsequence
    - subsequence
        - can contruct by deleting some chars
    - prefix and suffix
        - prefix is the start of a string
        - suffix is the end of a string
    - lexicographical order
        - eg. ["app", "apple", "application", "ban", "banana"]
    - trie
        - can insert and search in `O(L)` 

## pattern

- **traverse from end**
    - traverse from last idx
    - or reverse whole string first
- **handle value’s bound**
    - be aware of the negative number
        - `-25//10 == -3`
        - `int(-25/10) == -2`
        - `-102 % 10 == 8`
        - `2 == 10 - (-102 % 10)`
- **use chunk**
    - every chunk starts with 4 char/byte string to represent the the length of string in chunk
    - use bit manipulation to turn length (int number) to 4-byte string
- **use rabin karp**
    - find pattern match / substring in string can use Rabin Karp (rolling hash)
        - time `O(n)` or `O(n+m)`
        - space `O(n)`, due to hashset or `O(1)`, due to finding fixed hash val
        - notice: we can use mod to avoid large number calculations
        - should consider the collision problem
            - solution 1: use 2-choice hashing
            - solution 2: when find match, check the substring really match or not. worst time could degenerate to `O(nm)`
        
    ```python
    # notice s length and p length must > 0
    def get_pattern_match_start_idx(s, p):
        base = 27
        hashval_set = set()
        hashval = 0
        for i, c in enumerate(p):
            hashval = hashval * base + ord(c)
        hashval_set.add(hashval)

        hashval = 0
        remove_base = base ** (len(p) - 1)
        for i, c in enumerate(s):
            if i >= len(p):
                hashval -= remove_base * ord(s[i - len(p)])
            hashval = hashval * base + ord(c)
            if i >= len(p) - 1:
                if hashval in hashval_set:
                    return i - (len(p) - 1)
        return - 1

    # notice s length and k must > 0
    def is_length_k_substring_repeat(s, k):
        base = 27
        mod = 10**9 + 7
        hashval_set = set()
        hashval = 0
        remove_base = (base ** (k - 1)) % mod
        for i, c in enumerate(s):
            if i >= k:
                hashval -= (remove_base * ord(s[i - k])) % mod
            hashval = (hashval * base + ord(c)) % mod
            if i >= k - 1:
                if hashval in hashval_set:
                    return True
                hashval_set.add(hashval)
        return False
    ``` 
- **string composition**
    - consider the composition of string
    - consider how to concat the string