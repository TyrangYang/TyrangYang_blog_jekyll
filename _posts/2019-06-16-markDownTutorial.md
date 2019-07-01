---
layout: post
title: Learning MarkDown
date: 2019-06-16
author: Haolin Yang
categories: note
---

This is learning note for MarkDown

# Heading 1
or

Heading 1
===

## Heading 2
or

Heading 2
---

## Intalic and bold
*intalic* or _intalic_
**bold** or __bold__
***intalic and bold*** or ___intalic and bold___

## Unordered list
- line 1
- line 2
- line 3
    + sub 1
    + sub 2

or 

* line 1
* line 2
* line 3
    - sub 1
    - sub 2

## Ordered list
1. line 1
2. line 2
    1. sub 1
    2. sub 2
3. line 3

## Blockqutoes
Use '>' for a qutoes
> This is a qutoe.
> 
> All other syntax can use in quto
> > This is a nested qutoe
> > Use '>>'

## Code block
Just on tab

    <html>
      <head>
      </head>
    </html>

## Code
This is a code part `function foo()`

``Escaping Tick Marks `funtion foo()` ``

```cpp
int add(int a, int b){
    return a+b;
}
```

```javascript
function add(a, b){
    return a+b;
}
```

```python
def add(self, a, b):
    return a+b
```

## Table (For github)
| a     | pdf   | fed   | afd   | 2     |
|------ |-----  |-----  |-----  |---    |
| adfs  | sda   | pdf   | 1     | 3     |
| fads  | pdf   | 1     | 1     | 3     |
| fast  | 1     | 1     | 2     | 3     |

Here is the [markdown table generator](https://www.tablesgenerator.com/markdown_tables)


## Url and Email
<haolinyang95@sina.com>

<https://www.markdownguide.org/basic-syntax/>

## Links
This the official [guide](https://www.markdownguide.org/basic-syntax/ "cool link")

## Horizontal rule
---
***
___

## ==mark==

## Subscript h~2~0

## Superscript 19^th^

## Image
![what is here](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 1")
![anything?][logo]

Write by Haolin Yang

[logo]: https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 2"