---
categories: 
 - Python
layout: single
title: "(Python) 파일 읽기, 쓰기"
---

### 파일 읽기

1. open/close 사용하기 
```python
file = open("my_file.txt")
contents = file.read()
print(contents)
file.close()
```

2. with open 사용하기
```python
with open("my_file.txt") as file:
  contents = file.read()
  print(contents)
```

3. 읽기/쓰기 모드
 - mode 파라미터 : r(읽기), w(쓰기)
```python
with open("my_file.txt", mode = "r") as file:
  contents = file.read()
  print(contents)
```