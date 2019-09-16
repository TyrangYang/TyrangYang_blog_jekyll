---
layout: post
author: Haolin Yang
title: Concurrent Programming Course note 
categories: Concurrent-programming
tags: 
    - concurrent
    - course note
---

## Semaphore

Initialize how many permissions you will use.

*acquire()* will add one permission.

*release()* will remove one permission.

Permission must ≥ 0. 

### Semaphore solution for the MEP

1. #criticalSection + permissions = 1
2. #criticalSection = #acquires − #releases

Mutual exclusion: #criticalSection ≤ 1 since #permission ≥ 0.
Absence of deadlock: It never happens that #permission = 0 and #criticalSection = 0

### Java

```java
public class Turnstile extends Thread { 
    static volatile int counter = 0; // keyword is recommended for variables that are shared
    static Semaphore mutex = new Semaphore (1); 
    public void run() {
        for(int i = 0; i < 50; i++){ 
            mutex.acquire();
            counter ++;
            mutex.release();
            System.out.println(id+"- In comes: "+i );
        } 
    }

    public static void main(String args[]) { 
        try{
            Thread m1 = new Turnstile (1); m1.start();
            Thread m2 = new Turnstile (2); m2.start();
        } catch(Exception e){} 
    }
}
```

#### Strong semaphor

Possibility of starvation is caused by the fact that blocked processes are placed in a **set** of processes. But this can be remedied by changing the set to be a queue.

```java
Semaphore(int permits , boolean fair)
```

When fairness is set to true, the semaphore gives permits to access mutual resources in the order the threads have asked for it (FIFO).

## Dining Philosophers

```java
semaphore[] forks = [1,1,1,1,1]; // N = 5;
semaphore chairs = new semaphore(4); // N-1 
// if all get the left fork, it is deadlock. Therefore, At least one can get both forks when only four sit in table

thread Philosopher(i) {
    left = i;
    right = (i+1) % 5
    while(ture){
        chairs.acquire();
        fork(left).acquire();
        fork(right).acquire();

        //eat
        fork(left).release();
        fork(right).release();

        chairs.release();
        //think
    }
}
```

## Producer & Consumer

``` java

Object[] buffer = new Object[N]; //size N
Semaphore prem_to_produce = new Semaphore(N);
Semaphore prem_to_consume = new Semaphore(0); // 0 means you want produce first.
Semaphore mutexP = new Semaphore(1); 
Semaphore mutexC = new Semaphore(1); 
thread Producer: {
    while(true){
        prem_to_produce.acquire();
        mutexP.acquire(); // critcal section. Protect mutiple producers will affect front.
        buffer[front] = produce();
        front = (front + 1) % N;
        prem_to_consume.release();       
        mutexP.release(); 
    }
}

thread Consumer: {
    while(true) {
        prem_to_produce.acquire();
        mutexC.acquire(); // Portect rear from mutiple consumers.
        consume(buffer[rear]);
        rear = (rear + 1) % N;
        prem_to_consume.release();
        mutexC.release();
    }
}

```

## Reader & Writer
Mutiple reader could read.
No reader can read when writer writing

``` java
Semaphore resource = new Semaphore(1);
Semaphore mutexR = new Semaphore(1);
int readers = 0;
thread Writer: {
    while(true){
        resource.acquire();
        // write
        resource.release();
    }
}

thread Reader: {
    while(true){

        mutexR.acquire();
        reader++;
        if(readers == 1)
            resource.acquire();
        mutexR.release();
        // read
        mutexR.acquire();
        reader--;
        if(readers == 0)
            resource.release();
        mutexR.release();
    }
}
```