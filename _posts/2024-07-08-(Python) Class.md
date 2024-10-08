---
categories: 
 - Python
layout: single
title: "(Python) Class"
---

## 상속((Inheritance)
```python
class Animal:
    def __init__(self):
        self.num_eyes = 2

    def breathe(self):
        print("Inhale, exhale.")

class Fish(Animal):
    def __init__(self):
        super().__init__()

    def breathe(self):
        super().breathe()
        print("doing this underwater.")

    def swim(self):
        print("moving in water.")

nemo = Fish()
nemo.breathe()
```

결과는 아래와 같다.

```python
Inhale, exhale.
doing this underwater.
```


```python
class Dog:
    def __init__(self):
        self.temperament = "loyal"
 
    def bark(self):
        print("Woof, woof!")
 
class Labrador(Dog):
    def __init__(self):
        super().__init__()
        self.is_a_good_boy = True
 
    def bark(self):
        super().bark()
        print("Greetings, good sir. How do you do?")
```

결과는 아래와 같다.
```
Woof, woof!
Greetings, good sir. How do you do?
```
