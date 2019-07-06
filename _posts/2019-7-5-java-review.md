---
layout: post
title: Review java - OO
author: Haolin Yang
catagories: note
---

## Class & Object

A **class** only exists at *compile time*; 

An **object** only exists at *runtime*.

## Data Encapsulation

Data Encapsulation/information hiding: where the internal state and operation are hidden from others.

The more information Class A knows about Class B, the greater the possibility that changing Class A will adversely affect Class B. In an ideal world, making internal changes to Class A should have no, or very little, effect on other classes.

_**Access control** allows for encapsulation_

## Access modifiers

| Qualifier | class | package | subclass | outside the package |
| :---:     | :---: | :---:   | :---:    | :---:               |
| public    |&radic;| &radic; | &radic;  | &radic; |
| protected |&radic;| &radic; | &radic;  | X |
| default   |&radic;| &radic; | X        | X |
| private   |&radic;| X       | X        | X |
