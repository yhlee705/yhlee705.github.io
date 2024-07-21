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

<br>

## <b>**kwargs</b>

* Unlimited Positional Arguments라고 함
* Dictionary를 반환함

```python
class Car1:
    def __init__(self, **kw):
        self.make = kw['make']
        self.model = kw['model']
```

```python
my_car1_1 = Car1(make = 'nissan', model = 'GT')
print(my_car1_1.model)
```

    GT


```python
my_car1_2 = Car1(make = 'nissan')
print(my_car1_2.model)
```

    Error 발생

<br>


* <code>kwarg.get()</code>를 사용하면 파라미터 설정하지 않는 경우 None을 반환함

```python
class Car2:
    def __init__(self, **kw):
        self.make = kw.get('make')
        self.model = kw.get('model')

my_car2 = Car2(make = 'nissan')
print(my_car2.model)
```

    None
