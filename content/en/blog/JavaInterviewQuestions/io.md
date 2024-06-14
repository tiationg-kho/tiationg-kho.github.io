---
title: I/O
date: 2024-06-13
tags: [Java]
author: "Tiationg Kho"
weight: 20
---

## I/O

- Java I/O is built around the concept of streams, which are sequences of data
- Type
    - Byte Streams
        - `InputStream` and its subclasses
        - `OutputStream` and its subclasses
    - Character Streams
        - `Reader` and its subclasses
        - `Writer` and its subclasses
- **Buffered streams** are more efficient as they reduce the number of I/O operations by using a buffer (eg. `BufferedReader`, `BufferedWriter`)
- **Serialization** is the process of converting objects to byte streams and vice versa, allowing it to be saved to a file or transferred over a network (eg. `ObjectInputStream`, `ObjectOutputStream`)
- **Java NIO**
    - **Buffers** are containers for data that you want to read or write (eg. `ByteBuffer`)
    - **Channels** are used for data transfer between byte buffers and I/O entities (eg. `FileChannel`, `ServerSocketChannel`, `DatagramChannel`)
    - **Selectors** allow a single thread to monitor multiple channels for events (eg. `Selector`)