---
layout: post
author: Haolin Yang
title: Concurrent Programming Course note 
categories: Concurrent-programming
tags: 
    - concurrent
    - course note
---

## Race condition

Multipul thread asccess one same variables of object concurrently and at least one does update.

Bad situation.

## Atomic operation

An operation is atomic if it excute until it completion without interuption

## Critical section

A part of program that accesses shared memory and which we whiich to execute automically.

### mutual exclusion problem (MEP)

1. Mutex: at and point in time, there is at most one thread in the critical section
2. Absence of livelock: If various of threads try to entry the critical section, at lease one of them will succeed.
3. Free from starvation: A thread trying to enter its critical section will eventually be able to do so.


**no shared variables between critical and non critical section nor with the entry/exit protocal.**

critical section must be end

it is meanless that while(true) loop not exsit.

```
while(!flag){
    flag = true;
    // ..... 
    flage = flase;
}

await !flag
```

![transtion system]({{site.baseurl}}{{site.url}}/public/images/2019-09-04-concurrent-programming-2/transition-system.png)

no (p4,q4) which two thread in critical sekction at same time.