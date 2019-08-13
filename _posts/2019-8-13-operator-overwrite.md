---
layout: post
author: Haolin Yang
title: Operator overwrite in c++
categories: STL-study-note
tags: 
    - c++
    - operator
---

## Example

```cpp
#include <iostream>
using namespace std;

class INT
{
private:
    int m_i;
public:
    INT(int i):m_i(i){};

    int& operator*() const{
        return (int&)this->m_i;
    }
    // int a() const {}; This means a() connot change any member in class.

    INT& operator++(){ //pretfix. ++test;
        this->m_i += 1;
        return *this;
    }
    // Why prefix is not const. Because it always return original class and actually it support ++++test.

    const INT operator++(int){ //postfix. test++;
        INT temp = *this;
        // ++(*this);
        this->m_i += 1;
        return temp;
    }
    // Postfix must be const. Because it return a temperory varible and it not support test++++.
    // You can try int i = 1; i++++;
    // This is invaild.
    
    friend ostream& operator<<(ostream& s, const INT& i){
        s << '[' << i.m_i << ']';
        return s;
    }
    
};

int main(int argc, char const *argv[])
{
    INT test(1);
    cout << ++test << endl;
    cout << test++ << endl;
    cout << test << endl;
    cout << *test << endl;
    return 0;
}
```