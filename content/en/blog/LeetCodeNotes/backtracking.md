---
title: Backtracking
date: 2024-06-13
tags: [LeetCode, Backtracking]
author: "Tiationg Kho"
weight: 10
---
>Starred by 25+ users, GitHub Repo: <a href="https://github.com/tiationg-kho/leetcode-pattern-500" target="_blank">LeetCode Pattern 500</a> offers:
>- 500 solutions for LeetCode problems in Python and Java
>- 17 notes on essential concepts related to data structures and algorithms
>- 130 patterns for solving LeetCode problems

# backtracking

## intro

- backtracking like dfs on a tree
- if a problem need try and error (make decisions) to enum every res, then use backtracking
    - making decisions
        - each round we got multi choices (must pick one)
        - each round we choose sth or not choose
    - notice elements are duplicate or unique
        - if so, we need to take care of pruning
    - notice elements can be chosen repeatedly or not
        - if not, we need to maintain a memo
    - notice that inside backtracking, we can use the boolean value as a return value to indicate whether there is a valid answer or not

```python

def backtrack(res, path, count, visited, index/node):
    if BOUND_REACHED:
        if GOAL_REACHED:
            RECORD_RESULT
        return

    for CHOCIE in CHOICES:
        if CHOICE is VALID:
            MAKE_CHOICE
            backtrack(res, path, count, visited, index/node)
            UNDO_CHOICE
```

## pattern

- subset
    - a subset is composed of none or some or all elements from a set
- permutation
    - a permutation is an ordered selection of a certain number of elements from a set
- combination
    - a combination is an unordered selection of a certain number of elements from a set
- backtracking with constraints
    - make choices and backtrack based on certain constraints or conditions
