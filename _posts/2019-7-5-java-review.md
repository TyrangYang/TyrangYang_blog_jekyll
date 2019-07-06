---
layout: post
title: Review java - OO
author: Haolin Yang
categories: note
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

## Instance veriable & Local veriable

**Instance veriable** is declared inside a class but not inside a method.

**Local veriable** is declared within a method.

## Getter & Setter

If a instance veriable is private, constructor should use the setter of that veriable.

Wrong code
```java
public class Flower {
    private String color;
    private int height;

    public Flower(){
    }

    public Flower(String c, int h){
        this.color = c;
        this.height = h;
    }

    public void setColor(String c){
        this.color = c;
    }

    public String getColor(){
        return this.color;
    }

    public void setHeight(int h){
        if(h < 0 || h > 10){
            System.out.println("ERROR");
        }
        else{
            this.height = h;
        }
    }

    public int getColor(){
        return this.color;
    }
}
```

Test code:
```java
public class FlowerTest(){
    public static void main(String[] args) {
        Flower f1 = new Flower();
        f1.setColor = "red";
        f1.setHeight = 11; // wrong
        f1.setHeight = 10; // OK

        Flower f2 = new Flower("red",11) // Should print error. BUT it pass.
    }
}
```

Change constructor into:
```java
...
    public Flower(String c, int h){
        this.setColor(c);
        this.setHeight(h);
    }
...
```