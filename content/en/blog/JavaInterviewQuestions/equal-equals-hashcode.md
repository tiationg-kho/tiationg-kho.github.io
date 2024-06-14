---
title: == vs equals vs hashCode
date: 2024-06-13
tags: [Java]
author: "Tiationg Kho"
weight: 14
---

## == vs equals vs hashCode

|               | ==                                                     | equals                                                                                  | hashCode                                                                                       |
| ------------- | ------------------------------------------------------ | --------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| Definition    | Compares references for objects, values for primitives | Compares the contents of two objects                                                    | Returns a hash code value for the object                                                       |
| Good Practice |                                                        | Always override equals() when a class's identity is not solely based on memory location | When overriding equals(), you must also override hashCode() to maintain the hash code contract |