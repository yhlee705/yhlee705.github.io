---
categories: 
 - Python
layout: single
title: "(Python) *args, **kwargs"
---

## <b>*args</b>

여러개의 인수를 받을 수 있음

기본 양식
```python
def add(*args):
    sum = 0
    for i in args:
        sum += i
    return sum

print (add(1, 2, 3, 4, 5))
```

15


