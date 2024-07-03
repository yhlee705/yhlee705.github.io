---
categories: Python
layout: single
title: "함수를 다른 함수의 인자로 받기"
---

기존의 함수를 다른 함수에서 인자로 받는 방법

```python
from turtle import Turtle, Screen

tim = Turtle()
screen = Screen()

def move_forwards():
  tim.forward(10)

screen.listen()
screen.onkey(key="space", fun=move_forwards)  # ()를 추가하면 곧바로 실행됨
screen.exitonclick()
```

