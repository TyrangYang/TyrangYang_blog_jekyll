---
title: Concurrent Programming Course note 
categories: Concurrent-programming
tags: 
    - concurrent
    - course note
---

## Moniter
signal contidtion --> waiting  moniter --> signaling


### producer and consumer with a  buffer whose size is one

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


## Semaphore

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

## readers and writers

assume start first and stop

```java

monitor RW {

    int readers=0;
    int writers=0;

    void start_read(){
        if (writer!=0 || !okToWirte.isempty())
            okToRead.wait();
        readers++;
        okToRead.signal(); // coscadp signaling
    }

    void stop_read(){
        readers--;
        if(readers == 0)
            okToWrite.signal();
    }

    void start_write(){
        if(writers!=0 || readers!=0)
            okToWrite.wait();
        writers++;
    }

    void stop_write(){
        writers--;
        if(okToRead.isempty())
            okToWrite.signal();
        else
            okToRead.signal();
    }
}

```

## 3 way sequence (booklet q4)

```java
monitor 3WS{
    int state;
    int fisrt, second, third;
    void first(){
        first++;
        okToSec.
    }

    void second(){

    }

    void third(){

    }
}
```