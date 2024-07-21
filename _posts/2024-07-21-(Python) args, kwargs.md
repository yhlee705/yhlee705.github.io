---
categories: 
 - Python
layout: single
title: "(Python) *args, **kwargs"
---

## <b>*args</b>

* Unlimited Positional Arguments라고 함
* 여러개의 인수를 받을 수 있음, Tuple을 반환함

```python
def add(*args):
    sum = 0
    for i in args:
        sum += i
    return sum

print (add(1, 2, 3, 4, 5))
```

15


## <b>**kwargs</b>

* Unlimited Positional Arguments라고 함
* Dictionary를 반환함
