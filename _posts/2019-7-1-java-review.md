---
layout: post
title: Review java - Variable
author: Haolin Yang
catagories: note
---

## Basic types

| Type | Type name |
| :--: | :---:     |
| Integers | bytes, short, int, long|
| Real number | float, double |
| Boolean value | boolean |
| Characters | char |

Every type have a default value:

| Type | Representation | Initial value | Storage | Max. value |
| :-:  | :---:          | :---:         | :---:   | :---:      |
| byte | singed integer | 0             | 8 bits  | 127        | 
| short| singed integer | 0             | 16 bits | 32767      |
| int  | singed integer | 0             | 32 bits | 2147483647 |
| long | singed integer | 0             | 64 bits | over 10^18 |
| float| floating point | 0.0           | 32 bits | over 10^38 | 
| double| floating point | 0.0          | 64 bits | over 10^308|
| boolean| true or false | false        | 1 bit   |            | 
| char | UNICODE (not ASCII)| u0000     | 16 bits | uFFFF      | 

## Difference bewteen i++ and ++i
```java
b = 1;
a = b++; // a = 1; b = 2
```
```java
b = 1;
a = ++b; // a = 2; b = 2
```
```java
int a = 1;
int res = a++ + a;
// res = 3 ; a = 2.
```
```java
int a = 1;
int res = a + a++;
// res = 2; a = 2.
```
```java
int a = 1;
int res = ++a + a;
// res = 4; a = 2.
```
```java
int a = 1;
int res = a + ++a;
// res = 3; a = 2.
```

## For loop
for(**int** i=0; i < n ; i++)



