---
layout: post
title: Review java - Array
author: Haolin Yang
categories: note
---

## Declaring an array

Both are allow

```java
string argc[];
string[] argc;
```

### Int array

```java
int[] nums = new int[7];
nums[0] = 10;
```

```java
Rabbit[] racers = new Rabbit[10];//10 empty rabbit array;
racers[0] = new Rabbit("B","F");
```

## arraycopy()
```java
System.arraycopy(nums, 0, nums, 0, nums.length);

