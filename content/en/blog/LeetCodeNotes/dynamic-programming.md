---
title: Dynamic Programming
date: 2024-06-13
tags: [LeetCode, DynamicProgramming, Knapsack]
author: "Tiationg Kho"
weight: 13
---
>Starred by 25+ users, GitHub Repo: <a href="https://github.com/tiationg-kho/leetcode-pattern-500" target="_blank">LeetCode Pattern 500</a> offers:
>- 500 solutions for LeetCode problems in Python and Java
>- 17 notes on essential concepts related to data structures and algorithms
>- 130 patterns for solving LeetCode problems

# dynamic programming

## intro

- dp
    - solving bigger problems using smaller problems while saving results to avoid repeated calculations
    - dp problem is about
        - count of ways
        - minimum
        - maximum
    - a problem is a dp problem if it satisfy three conditions
        1. the problem can be divided into subproblems, and its optimal solution can be constructed from optimal solutions of the subproblems (**optimal substructure**)
        2. the subproblems **overlap**
        3. ****no aftereffect****
    - example of problem has optimal substructure but subproblems do not overlap
        - merge sort
            - so we use divide and conquer not dp to solve merge sort
    - dp vs greedy
        -  in dp, we solve overall problem by combining the solutions about subproblems
        -  in greedy, we make a series of localized optimal choices without considering the overall problem
    - two approaches of dp
        - top-down approach (memoization)
            - dfs and cache table
        - bottom-up approach (tabulation)
            - for loop and dp table
    - steps of bottom-up dp
        - define how to divide into smaller subproblems
        - create dp table to store results for these subproblems
        - fill dp table for base cases
        - find out the formula about how to combine subproblems result to larger problem's result
        - start for loop and use formula we just found to fill rest of dp table

## pattern

- 2D
    - use `dp[i][j]`
    - cur states comes from previous states which record in 2D dp table
    - use a 2D array for memo
- knapsack
    - use `dp[i]`
    - dp table's size is the volume of the knapsack, and `dp[i]` is the value of size i knapsack
    - 0-1 knapsack
        - one item can only be selected once
    ```python
    for num in nums:
        for total in range(target, num - 1, - 1):
    ```
    - complete knapsack
        - one item can be selected several times
    ```python
    for num in nums:
        for total in range(1, target + 1):
    ```
    - combination knapsack
        - consider the select ways of item
    ```python
    for num in nums:
        for total in range(1, target + 1):
    ```
    - permutation knapsack
        - consider the select order of item
    ```python
    for total in range(1, target + 1):
        for num in nums:
    ```
- linear sequence
    - use `dp[i]`
    - cur states comes from previous states which record in dp table
    - or use some variable to record previous states to replace using the whole dp table
- LIS 
    - use `dp[i]`
    - LIS (longest increasing subsequence) problem
    - `O(n**2)` approach (linear sequence)
        - `dp[i]` means the length of LIS which ends in `i`
    - `O(nlogn)` approach (patience sort and greedy and binary search)
        - `dp[i]` means the smallest last num when subseq's length is `i+1`
- double sequence
    - use `dp[i][j]`
    - can solve LCS (longest common subsequence) problem
        - eg. `dp[i][j]` means the length of LCS in `s[:i]` and `t[:j]`
- interval (start from one interval)
    - use `dp[i][k]`
- interval (start from short interval)
    - use `dp[i][j]`


