---
title: Concurrent Programming Course note 5
categories: Concurrent-programming
tags: 
    - concurrent
    - course note
---

## Message passing

```md
echo() ->
    receive
        {From, Msg} -> From ! {Msg}, echo();
        %^pattern^    %^response^   %^keep loop
        stop -> true
        %^pattern^  ^a return value and stop receiving
    end.
```