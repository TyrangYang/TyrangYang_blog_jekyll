---
layout: post
title: Iterator in c++
author: Haolin Yang
categories: STL-study-note
tags:
    - c++
    - STL
---

## Iterator设计思维

STL中containor和algorithm是相对独立的，本身设计也是泛型化的。Iterator就是用来将这两者联系在一起的。

