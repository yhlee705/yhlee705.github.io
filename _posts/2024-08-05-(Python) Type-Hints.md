---
categories: 
 - Python
layout: single
title: "(Python) Type Hints"
---

# Type Hints

* 파이썬에서는 데이터형이 유연함(변수 생성 후 나중에 데이터형 변경이 가능함) -> 동적 타이핑
* 코드에서 오류가 덜 발생하게 하기 위해서 데이터형을 지정할 수 있음

아래 예시에서 age는 int 타입이고 police_check 함수는 bool 타입을 반환함을 알 수 있음


```python
def police_check(age: int) -> bool:
    if age > 18:
        can_drive = True
    else:
        can_drive = False
    return can_drive
```
