---
title: Java集合类源码
date: 2017-05-03 11:00:34
tags: Java
---

## List

### CopyOnWriteArrayList

Java的并发安全的List，基于不可变策略，读不加锁，写加速。因为写入时候需要原来的一份副本。适合读多写少得场景。
