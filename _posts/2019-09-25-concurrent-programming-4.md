---
title: Concurrent Programming Course note 
categories: Concurrent-programming
tags: 
    - concurrent
    - course note
---

## Moniter
signal contidtion --> waiting  moniter --> signaling


### producer and consumer


```java

moniter PC {
    Object buffer;

    void produce(Object o){
        if(buffer != null){ // while
            empty.wait();
        }
        buffer = o;
        full.signal();
    }

    Object consume() {
        if(buffer == null) // while
            full.wait();
        Object temp = buffer;
        empty.signal();
        return temp;
    }
}

```

```java
// Assuption: E < S < W (Signal and urgent wait)
moniter Semaphore {
    int permit;

    void accquire() {
        if(permit == 0){
            permitsAvailable.wait();
        } else {
            permint--;
        }
    }

    void release(){
        if(!permitAvaible.isempty()){
            permitsAvailable.signal();
        } else{
            permit++;
        }
    }
}
```