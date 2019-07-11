---
layout: post
title: Container comparison - c++ & java
author: Haolin Yang
categories: note langage-compare
---

## Container comparison

C++ version is c++11. Java version is java se8.

|  C++  | JAVA  | Description |
| :---: | :---: | :---        |
| array |  [ ]  | 固定大小的数组 |
| vector| ArrayList | 可变长度的数组 |
|       | Vector | 可变长度的数组，支持同步操作，效率比ArrayList略差 |
| list  | LinkedList | 双链表，便于增删 |
| forward_list |     | 单链表，c++没有给他提供size()的方法 |
| deque | ArrayDeque | 双向队列 |
| stack | Stack | 栈，先进后出 |
| queue | Queue | 队，先进先出 |
| priority_queue | PriorityQueue | 支持优先级的队列 |
| set | TreeSet | 集合，数据有序，。。。。|
| unordered_set | HashSet | 集合，数据无序，。。。。|
| map | TreeMap | key-value映射，key有序，+++|
| unordered_map | HashMap | map, 无序，+++ |
| multiset |    | 集合，允许重复元素 |
| multimap |    | map，允许重复的key |
| unordered_multiset | | 无序允许重复元素集合 |
| unordered_multimap | | 无序允许重复key的map |
|   | LinkedHashSet | 按照插入顺序，支持hash查找 |
|   | LinkedHashMap | 按照插入顺序，支持hash查找 |
|   | HashTable | 类似HashMap |
| bitset | BitSet | 位操作 |